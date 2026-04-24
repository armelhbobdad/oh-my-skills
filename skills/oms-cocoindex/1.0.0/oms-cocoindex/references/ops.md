# Ops — `cocoindex.ops.*`

v1.0.0 replaces v0.3.37's `cocoindex.functions.*` namespace with `cocoindex.ops.*`. Four sub-modules expose three categories: text processing, embeddings, and entity resolution.

```python
# cocoindex/ops/__init__.py
__all__ = ["litellm", "sentence_transformers", "text"]
```
[AST:python/cocoindex/ops/__init__.py:L1]

(Note: `entity_resolution` is a sub-package, not exported by `ops/__init__.py`. Import it as `from cocoindex.ops.entity_resolution import ...`.)

## Text — `cocoindex.ops.text`

```python
__all__ = ["detect_code_language", "SeparatorSplitter", "CustomLanguageConfig", "RecursiveSplitter"]
```
[AST:python/cocoindex/ops/text.py:L6]

### detect_code_language

```python
def detect_code_language(*, filename: str) -> str | None: ...
```
[AST:python/cocoindex/ops/text.py:L19]

```python
detect_code_language(filename="main.py")    # 'python'
detect_code_language(filename="test.rs")    # 'rust'
detect_code_language(filename="x.xyz")      # None
```

Replaces v0.3.37's `cocoindex.functions.DetectProgrammingLanguage`.

### SeparatorSplitter

Regex-based splitter. Instantiate once, reuse for many texts. [AST:python/cocoindex/ops/text.py:L39]

```python
class SeparatorSplitter:
    def __init__(
        self,
        separators_regex: list[str],
        *,
        keep_separator: Literal["left", "right"] | None = None,
        include_empty: bool = False,
        trim: bool = True,
    ) -> None: ...
    def split(self, text: str) -> list[Chunk]: ...
```

```python
splitter = SeparatorSplitter([r"\n\n+"])
chunks = splitter.split("Para1\n\nPara2\n\nPara3")
```

Replaces v0.3.37's `cocoindex.functions.SplitBySeparators`.

### RecursiveSplitter

Tree-sitter-aware recursive splitter with built-in language support and pluggable custom languages. [AST:python/cocoindex/ops/text.py:L120]

```python
class RecursiveSplitter:
    def __init__(self, *, custom_languages: list[CustomLanguageConfig] | None = None) -> None: ...
    def split(
        self,
        text: str,
        chunk_size: int,
        *,
        min_chunk_size: int | None = None,    # defaults to chunk_size / 2
        chunk_overlap: int | None = None,
        language: str | None = None,          # "python", "rust", ".py", "markdown", etc.
    ) -> list[Chunk]: ...
```

```python
splitter = RecursiveSplitter()
chunks = splitter.split(text, chunk_size=2000, chunk_overlap=500, language="markdown")
# chunks: list[cocoindex.resources.chunk.Chunk] — see resources.md
```

Replaces v0.3.37's `cocoindex.functions.SplitRecursively`. The chunk type changed: v1.0.0 returns `cocoindex.resources.chunk.Chunk` (`text`, `start: TextPosition`, `end: TextPosition`) instead of v0.3.37's flatter shape.

### CustomLanguageConfig

Pluggable language for the recursive splitter. [AST:python/cocoindex/ops/text.py:L87]

```python
class CustomLanguageConfig:
    def __init__(
        self,
        language_name: str,
        separators_regex: list[str],
        aliases: list[str] | None = None,
    ) -> None: ...
```

```python
config = CustomLanguageConfig(language_name="myformat", separators_regex=[r"---", r"\n\n+"], aliases=["mf", ".mf"])
splitter = RecursiveSplitter(custom_languages=[config])
chunks = splitter.split("A---B---C", chunk_size=10, language="myformat")
```

## Sentence Transformers — `cocoindex.ops.sentence_transformers`

```python
__all__ = ["SentenceTransformerEmbedder"]
```
[AST:python/cocoindex/ops/sentence_transformers.py:L9]

```python
class SentenceTransformerEmbedder(VectorSchemaProvider):
    def __init__(
        self,
        model_name_or_path: str,
        *,
        device: str | None = None,           # "cuda", "cpu", or None for auto
        trust_remote_code: bool = False,
    ) -> None: ...

    async def __coco_vector_schema__(self) -> VectorSchema: ...   # auto-discovers dim + dtype
    async def embed(self, text: str) -> NDArray: ...
```
[AST:python/cocoindex/ops/sentence_transformers.py:L25] [:L52]

