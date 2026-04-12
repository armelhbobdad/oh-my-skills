# Output Contract Schema

Every pipeline-capable skill writes a result JSON file at its final step. This enables reliable CI integration and pipeline chaining.

## Schema

```json
{
  "skill": "skf-skill-name",
  "status": "success" | "failed" | "partial",
  "timestamp": "ISO-8601",
  "outputs": [
    {"type": "report|skill|manifest|config", "path": "relative/path/to/file"}
  ],
  "summary": {
    // skill-specific summary fields
  }
}
```

## Filenames

Each run writes **two files** to `{output_dir}`:

1. **Per-run record** (audit trail): `{skill-name}-result-{YYYYMMDD-HHmmss}.json`
   - Timestamp is UTC, resolution to seconds — e.g., `update-skill-result-20260413-145230.json`
   - Never overwritten by subsequent runs — preserves a durable audit trail across retries, aborts, and re-runs
2. **Stable latest pointer** (pipeline consumption): `{skill-name}-result-latest.json`
   - A **copy** (not a symlink) of the per-run record just written
   - Always present at a deterministic path so CI / pipelines / the forger can read `summary.*` without enumerating timestamps
   - Overwritten on every successful write

Write the per-run record first, then copy it to the `-latest.json` path. If the copy fails, the per-run record still exists — the run is not lost.

**Consumers (forger, CI, chained workflows):** read from `{skill-name}-result-latest.json`. Do not enumerate timestamped files unless inspecting prior-run history.
