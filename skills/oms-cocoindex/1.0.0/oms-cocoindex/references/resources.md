# Resources — `cocoindex.resources.*`

First-class data types referenced throughout cocoindex. Not a "subset of internals" — connectors and `@coco.fn` signatures depend on these types directly.

## Chunk — `cocoindex.resources.chunk`

```python
__all__ = ["Chunk", "TextPosition"]
```
[AST:python/cocoindex/resources/chunk.py:L5]

```python
@dataclass(frozen=True, slots=True)
class TextPosition:
    byte_offset: int      # byte offset from start of text
    char_offset: int      # character (not byte) offset from start of text
    line: int             # 1-based line number
    column: int           # 1-based column number

@dataclass(frozen=True, slots=True)
class Chunk:
    text: str
    start: TextPosition
    end: TextPosition
```
[AST:python/cocoindex/resources/chunk.py:L8] [:L25]

Returned by `cocoindex.ops.text.RecursiveSplitter.split()` and `SeparatorSplitter.split()`. Always frozen; safe as a dict key when paired with `__hash__`.

## File — `cocoindex.resources.file`

```python
__all__ = [
    "FileMetadata", "FileLike",
    "FilePath", "FilePathMatcher",
    "MatchAllFilePathMatcher", "PatternFilePathMatcher",
]
```
[AST:python/cocoindex/resources/file.py:L5]

### FileMetadata

```python
class FileMetadata(NamedTuple):
    size: int
    modified_time: datetime
    content_fingerprint: bytes | None = None     # backend-provided fingerprint (e.g. S3 ETag)
```
[AST:python/cocoindex/resources/file.py:L40]

### FileLike

Abstract base for file-like objects with lazy metadata, content caching, and memoization. Generic over `ResolvedPathT` (e.g. `pathlib.Path` for localfs, S3 key for S3). [AST:python/cocoindex/resources/file.py:L56]

```python
class FileLike(ABC, Generic[ResolvedPathT]):
    def __init__(self, file_path: FilePath[ResolvedPathT], *, _metadata: FileMetadata | None = None): ...

    @property
    def file_path(self) -> FilePath[ResolvedPathT]: ...

    # Subclasses implement these:
    async def _fetch_metadata(self) -> FileMetadata: ...
    async def _read_impl(self) -> bytes: ...
    async def _compute_content_fingerprint(self) -> bytes: ...     # default: hash content if metadata fingerprint absent

    # Public API (cached):
    async def metadata(self) -> FileMetadata: ...
    async def read(self) -> bytes: ...
    async def read_text(self, encoding: str | None = None, errors: str = "strict") -> str: ...
    async def content_fingerprint(self) -> bytes: ...
```

`FileLike` is what `localfs.File`, `amazon_s3.S3File`, `google_drive.DriveFile` all inherit from. When you write a custom source, subclass `FileLike[YourPathType]` and implement the two `_*_impl` methods.

### FilePathMatcher

Protocol for filtering paths. [AST:python/cocoindex/resources/file.py:L205]

```python
class FilePathMatcher(Protocol):
    def matches(self, path: PurePath) -> bool: ...

class MatchAllFilePathMatcher(FilePathMatcher): ...   # matches everything
class PatternFilePathMatcher(FilePathMatcher):
    def __init__(self, *, included_patterns: list[str] | None = None,
                          excluded_patterns: list[str] | None = None) -> None: ...
```
[AST:python/cocoindex/resources/file.py:L215] [:L227]

Pattern syntax: `pathlib`-style globs (`**/*.md`, `src/**/*.py`). Standard idiom:

```python
files = localfs.walk_dir(sourcedir, recursive=True,
    path_matcher=PatternFilePathMatcher(
        included_patterns=["**/*.md", "**/*.txt"],
        excluded_patterns=["**/node_modules/**"],
    ))
```

### FilePath

Generic wrapper around a backend-resolved path. [AST:python/cocoindex/resources/file.py:L304]

```python
class FilePath(Generic[ResolvedPathT]):
    @property
    def path(self) -> ResolvedPathT: ...           # backend-native path (e.g. pathlib.Path)
    @property
    def relative_path(self) -> PurePath: ...       # always PurePath, comparable across backends
```

Used in `@coco.fn` signatures so user code can write `filename: pathlib.PurePath` portably across `localfs` and `S3` sources.

