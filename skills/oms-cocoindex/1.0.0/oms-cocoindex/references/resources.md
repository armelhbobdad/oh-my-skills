# Resources — `cocoindex.resources.*`

First-class data types referenced throughout cocoindex. Not a "subset of internals" — connectors and `@coco.fn` signatures depend on these types directly.

## Chunk — `cocoindex.resources.chunk`

```python
__all__ = ["Chunk", "TextPosition"]
```
[SRC:python/cocoindex/resources/chunk.py:L5]

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
`TextPosition` [AST:python/cocoindex/resources/chunk.py:L9] · `Chunk` [AST:python/cocoindex/resources/chunk.py:L26]

Returned by `cocoindex.ops.text.RecursiveSplitter.split()` and `SeparatorSplitter.split()`. Always frozen; safe as a dict key when paired with `__hash__`.

## File — `cocoindex.resources.file`

```python
__all__ = [
    "FileMetadata", "FileLike",
    "FilePath", "FilePathMatcher",
    "MatchAllFilePathMatcher", "PatternFilePathMatcher",
]
```
[SRC:python/cocoindex/resources/file.py:L5]

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

    # Subclasses implement these (abstract):
    async def _fetch_metadata(self) -> FileMetadata: ...
    async def _read_impl(self, size: int = -1) -> bytes: ...      # size=-1 reads the whole file
    # Optional override:
    async def _compute_content_fingerprint(self) -> bytes: ...     # default: metadata fingerprint, else hash of the content

    # Public API (cached):
    async def size(self) -> int: ...                               # from the lazily fetched FileMetadata
    async def read(self, size: int = -1) -> bytes: ...             # full reads (size < 0) are cached
    async def read_text(self, encoding: str | None = None, errors: str = "replace") -> str: ...   # encoding=None: BOM detection, else UTF-8
    async def content_fingerprint(self) -> bytes: ...
```
[SRC:python/cocoindex/resources/file.py:L101] [:L115] [:L160] [:L108] [:L122] [:L143] [:L172]

`FileLike` has no public accessor for the whole `FileMetadata`: `size()` is the one metadata read it exposes, and the cached metadata sits behind the private `_ensure_metadata()` [SRC:python/cocoindex/resources/file.py:L94].

`FileLike` is what `localfs.File`, `amazon_s3.S3File`, `google_drive.DriveFile` all inherit from. When you write a custom source, subclass `FileLike[YourPathType]` and implement its two abstract methods, `_fetch_metadata` and `_read_impl`.

### FilePathMatcher

Protocol for filtering paths. [AST:python/cocoindex/resources/file.py:L205]

```python
class FilePathMatcher(Protocol):
    def is_dir_included(self, path: PurePath) -> bool: ...    # traverse this directory?
    def is_file_included(self, path: PurePath) -> bool: ...   # include this file?

class MatchAllFilePathMatcher(FilePathMatcher): ...   # includes every directory and file
class PatternFilePathMatcher(FilePathMatcher):
    def __init__(self, included_patterns: list[str] | None = None,
                 excluded_patterns: list[str] | None = None) -> None: ...
```
[SRC:python/cocoindex/resources/file.py:L208] [:L211] · [AST:python/cocoindex/resources/file.py:L215] [:L227] · `__init__` [SRC:python/cocoindex/resources/file.py:L240]

`localfs.walk_dir` asks `is_dir_included` before descending into a directory and `is_file_included` before yielding a file, each with the path relative to the walk root; `amazon_s3.list_objects` asks only `is_file_included`, with the key relative to its prefix. [SRC:python/cocoindex/connectors/localfs/_source.py:L125] [:L130] · [SRC:python/cocoindex/connectors/amazon_s3/_source.py:L305]

Pattern syntax: globset globs matched against the full relative path with forward slashes (`**/*.md` at any depth, `*.md` in the root only, `{*.md,*.txt}` for alternation); an excluded directory excludes everything under it. [SRC:python/cocoindex/resources/file.py:L230] Standard idiom:

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
    def base_dir(self) -> ContextKey[ResolvedPathT] | None: ...   # stable key of the base directory (for memoization)
    @property
    def path(self) -> PurePath: ...               # the path relative to base_dir
    def resolve(self) -> ResolvedPathT: ...        # abstract: the backend-native full path (pathlib.Path for localfs, a str key for S3)
    # plus PurePath-like members: /, parent, parents, name, stem, suffix, suffixes, parts,
    # with_name, with_stem, with_suffix, with_segments, is_absolute, is_relative_to,
    # relative_to, match, as_posix, joinpath
```
[SRC:python/cocoindex/resources/file.py:L339] [:L344] [:L352]

`file.file_path.path` is a `PurePath` whichever backend the file came from, which is why the Quick Start can pass it as `filename: pathlib.PurePath`; call `resolve()` when you need the backend path itself.

## ID — `cocoindex.resources.id`

```python
__all__ = ["IdGenerator", "UuidGenerator", "generate_id", "generate_uuid"]
```
[SRC:python/cocoindex/resources/id.py:L20]

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
    def next_uuid(self, dep: Any = None) -> uuid.UUID: ...
```
[AST:python/cocoindex/resources/id.py:L152] · `next_uuid` [SRC:python/cocoindex/resources/id.py:L190]

Returns a **distinct** ID on each call, even for the same `dep`. `next_id` is async (await it); `next_uuid` is a plain `def`, called without `await`, like `generate_uuid`. Use when you need multiple IDs for potentially non-distinct inputs (e.g., chunk-by-chunk indexing where chunks may share text). Sequence is stable across runs.

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
[SRC:python/cocoindex/resources/schema.py:L67]

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
class FixedSizeEmbedder:                   # any object with this method is a VectorSchemaProvider
    async def __coco_vector_schema__(self) -> VectorSchema:
        return VectorSchema(dtype=np.dtype(np.float32), size=384)
```

`SentenceTransformerEmbedder` and `LiteLLMEmbedder` do not hard-code a size: theirs ask the model for its dimension. [SRC:python/cocoindex/ops/sentence_transformers.py:L152] [SRC:python/cocoindex/ops/litellm.py:L135]

## Embedder — `cocoindex.resources.embedder`

```python
__all__ = ["Embedder"]
```
[SRC:python/cocoindex/resources/embedder.py:L11]

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
