# nuxScript Package Specification v1.0

## Package Structure

```
<package-name>/
├── nuxpackage.json    # Required: Package manifest
├── main.nux          # Required: Entry point
├── lib/              # Optional: Additional modules
│   └── helper.nux
└── README.md         # Optional: Package documentation
```

## Manifest (`nuxpackage.json`)

```json
{
  "name": "package-name",
  "version": "1.0.0",
  "description": "Short description",
  "main": "main.nux",
  "author": "Author Name",
  "license": "MIT",
  "dependencies": {
    "std::json": "^1.0.0"
  },
  "keywords": ["json", "parser"],
  "repository": {
    "type": "git",
    "url": "https://github.com/nuxScript/nux-pacotes"
  }
}
```

### Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | String | Yes | Package name (namespace::name) |
| `version` | String | Yes | SemVer version |
| `description` | String | Yes | Short description |
| `main` | String | Yes | Entry point file |
| `author` | String | No | Author name/email |
| `license` | String | No | SPDX license identifier |
| `dependencies` | Object | No | Package dependencies |
| `keywords` | Array | No | Search keywords |
| `repository` | Object | No | Source repository info |

## Package Exports

A package exports functions using the `export` keyword:

```nux
# main.nux
fn greet(name :: String) -> String
    "Hello, " + name
end

fn add(a, b)
    a + b
end

export greet
export add
```

## Versioning

Packages follow SemVer (MAJOR.MINOR.PATCH):
- MAJOR: Breaking changes
- MINOR: New features (backwards compatible)
- PATCH: Bug fixes (backwards compatible)

## Resolution

When `nux pkg install std::json` is run:
1. The registry is queried for `packages/std/json/` 
2. The manifest is read from `nuxpackage.json`
3. Dependencies are resolved recursively
4. Files are copied to `nux_modules/std::json/`
5. The manifest is updated in the project's `nuxpackage.json`