## ID — `cocoindex.resources.id`

```python
__all__ = ["IdGenerator", "UuidGenerator", "generate_id", "generate_uuid"]
```
[AST:python/cocoindex/resources/id.py:L20]

Two patterns for stable IDs.

### Idempotent stable IDs (one ID per unique input)

```python
@coco.fn(memo=True)
async def generate_id(_dep: Any = None) -> int: ...
```
[AST:python/cocoindex/resources/id.py:L31]

```python
@coco.fn(memo=True)
def generate_uuid(_dep: Any = None) -> uuid.UUID: ...
```
[AST:python/cocoindex/resources/id.py:L61]

Returns the **same** ID/UUID for the **same** `dep` value within a component. Use when each unique input maps to exactly one ID. IDs start at 1 (0 is reserved).

### Distinct stable IDs (multiple IDs even for identical inputs)

```python
class IdGenerator(coco.NotMemoKeyable):
    def __init__(self, deps: Any = None) -> None: ...
    async def next_id(self, dep: Any = None) -> int: ...
```
[AST:python/cocoindex/resources/id.py:L89]

```python
class UuidGenerator(coco.NotMemoKeyable):
    def __init__(self, deps: Any = None) -> None: ...
    async def next_uuid(self, dep: Any = None) -> uuid.UUID: ...
```
[AST:python/cocoindex/resources/id.py:L152]

Returns a **distinct** ID on each call, even for the same `dep`. Use when you need multiple IDs for potentially non-distinct inputs (e.g., chunk-by-chunk indexing where chunks may share text). Sequence is stable across runs.

Both generators inherit from `coco.NotMemoKeyable` — they cannot be used as memoization keys (they hold mutable state).

```python
@coco.fn(memo=True)
async def process_doc(doc: Document, table) -> None:
    id_gen = IdGenerator(doc.path)
    for chunk in split(doc.content):
        chunk_id = await id_gen.next_id(chunk.text)
        table.declare_row(row=Row(id=chunk_id, text=chunk.text))
```

## Schema — `cocoindex.resources.schema`

```python
__all__ = [
    "MultiVectorSchema", "MultiVectorSchemaProvider",
    "VectorSchema", "VectorSchemaProvider",
    "get_multi_vector_schema", "get_vector_schema",
]
```
[AST:python/cocoindex/resources/schema.py:L67]

```python
@runtime_checkable
class VectorSchemaProvider(Protocol):
    """Additional information for a vector column."""
    def __coco_vector_schema__(self) -> Awaitable[VectorSchema]: ...

class VectorSchema(msgspec.Struct, frozen=True, tag=True):
    dtype: np.dtype
    size: int
    async def __coco_vector_schema__(self) -> VectorSchema: ...   # self-providing
```
[AST:python/cocoindex/resources/schema.py:L17] [:L23]

```python
async def get_vector_schema(obj: object) -> VectorSchema | None: ...
```
[AST:python/cocoindex/resources/schema.py:L33]

`get_vector_schema` accepts a `ContextKey` (looks it up via `coco.use_context`), an instance implementing `VectorSchemaProvider`, or anything else (returns `None`). This is what connector targets call when resolving an `Annotated[NDArray, EMBEDDER]` column type — they walk the annotation, hit a `ContextKey`, and ask for its provider's schema.

`MultiVectorSchema` / `MultiVectorSchemaProvider` are the analog for multi-vector embeddings (ColPali-style); same shape but with a `vector_schema: VectorSchema` field.

```python
class SentenceTransformerEmbedder(VectorSchemaProvider):
    async def __coco_vector_schema__(self) -> VectorSchema:
        return VectorSchema(dtype=np.float32, size=384)
```

## Embedder — `cocoindex.resources.embedder`

```python
__all__ = ["Embedder"]
```
[AST:python/cocoindex/resources/embedder.py:L11]

```python
@runtime_checkable
class Embedder(Protocol):
    async def embed(self, text: str) -> NDArray: ...
```
[AST:python/cocoindex/resources/embedder.py:L15]

Common Protocol implemented by `SentenceTransformerEmbedder`, `LiteLLMEmbedder`, and any custom embedder. Lets `@coco.fn` signatures be written generically:

```python
@coco.fn
async def process(text: str, embedder: Embedder) -> NDArray:
    return await embedder.embed(text)
```
