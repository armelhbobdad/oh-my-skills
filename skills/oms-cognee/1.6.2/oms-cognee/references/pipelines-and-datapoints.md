# Pipelines, Tasks, and DataPoints — Full Reference

Primitives for building custom Cognee workflows beyond `add → cognify → search`.

## Contents

- [Why custom pipelines](#why-custom-pipelines)
- [Import paths](#import-paths)
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

## Import paths

| Import from | Names | Source |
|---|---|---|
| `cognee` (top level) | `run_custom_pipeline`, `Drop`, `pipelines` | `[SRC:cognee/__init__.py:L44]` · `[SRC:cognee/__init__.py:L67-L68]` |
| `cognee.modules.pipelines` | `Task`, `run_tasks`, `run_tasks_parallel`, `run_pipeline` (the orchestrator) | `[SRC:cognee/modules/pipelines/__init__.py:L75-L78]` |
| `cognee.pipelines` | `Drop` (eager); `Task`, `task`, `run_tasks`, `run_tasks_parallel`, `run_pipeline` (lazy re-exports; this `run_pipeline` is the lightweight runner) | `[SRC:cognee/pipelines/__init__.py:L17-L48]` |
| `cognee.modules.pipelines.tasks.task` | `Task`, `task`, `TaskSpec`, `BoundTask`, `task_summary`, `pipeline_needs_llm` | `[AST:cognee/modules/pipelines/tasks/task.py:L188]` · `[AST:cognee/modules/pipelines/tasks/task.py:L124]` · `[AST:cognee/modules/pipelines/tasks/task.py:L35]` · `[AST:cognee/modules/pipelines/tasks/task.py:L8]` · `[AST:cognee/modules/pipelines/tasks/task.py:L169]` · `[AST:cognee/modules/pipelines/tasks/task.py:L160]` |

- `cognee.modules.pipelines` does not export `task`; import it from `cognee.pipelines` or `cognee.modules.pipelines.tasks.task`. `[SRC:cognee/modules/pipelines/__init__.py:L75-L78]` · `[SRC:cognee/pipelines/__init__.py:L22-L28]`
- The top-level `cognee.pipelines` attribute is bound by `from .modules import pipelines`, while the statement `from cognee.pipelines import …` loads the separate `cognee/pipelines/` package. Import explicitly from the module you mean. `[SRC:cognee/__init__.py:L67]`

## Task class

Import: `from cognee.modules.pipelines import Task`.

### Signature

```python
class Task:
    executable: (
        Callable[..., Any]
        | Callable[..., Coroutine[Any, Any, Any]]
        | Generator[Any, Any, Any]
        | AsyncGenerator[Any, Any]
    )
    task_config: dict[str, Any] = {"batch_size": 1}
    default_params: dict[str, Any] = {}
    task_type: str = None
    enriches: bool = False
    needs_llm: bool = True
    _execute_method: Callable = None

    def __init__(self, executable, *args, task_config=None, batch_size=None,
                 enriches=False, needs_llm=True, **kwargs): ...
    def with_config(self, **overrides) -> "Task": ...
    def run(self, *args, **kwargs): ...
    async def execute_async_generator(self, args, kwargs, batch_size): ...
    async def execute_generator(self, args, kwargs, batch_size): ...
    async def execute_coroutine(self, args, kwargs, batch_size): ...
    async def execute_function(self, args, kwargs, batch_size): ...
    async def execute(self, args, kwargs, next_batch_size=None): ...
```

Provenance: `[AST:cognee/modules/pipelines/tasks/task.py:L188]`

### Task type detection

`Task.__init__` inspects the `executable` to set `task_type` and `_execute_method`:

- `inspect.isasyncgenfunction(executable)` → `"Async Generator"` → `execute_async_generator`
- `inspect.isgeneratorfunction(executable)` → `"Generator"` → `execute_generator`
- `inspect.iscoroutinefunction(executable)` → `"Coroutine"` → `execute_coroutine`
- `inspect.isfunction(executable)` → `"Function"` → `execute_function`
- Otherwise raises `ValueError(f"Unsupported task type: {executable}")`

`[SRC:cognee/modules/pipelines/tasks/task.py:L224-L237]`

### Task config

```python
Task(my_fn, task_config={"batch_size": 100})
Task(my_fn, batch_size=100)          # keyword form; overrides task_config["batch_size"]
Task(build_nodes, needs_llm=False)   # task never calls the LLM
```

- `batch_size` defaults to `1`; the `batch_size=` keyword overrides the value from `task_config`. `[SRC:cognee/modules/pipelines/tasks/task.py:L239-L254]`
- `execute(args, kwargs, next_batch_size=N)` hands N to the `execute_*` method as a local `batch_size` `[SRC:cognee/modules/pipelines/tasks/task.py:L336-L341]`, and the runner passes the *next* task's `task_config["batch_size"]` `[SRC:cognee/modules/pipelines/operations/run_tasks_base.py:L278]` — so a task's `batch_size` batches the PREVIOUS task's output. Generator and async-generator tasks yield lists of that size; coroutine and function tasks yield their single return value regardless. `[SRC:cognee/modules/pipelines/__init__.py:L48-L51]` · `[SRC:cognee/modules/pipelines/tasks/task.py:L283-L334]`
- `enriches=True` marks a task that mutates its input in place: when a coroutine or function task returns `None`, the runner passes the input on unchanged. `[SRC:cognee/modules/pipelines/tasks/task.py:L316-L334]`
- `needs_llm=False` on tasks that never call the LLM lets `run_pipeline` skip the first-run LLM connection probe: the pipeline's need is the union over its tasks (`pipeline_needs_llm`), and embeddings are always probed. The flag is a named `__init__` parameter, so it is not forwarded to the executable. `[AST:cognee/modules/pipelines/tasks/task.py:L160]` · `[SRC:cognee/modules/pipelines/operations/pipeline.py:L74-L86]` · `[SRC:cognee/modules/pipelines/tasks/task.py:L209-L222]`
- A task whose signature has a parameter literally named `ctx` receives the run's `PipelineContext` (`user`, `data_item`, `dataset`, `pipeline_run_id`, `pipeline_name`, `extras`). `[SRC:cognee/modules/pipelines/tasks/task.py:L246-L251]` · `[SRC:cognee/modules/pipelines/operations/run_tasks_base.py:L172-L176]` · `[SRC:cognee/modules/pipelines/models/PipelineContext.py:L23-L28]`
- `with_config(**overrides)` returns a new `Task` with `batch_size`, `enriches`, `needs_llm` or bound kwargs overridden. `[SRC:cognee/modules/pipelines/tasks/task.py:L256-L274]`

### @task_summary decorator

```python
from cognee.modules.pipelines.tasks.task import task_summary

@task_summary("Classified {n} document(s)")
async def classify_documents(data_documents):
    ...
```

Attaches a human-readable summary template to the task function via the `__task_summary__` attribute. Used for log/telemetry output.

Provenance: `[AST:cognee/modules/pipelines/tasks/task.py:L169]`

### task() deferred-call sugar (TaskSpec / BoundTask)

```python
from cognee.pipelines import task

@task(batch_size=20)                       # decorator, with or without arguments
async def extract(chunks, graph_model=None): ...

classify = task(classify_documents)        # functional wrapper for functions you don't own

step = extract(graph_model=KnowledgeGraph) # BoundTask: kwargs captured, nothing runs yet
```

- `task(fn=None, *, batch_size=None, enriches=False, needs_llm=True, **default_params)` returns a `TaskSpec`. `[AST:cognee/modules/pipelines/tasks/task.py:L124]`
- Calling a `TaskSpec` does not execute the function: it returns a `BoundTask` holding the kwargs for later. `batch_size`, `enriches` and `needs_llm` passed at call time override that step's config. `[AST:cognee/modules/pipelines/tasks/task.py:L35]` · `[SRC:cognee/modules/pipelines/tasks/task.py:L82-L104]`
- `spec.direct(*args, **kwargs)` calls the underlying function directly (for tests); `spec.task` returns the pre-built `Task`. `[SRC:cognee/modules/pipelines/tasks/task.py:L106-L117]`
- `BoundTask` steps are run by the lightweight `cognee.pipelines.run_pipeline` (see [run_pipeline](#run_pipeline)), which supplies the pipeline data as the first positional argument. `[AST:cognee/modules/pipelines/tasks/task.py:L8]`

### Drop: filtering items out of the stream

```python
from cognee.pipelines import Drop   # also cognee.Drop

async def filter_short(text: str) -> str:
    if len(text) < 10:
        return Drop  # this item is removed from the pipeline
    return text
```

`Drop` is a falsy singleton sentinel `[SRC:cognee/pipelines/types.py:L8-L32]`. Every `execute_*` method discards a returned or yielded `Drop` instead of passing it downstream. `[SRC:cognee/modules/pipelines/tasks/task.py:L283-L334]`

## run_pipeline

Two functions share this name `[SRC:cognee/modules/pipelines/__init__.py:L23-L37]`:

- `cognee.modules.pipelines.run_pipeline` (`operations/pipeline.py`) — the full orchestrator: resolves the user and authorized datasets, takes the per-dataset lock, records `PipelineRun` rows and yields `PipelineRunInfo` events. `cognify`, `improve` and `run_custom_pipeline` call it.
- `cognee.pipelines.run_pipeline` (`operations/run_pipeline.py`) — the lightweight runner over `BoundTask` steps; returns the final step's results as a list, with no dataset locking and no run records. See the last subsection below.

```python
async def run_pipeline(
    tasks: list[Task] | Callable[[Any], list[Task]] | None = None,
    data=None,
    datasets: str | list[str] | list[UUID] | None = None,
    user: User | None = None,
    pipeline_name: str = "custom_pipeline",
    vector_db_config: dict | None = None,
    graph_db_config: dict | None = None,
    incremental_loading: bool = False,
    data_per_batch: int = 20,
    rollback_handler: Callable[..., Awaitable[None]] | None = None,
    llm_config: LLMConfig | None = None,
    embedding_config: EmbeddingConfig | None = None,
    data_cache: bool = False,
    skip_connection_test: bool = False,
    needs_llm: bool = True,
)
```

`tasks` is either the task list every data item runs, or a callable mapping one item to its task list (a task resolver). For a task list, `needs_llm` is derived from the tasks; the parameter applies only to a resolver. `[SRC:cognee/modules/pipelines/operations/pipeline.py:L70-L79]`

Top-level async generator. Internally:

1. Raises `ValueError` if `tasks` is `None`. For a task list, `validate_pipeline_tasks(tasks)` checks it is a list of `Task` instances (else `WrongTaskTypeError`) and `needs_llm` becomes `pipeline_needs_llm(tasks)`. `[SRC:cognee/modules/pipelines/operations/pipeline.py:L80-L86]` · `[SRC:cognee/modules/pipelines/layers/validate_pipeline_tasks.py:L13-L20]`
2. `setup_and_check_environment(vector_db_config, graph_db_config, skip_connection_test=..., needs_llm=...)` — creates the relational tables (and, for a `pgvector` provider with backend access control off, the `vector` extension), then runs the first-use connection probes (LLM only when needed, embeddings always). `skip_connection_test=True` skips them for this call; `COGNEE_SKIP_CONNECTION_TEST=true` skips them process-wide. `[SRC:cognee/modules/pipelines/operations/pipeline.py:L87-L92]` · `[SRC:cognee/modules/pipelines/layers/setup_and_check_environment.py:L41-L94]` · `[SRC:cognee/infrastructure/databases/vector/pgvector/create_db_and_tables.py:L13-L15]`
3. `resolve_authorized_user_datasets(datasets, user)` — resolves user + authorized datasets. `[SRC:cognee/modules/pipelines/operations/pipeline.py:L94]`
4. For each authorized dataset, in sequence: yields from `run_pipeline_per_dataset` which `[SRC:cognee/modules/pipelines/operations/pipeline.py:L96-L112]`:
   - Loads existing dataset data if none is passed. `[SRC:cognee/modules/pipelines/operations/pipeline.py:L131]`
   - Serializes on the per-dataset lock (`get_dataset_lock`): a run on the same dataset waits for the in-flight one, separate runs on different datasets still proceed in parallel, and a nested run on a dataset its ancestor already holds proceeds without re-locking. `[SRC:cognee/modules/pipelines/operations/pipeline.py:L24-L27]` · `[SRC:cognee/modules/pipelines/operations/pipeline.py:L153-L167]`
   - Always runs: run history does not gate the run; already-processed items are skipped per item by incremental loading (only when `incremental_loading` or `data_cache` is set). `[SRC:cognee/modules/pipelines/operations/pipeline.py:L133-L135]` · `[SRC:cognee/modules/pipelines/operations/run_tasks_data_item.py:L377]`
   - Delegates to `run_tasks`. `[SRC:cognee/modules/pipelines/operations/pipeline.py:L136-L148]`

Provenance: `[AST:cognee/modules/pipelines/operations/pipeline.py:L53]`

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

`async for` iteration is important — `run_pipeline` yields `PipelineRunStarted`, then `PipelineRunCompleted`/`PipelineRunErrored` per dataset (classes in `cognee.modules.pipelines.models.PipelineRunInfo`). `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L80-L85]` · `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L285-L290]` · `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L336-L346]` · `[SRC:cognee/modules/pipelines/models/PipelineRunInfo.py:L26-L50]`

### Lightweight runner: cognee.pipelines.run_pipeline

```python
async def run_pipeline(
    steps: list[BoundTask],
    *,
    data: Any = None,
    user: User | None = None,
    dataset: str | None = None,
    pipeline_name: str = "pipeline",
    context: dict | None = None,
) -> list
```

```python
from cognee.pipelines import task, run_pipeline   # lightweight runner, not the orchestrator

classify = task(classify_documents)
extract = task(extract_graph, batch_size=20)

results = await run_pipeline(
    [classify(), extract(graph_model=KnowledgeGraph)],
    data=raw_input,
)
```

- Each step receives the previous step's output as its first positional argument; the return value is the list of the final step's results. `[SRC:cognee/modules/pipelines/operations/run_pipeline.py:L46-L61]`
- Empty `steps` returns `[data]` (or `[]`); a step that is not a `BoundTask` raises `TypeError` ("Did you forget to call the task?"). `[SRC:cognee/modules/pipelines/operations/run_pipeline.py:L63-L72]`
- `context` becomes `PipelineContext.extras`; the steps run through `run_tasks_base` directly. `[SRC:cognee/modules/pipelines/operations/run_pipeline.py:L86-L100]`

Provenance: `[AST:cognee/modules/pipelines/operations/run_pipeline.py:L37]`

## run_tasks

Import: `from cognee.modules.pipelines import run_tasks`.

```python
async def run_tasks(
    tasks: list[Task] | Callable[[Any], list[Task]],
    dataset_id: UUID,
    data: list[Any] | None = None,
    user: User | None = None,
    pipeline_name: str = "unknown_pipeline",
    incremental_loading: bool = False,
    data_per_batch: int = 20,
    extras: dict | None = None,
    rollback_handler: Callable[..., Awaitable[None]] | None = None,
    llm_config: LLMConfig | None = None,
    embedding_config: EmbeddingConfig | None = None,
    data_cache: bool = False,
)
```

Runs a pipeline over one dataset as one logical run. `tasks` is a task list or a per-item task resolver; items resolved to different lists still share one run record, one database context, one rollback and one terminal status. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L53-L61]` There is no `context` parameter: pass `extras`, which each item receives as a copied `PipelineContext.extras`. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L192-L201]`

### Internal flow

1. Resolve default user if `user is None`. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L62-L64]`
2. Load the dataset object via SQLAlchemy async session. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L66-L69]`
3. Generate pipeline id via `generate_pipeline_id(user.id, dataset.id, pipeline_name)`. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L71]`
4. Log pipeline start and yield `PipelineRunStarted`. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L72-L85]`
5. Set the database global context variables for the dataset (with `llm_config`/`embedding_config`). With `data_cache` or `incremental_loading`, resolve data directories. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L93-L104]`
6. Pair each data item with its task list (each distinct resolver list is validated once), then schedule every item at once with `asyncio.gather`; a semaphore caps concurrency at `data_per_batch`, and each item runs `run_tasks_data_item`. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L106-L121]` · `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L182-L215]`
7. Check for any `PipelineRunErrored` item results → raises `PipelineRunFailedError` carrying the first root error. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L217-L258]` An item that raises never reaches this check: `asyncio.gather` runs without `return_exceptions`, so the error goes straight to step 10. That is the default path: regular mode does not catch task errors, and incremental mode re-raises while `RAISE_INCREMENTAL_LOADING_ERRORS` keeps its default `true`. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L210-L215]` · `[SRC:cognee/modules/pipelines/operations/run_tasks_data_item.py:L257-L282]`
8. If the graph engine has `push_to_s3`, push. Same for the relational engine. This runs BEFORE completion, so a push failure becomes a failed run. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L260-L271]`
9. Log complete → yield `PipelineRunCompleted`. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L273-L290]`
10. On any `Exception` or `asyncio.CancelledError`: call `rollback_handler` if given (its own errors are only logged), log the root error, yield `PipelineRunErrored`, and re-raise unless it was already `PipelineRunFailedError`. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L292-L350]`

Provenance: `[AST:cognee/modules/pipelines/operations/run_tasks.py:L39]`

## run_tasks_parallel

```python
def run_tasks_parallel(tasks: list[Task]) -> Callable[[Any], Generator[Any, Any, Any]]  # actually returns Task(parallel_run)
```

Wraps a list of tasks in a new `Task` that runs all of them concurrently via `asyncio.gather`. Returns the last task's result if multiple tasks are supplied; returns `[]` if only one task. Each task's `run()` result goes to `asyncio.create_task`, so the wrapped executables must be coroutine functions. `[SRC:cognee/modules/pipelines/operations/run_parallel.py:L9-L15]`

```python
from cognee.modules.pipelines import Task, run_tasks_parallel

