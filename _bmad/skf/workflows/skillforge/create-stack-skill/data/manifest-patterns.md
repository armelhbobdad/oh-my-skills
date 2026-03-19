# Manifest Detection Patterns

## Supported Ecosystems

| Ecosystem | Manifest File(s) | Dependency Key | Import Pattern |
|-----------|-----------------|----------------|----------------|
| JavaScript/TypeScript | package.json | dependencies, devDependencies | `import ... from '...'`, `require('...')` |
| Python | requirements.txt, setup.py, pyproject.toml, Pipfile | install_requires, [project.dependencies] | `import ...`, `from ... import` |
| Rust | Cargo.toml | [dependencies] | `use ...`, `extern crate` |
| Go | go.mod | require | `import "..."` |
| Java | pom.xml, build.gradle | dependencies | `import ...` |
| Ruby | Gemfile | gem | `require '...'`, `require_relative` |
| PHP | composer.json | require, require-dev | `use ...`, `require_once` |
| .NET | *.csproj | PackageReference | `using ...` |

## Detection Priority

1. Search project root for manifest files (depth 0-1)
2. Parse each found manifest to extract dependency names
3. Normalize names across ecosystems (e.g., `@scope/package` → `package`)
4. Deduplicate across multiple manifests

## Filtering Rules

- Exclude dev-only dependencies unless they appear in production imports
- Exclude build tools (webpack, babel, eslint, etc.) unless significantly imported
- Include all runtime dependencies by default
- Flag transitive dependencies that appear in direct imports

## Import Counting

For each dependency, count distinct files that import it:
- Use grep patterns from Import Pattern column
- Count unique file paths, not total import statements
- Exclude test files, config files, and build artifacts from count
