# Pipelines, Tasks, and DataPoints — Full Reference

Primitives for building custom Cognee workflows beyond `add → cognify → search`.

## Contents

- [Why custom pipelines](#why-custom-pipelines)
- [Task class](#task-class)
- [run_pipeline](#run_pipeline)
- [run_tasks](#run_tasks)
- [run_tasks_parallel](#run_tasks_parallel)
- [run_custom_pipeline](#run_custom_pipeline)
- [DataPoint and add_data_points](#datapoint-and-add_data_points)
- [LLMGateway for structured extraction](#llmgateway-for-structured-extraction)
- [Pipeline naming rules](#pipeline-naming-rules)

## Why custom pipelines

Use custom tasks and pipelines when you need to:

- Extract structured data from text with a domain-specific schema.
- Combine LLM extraction with programmatic data insertion.
- Chain multiple processing steps with custom logic between them.
- Insert structured DataPoints without the full cognify entity-extraction flow.

`[EXT:https://docs.cognee.ai/guides/custom-tasks-pipelines]`

## Task class

### Signature

```python
class Task:
    executable: Union[
        Callable[..., Any],
        Callable[..., Coroutine[Any, Any, Any]],
        Generator[Any, Any, Any],
        AsyncGenerator[Any, Any],
    ]
    task_config: dict[str, Any] = {"batch_size": 1}
    default_params: dict[str, Any] = {}
    task_type: str = None
    _execute_method: Callable = None
    _next_batch_size: int = 1

    def __init__(self, executable, *args, task_config=None, **kwargs): ...
    def run(self, *args, **kwargs): ...
    async def execute_async_generator(self, args, kwargs): ...
    async def execute_generator(self, args, kwargs): ...
    async def execute_coroutine(self, args, kwargs): ...
    async def execute_function(self, args, kwargs): ...
    async def execute(self, args, kwargs, next_batch_size=None): ...
```

Provenance: `[AST:cognee/modules/pipelines/tasks/task.py:L24]`

### Task type detection

`Task.__init__` inspects the `executable` to set `task_type` and `_execute_method`:

- `inspect.isasyncgenfunction(executable)` → `"Async Generator"` → `execute_async_generator`
- `inspect.isgeneratorfunction(executable)` → `"Generator"` → `execute_generator`
- `inspect.iscoroutinefunction(executable)` → `"Coroutine"` → `execute_coroutine`
- `inspect.isfunction(executable)` → `"Function"` → `execute_function`
- Otherwise raises `ValueError(f"Unsupported task type: {executable}")`

### Task config

```python
Task(my_fn, task_config={"batch_size": 100})
```

- `batch_size` defaults to `1`. When set, the task yields batches of results via the async generator protocol.
- `_next_batch_size` is set by upstream tasks via `execute(args, kwargs, next_batch_size=N)`.

### @task_summary decorator

```python
from cognee.modules.pipelines.tasks.task import task_summary

@task_summary("Classified {n} document(s)")
async def classify_documents(data_documents):
    ...
```

Attaches a human-readable summary template to the task function via the `__task_summary__` attribute. Used for log/telemetry output.

Provenance: `[AST:cognee/modules/pipelines/tasks/task.py:L5]`

## run_pipeline

```python
async def run_pipeline(
    tasks: list[Task],
    data=None,
    datasets: Optional[Union[str, list[str], list[UUID]]] = None,
    user: Optional[User] = None,
    pipeline_name: str = "custom_pipeline",
    use_pipeline_cache: bool = False,
    vector_db_config: Optional[dict] = None,
    graph_db_config: Optional[dict] = None,
    incremental_loading: bool = False,
    context: Optional[Dict] = None,
    data_per_batch: int = 20,
)
```

Top-level async generator. Internally:

1. `validate_pipeline_tasks(tasks)` — sanity checks the task list.
2. `setup_and_check_environment(vector_db_config, graph_db_config)` — initializes dbs and checks embeddings config.
3. `resolve_authorized_user_datasets(datasets, user)` — resolves user + authorized datasets.
4. For each authorized dataset: yields from `run_pipeline_per_dataset` which:
   - Sets database global context variables.
   - Loads existing dataset data if none is passed.
   - Calls `check_pipeline_run_qualification` to honor caching (`use_pipeline_cache`).
   - Delegates to `run_tasks`.

Provenance: `[AST:cognee/modules/pipelines/operations/pipeline.py:L33]`

### Usage pattern

```python
from cognee.modules.pipelines import Task, run_pipeline

tasks = [
    Task(extract_people),
    Task(add_data_points),
]

async for run_info in run_pipeline(tasks=tasks, data=text, datasets=["people_demo"]):
    print(run_info)
```

`async for` iteration is important — `run_pipeline` yields `PipelineRunStarted`, then `PipelineRunCompleted`/`PipelineRunErrored` per dataset.

## run_tasks

```python
async def run_tasks(
    tasks: List[Task],
    dataset_id: UUID,
    data: Optional[List[Any]] = None,
    user: Optional[User] = None,
    pipeline_name: str = "unknown_pipeline",
    context: Optional[Dict] = None,
    incremental_loading: bool = False,
    data_per_batch: int = 20,
)
```

Decorated with `@override_run_tasks(run_tasks_distributed)` — respects `COGNEE_DISTRIBUTED=true` to swap in distributed execution.

### Internal flow

1. Resolve default user if `user is None`.
2. Load the dataset object via SQLAlchemy async session.
3. Generate pipeline id via `generate_pipeline_id(user.id, dataset.id, pipeline_name)`.
4. Log pipeline start and yield `PipelineRunStarted`.
5. Batch data items by `data_per_batch`, create one `run_tasks_data_item` task per item.
6. Gather batches concurrently with `asyncio.gather`.
7. Check for any `PipelineRunErrored` results → raises `PipelineRunFailedError`.
8. Log complete → yield `PipelineRunCompleted`.
9. If the graph engine has `push_to_s3`, push. Same for the relational engine.
10. On any exception: log error, yield `PipelineRunErrored`, and re-raise unless it was already `PipelineRunFailedError`.

Provenance: `[AST:cognee/modules/pipelines/operations/run_tasks.py:L54]`

## run_tasks_parallel

```python
def run_tasks_parallel(tasks: List[Task]) -> Callable[[Any], Generator[Any, Any, Any]]
```

Wraps a list of tasks in a new `Task` that runs all of them concurrently via `asyncio.gather`. Returns the last task's result if multiple tasks are supplied; returns `[]` if only one task.

```python
from cognee.modules.pipelines import Task, run_tasks_parallel

parallel_task = run_tasks_parallel([
    Task(fetch_vendor_a),
    Task(fetch_vendor_b),
    Task(fetch_vendor_c),
])
```

Provenance: `[AST:cognee/modules/pipelines/operations/run_parallel.py:L6]`

## run_custom_pipeline

Convenience wrapper exposed as `cognee.run_custom_pipeline(...)`:

```python
async def run_custom_pipeline(
    tasks: Union[List[Task], List[str]] = None,
    data: Any = None,
    dataset: Union[str, UUID] = "main_dataset",
    user: User = None,
    vector_db_config: Optional[dict] = None,
    graph_db_config: Optional[dict] = None,
    use_pipeline_cache: bool = False,
    incremental_loading: bool = False,
    data_per_batch: int = 20,
    run_in_background: bool = False,
    pipeline_name: str = "custom_pipeline",
)
```

Internally picks the blocking or background executor via `get_pipeline_executor(run_in_background=...)` and delegates to `run_pipeline`. Use this when you want a single async call rather than iterating the `run_pipeline` generator yourself.

Provenance: `[AST:cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L14]`

## DataPoint and add_data_points

### Imports

```python
# Primary path
from cognee.infrastructure.engine import DataPoint
from cognee.infrastructure.engine.models.Edge import Edge
from cognee.tasks.storage import add_data_points

# Shortcut (same DataPoint, via cognee.low_level alias)
from cognee.low_level import DataPoint, setup
```

`cognee.low_level.DataPoint` is an alias for `cognee.infrastructure.engine.ExtendableDataPoint`. `[AST:cognee/low_level.py:L1]`

### DataPoint pattern

```python
class Person(DataPoint):
    name: str
    knows: SkipValidation[Any] = None   # single Person or list[Person]
    metadata: dict = {"index_fields": ["name"]}
```

Key rules:

- Inherit from `DataPoint`.
- Use `SkipValidation[Any]` for fields that hold other DataPoints (avoids forward-reference issues during Pydantic validation).
- Set `metadata = {"index_fields": [...]}` to mark which fields should be embedded in the vector store.
- Assigning another DataPoint instance (or list of DataPoints) to a field creates an edge; the field name becomes the relationship label.

### Edge customization

```python
from cognee.infrastructure.engine.models.Edge import Edge

bob.knows = (Edge(weight=0.9, relationship_type="friend_of"), charlie)
```

Wrap the target in a `(Edge, target)` tuple to attach weight, relationship type, or other edge metadata.

### add_data_points usage

```python
from cognee.tasks.storage import add_data_points

await add_data_points([alice, bob, charlie])
```

Converts DataPoint instances into nodes and edges in the graph, automatically indexing fields listed in `metadata.index_fields` in the vector store. Can be called standalone or as a task inside a pipeline.

`[EXT:https://docs.cognee.ai/guides/custom-data-models]`

## LLMGateway for structured extraction

Custom tasks that extract structured data from text typically use `LLMGateway`:

```python
from cognee.infrastructure.llm.LLMGateway import LLMGateway
from pydantic import BaseModel

class People(BaseModel):
    persons: List[Person]

async def extract_people(text: str) -> List[Person]:
    system_prompt = "Extract people mentioned in the text. Return as persons: Person[]."
    people = await LLMGateway.acreate_structured_output(text, system_prompt, People)
    return people.persons
```

- `acreate_structured_output(text, system_prompt, PydanticModel)` — async method that returns a validated instance of the Pydantic model.
- Backend-agnostic: controlled by `STRUCTURED_OUTPUT_FRAMEWORK` env var (BAML or LiteLLM+Instructor).
- Internal module path: `cognee.infrastructure.llm.LLMGateway` (not re-exported at the top level; import directly).

`[EXT:https://docs.cognee.ai/guides/custom-tasks-pipelines]`

## Pipeline naming rules

- **`cognify_pipeline`** and **`add_pipeline`** are **reserved** — used by `cognify` and `add` internally. Do not reuse these names for custom pipelines.
- **`"custom_pipeline"`** is the safe default for any user-defined pipeline.
- **Give each custom pipeline a distinct name** when running multiple custom pipelines on the same dataset — otherwise their completion states collide.
- Pipeline status is tracked per `(user_id, dataset_id, pipeline_name)` via `generate_pipeline_id`.

`[EXT:https://docs.cognee.ai/guides/custom-tasks-pipelines]` · `[AST:cognee/modules/pipelines/operations/run_tasks.py:L72]`