parallel_task = run_tasks_parallel([
    Task(fetch_vendor_a),
    Task(fetch_vendor_b),
    Task(fetch_vendor_c),
])
```

Provenance: `[AST:cognee/modules/pipelines/operations/run_parallel.py:L8]`

## run_custom_pipeline

Convenience wrapper exposed as `cognee.run_custom_pipeline(...)`:

```python
async def run_custom_pipeline(
    tasks: list[Task] | list[str] | None = None,
    data: Any = None,
    dataset: str | UUID = DEFAULT_DATASET_NAME,  # "main_dataset"
    user: User = None,
    vector_db_config: dict | None = None,
    graph_db_config: dict | None = None,
    incremental_loading: bool = False,
    data_per_batch: int = 20,
    run_in_background: bool = False,
    pipeline_name: str = "custom_pipeline",
    data_cache: bool = False,            # process only new or modified data
    skip_connection_test: bool = False,  # skip the first-run LLM/embedding connection checks
)
```

`[SRC:cognee/modules/data/constants.py:L8]` · `[SRC:cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L48]` · `[SRC:cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L55-L61]`

Internally picks the blocking or background executor via `get_pipeline_executor(run_in_background=...)` and delegates to `run_pipeline`. Use this when you want a single async call rather than iterating the `run_pipeline` generator yourself. `[SRC:cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L75-L92]` Pass `Task` instances: despite the `list[str]` annotation, `run_pipeline` validates the list and rejects non-`Task` items. `[SRC:cognee/modules/pipelines/layers/validate_pipeline_tasks.py:L16-L20]`

Provenance: `[AST:cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L14]`

## DataPoint and add_data_points

### Imports

```python
# Primary path
from cognee.infrastructure.engine import DataPoint, Edge   # or: from cognee.infrastructure.engine.models.Edge import Edge
from cognee.tasks.storage import add_data_points