Replaces v0.3.37's `cocoindex.functions.SentenceTransformerEmbed`. Implements `VectorSchemaProvider` (`cocoindex.resources.schema.VectorSchemaProvider`), so connectors can derive vector column dimensions automatically — no need to pass dim/dtype manually.

```python
EMBEDDER = coco.ContextKey[SentenceTransformerEmbedder]("embedder", detect_change=True)

@coco.lifespan
async def env_lifespan(builder):
    builder.provide(EMBEDDER, SentenceTransformerEmbedder("sentence-transformers/all-MiniLM-L6-v2"))
    yield

@dataclass
class DocEmbedding:
    text: str
    embedding: Annotated[NDArray, EMBEDDER]   # vector schema resolved from the ContextKey at table-schema time
```

## LiteLLM — `cocoindex.ops.litellm`

```python
__all__ = ["LiteLLMEmbedder", "litellm"]
```
[AST:python/cocoindex/ops/litellm.py:L9]

```python
class LiteLLMEmbedder(VectorSchemaProvider):
    def __init__(self, model: str, **kwargs: Any) -> None: ...
    async def __coco_vector_schema__(self) -> VectorSchema: ...   # probes a "hello" embedding to discover dim
    async def embed(self, text: str) -> NDArray: ...
```
[AST:python/cocoindex/ops/litellm.py:L22]

Replaces v0.3.37's `cocoindex.functions.ExtractByLlm` + `LlmSpec` + `LlmApiType` + provider-specific config classes (`OpenAiConfig`, `AzureOpenAiConfig`, `VertexAiConfig`). Now uses LiteLLM's model-string convention:

```python
LiteLLMEmbedder("text-embedding-ada-002")                          # OpenAI
LiteLLMEmbedder("azure/<deployment-id>", api_key=..., api_base=...)  # Azure OpenAI
LiteLLMEmbedder("vertex_ai/textembedding-gecko")                   # Vertex AI
LiteLLMEmbedder("voyage/voyage-3", api_key=...)                    # Voyage
LiteLLMEmbedder("cohere/embed-english-v3.0", api_key=...)          # Cohere
```

Provider configuration flows through `**kwargs` to `litellm.aembedding`. Common kwargs: `api_key`, `api_base`, `api_version`, `dimensions`, `input_type` (Voyage/Cohere). Internally uses `@coco.fn.as_async(batching=True, max_batch_size=64)` for batched embedding ([AST:python/cocoindex/ops/litellm.py:L81]).

The `litellm` symbol in `__all__` is the underlying `litellm` library, re-exported for convenience (lets users access `litellm.completion`, `litellm.acompletion`, etc. without a separate import).

## Entity Resolution — `cocoindex.ops.entity_resolution`

Sub-package (not in `ops/__init__.py`'s `__all__` — import explicitly). [AST:python/cocoindex/ops/entity_resolution/__init__.py:L1]

```python
class CanonicalSide(StrEnum): ...
class PairDecision: ...                    # dataclass for resolver decisions
class ExistingCanonicalPolicy(StrEnum): ...
class ResolutionEvent: ...                 # dataclass
class PairResolver(Protocol): ...
class ResolvedEntities: ...

async def resolve_entities(...) -> ResolvedEntities: ...   # main entry point
```
[AST:python/cocoindex/ops/entity_resolution/__init__.py:L35] [:L46] [:L57] [:L70] [:L97] [:L114] [:L186]

Plus `llm_resolver.py` for an LLM-based `PairResolver` implementation. [AST:python/cocoindex/ops/entity_resolution/llm_resolver.py:L1]

```python
from cocoindex.ops import entity_resolution as er
from cocoindex.ops.entity_resolution.llm_resolver import LLMResolver  # signature TBD — read source
```

The entity-resolution surface is large (363 lines in `__init__.py` alone) — when working with it, read `python/cocoindex/ops/entity_resolution/__init__.py` directly for the full type signatures of `PairDecision`, `ExistingCanonicalPolicy`, `ResolvedEntities`, and the `resolve_entities` async function.