# Shortcut module (DataPoint here is ExtendableDataPoint)
from cognee.low_level import DataPoint, Edge, setup
```

- `cognee.infrastructure.engine` provides `DataPoint`, `Edge`, `ExtendableDataPoint`, `InternalDataPoint`, `INTERNAL_PROPERTY`, `is_internal_node`, and the field markers `Embeddable`, `Dedup`, `LLMContext` and `FromIdentity`. `[SRC:cognee/infrastructure/engine/__init__.py:L1-L5]`
- `cognee.low_level` provides `DataPoint` (an alias for `cognee.infrastructure.engine.ExtendableDataPoint`, a `DataPoint` subclass that adds nothing), `Edge`, `FromIdentity`, `setup`, `EntitySpec`, `GraphSchemaSpec`, `graph_model_from_spec` and `graph_spec_to_json_schema`, plus the lazily resolved `graph_schema_to_graph_model` and `graph_model_to_graph_schema`. `[SRC:cognee/low_level.py:L1-L21]` · `[SRC:cognee/infrastructure/engine/models/ExtendableDataPoint.py:L4-L7]`

### DataPoint pattern

```python
class Person(DataPoint):
    name: str
    knows: SkipValidation[Any] = None   # single Person or list[Person]
    metadata: dict = {"index_fields": ["name"], "identity_fields": ["name"]}
```

Key rules:

- Inherit from `DataPoint`.
- Use `SkipValidation[Any]` for fields that hold other DataPoints (avoids forward-reference issues during Pydantic validation).
- Set `metadata = {"index_fields": [...]}` to mark which fields should be embedded in the vector store (or mark fields `Annotated[str, Embeddable()]` and leave `metadata` undeclared). `[SRC:cognee/infrastructure/engine/models/DataPoint.py:L38-L40]` · `[SRC:cognee/infrastructure/engine/models/DataPoint.py:L49-L50]`
- Set `metadata["identity_fields"]` (or mark fields `Annotated[str, Dedup()]`) on any model whose nodes should merge: the id is then derived with `uuid5` from the class name and those values, and `Model.id_for(...)` recomputes it. A model without identity fields (and no explicit `id`) gets a random `uuid4` id and never merges across runs. `[SRC:cognee/infrastructure/engine/models/DataPoint.py:L41-L45]` · `[SRC:cognee/infrastructure/engine/models/DataPoint.py:L58-L64]` · `[SRC:cognee/infrastructure/engine/models/DataPoint.py:L176-L193]`
- Assigning another DataPoint instance (or list of DataPoints) to a field creates an edge; the field name becomes the relationship label. `[SRC:cognee/infrastructure/engine/models/DataPoint.py:L32-L34]`

### Edge customization

```python
from cognee.low_level import DataPoint, Edge

class Person(DataPoint):
    name: str
    # Edge owned by the node: same-type endpoints are spelled as strings
    reports_to: list[Edge["Person", "Person"]] = []
    metadata: dict = {"index_fields": ["name"], "identity_fields": ["name"]}

class SocialGraph(DataPoint):
    # Typed edge on a container; the relationship is named after the field
    friends_with: list[Edge[Person, Person]] = []

graph = SocialGraph(friends_with=[Edge(source=bob, target=charlie, weight=0.9)])
```

- Inside a class body, endpoints of the class's own type are spelled as strings (`Edge["Person", "Person"]`) because the class is not bound yet. `[SRC:examples/guides/custom_graph_model.py:L33-L36]`
- `Edge` is `Generic[Source, Target, RelationshipType]` with `source`, `target`, `relationship_type`, `weight`, `weights`, `properties` and `edge_text` fields. `[SRC:cognee/infrastructure/engine/models/Edge.py:L13]` · `[SRC:cognee/infrastructure/engine/models/Edge.py:L49-L56]`
- On a custom graph model, `list[Edge[Source, Target]]` asks the LLM for flat relationship rows that cognee resolves into edges. The third generic sets the name: omitted → the field name; `Literal["a", "b"]` → the LLM picks one; `str` → free-form. `[SRC:cognee/infrastructure/engine/models/Edge.py:L16-L20]` Endpoint models need exactly one identity field. `[SRC:cognee/infrastructure/engine/models/DataPoint.py:L44-L45]`
- A hand-built `Edge` may omit `source`: `fill_endpoints()` fills it from the declaring node and the relationship name from the field. On a parametrized edge the declaring node must match the declared `Source`, so set `source=` explicitly for edges declared on a container. A missing target is an error. `[SRC:cognee/infrastructure/engine/models/Edge.py:L22-L26]` · `[SRC:cognee/infrastructure/engine/models/Edge.py:L66-L109]`
- `to_properties()` returns the storage property bag: every set metadata field, endpoints excluded, with each `weights` entry also copied out as a scalar `weight_<name>` property. `[SRC:cognee/infrastructure/engine/models/Edge.py:L148-L164]`

The `(Edge, target)` tuple is the older form, still supported:

```python
bob.knows = (Edge(weight=0.9, relationship_type="friend_of"), charlie)
```

Wrap the target (or a list of targets) in an `(Edge, target)` tuple to attach weight, relationship type, or other edge metadata. `[SRC:cognee/infrastructure/engine/models/Edge.py:L31-L44]` · `[SRC:cognee/modules/graph/utils/field_edges.py:L70-L81]`

### add_data_points usage

```python
from cognee.tasks.storage import add_data_points

await add_data_points([alice, bob, charlie])
```

```python
async def add_data_points(
    data_points: list[DataPoint],
    custom_edges: list | None = None,
    embed_triplets: bool = False,
    ctx: Optional["PipelineContext"] = None,
    graph_only: bool = False,
) -> list[DataPoint]
```

`[SRC:cognee/tasks/storage/add_data_points.py:L70-L76]`

Converts DataPoint instances into nodes and edges in the graph, automatically indexing fields listed in `metadata.index_fields` in the vector store. Can be called standalone or as a task inside a pipeline.

- `data_points` must be a list of `DataPoint` instances, otherwise `InvalidDataPointsInAddDataPointsError`. `[SRC:cognee/tasks/storage/add_data_points.py:L94-L97]`
- `graph_only=True` writes graph nodes and edges without touching a vector engine, and cannot be combined with `embed_triplets=True`. `[SRC:cognee/tasks/storage/add_data_points.py:L86-L87]` · `[SRC:cognee/tasks/storage/add_data_points.py:L98-L101]`

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

- `acreate_structured_output(text, system_prompt, PydanticModel, **kwargs)` — static method returning a coroutine; await it to get a validated instance of the Pydantic model. `[SRC:cognee/infrastructure/llm/LLMGateway.py:L112-L118]`
- Backend-agnostic: controlled by `STRUCTURED_OUTPUT_FRAMEWORK` env var. Default `litellm_native`: plain litellm with a schema-native `response_format` (or a prompted-JSON fallback) and no instructor; set `instructor` or `baml` to opt back. `[SRC:cognee/infrastructure/llm/config.py:L101-L107]` · `[SRC:cognee/infrastructure/llm/LLMGateway.py:L121-L154]`
- Internal module path: `cognee.infrastructure.llm.LLMGateway` (not re-exported at the top level; import directly).

`[EXT:https://docs.cognee.ai/guides/custom-tasks-pipelines]`

## Pipeline naming rules

- **`cognify_pipeline`** and **`add_pipeline`** are **reserved** — used by `cognify` and `add` internally. Do not reuse these names for custom pipelines. `[EXT:https://docs.cognee.ai/guides/custom-tasks-pipelines]` · `[SRC:cognee/api/v1/cognify/cognify.py:L515]` · `[SRC:cognee/api/v1/add/add.py:L334]`
- **`"custom_pipeline"`** is the safe default for any user-defined pipeline.
- **Graph-writing custom pipelines should keep a name listed in `cognee.modules.improve.graph_changes.WRITE_PIPELINE_NAMES`** (the default `custom_pipeline` is listed): `improve()`'s enrichment gate counts only those names as graph changes, so writes under a bespoke name can be reported as already enriched. Run history does not gate pipeline runs, so distinct names are not needed to keep runs apart. `[SRC:cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L62-L68]` · `[SRC:cognee/modules/improve/graph_changes.py:L39-L50]` · `[SRC:cognee/modules/pipelines/operations/pipeline.py:L133-L135]`
- Pipeline status is tracked per `(user_id, dataset_id, pipeline_name)` via `generate_pipeline_id`.

`[AST:cognee/modules/pipelines/utils/generate_pipeline_id.py:L4]` · `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L71]`
