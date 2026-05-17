# nuxScript Package Registry — nux-pacotes

Official package registry for [nuxScript](https://github.com/nuxScript/nuxScript).

## 📦 Structure

```
nux-pacotes/
├── packages/
│   ├── std/                    # Standard library (official)
│   │   ├── io/                 # I/O operations
│   │   ├── fs/                 # File system
│   │   ├── http/               # HTTP client/server
│   │   ├── json/               # JSON parsing
│   │   ├── math/               # Advanced math
│   │   ├── strings/            # String utilities
│   │   ├── collections/        # Collection helpers
│   │   ├── os/                 # OS interactions
│   │   ├── regex/              # Regular expressions
│   │   ├── test/               # Testing framework
│   │   ├── sql/                # SQL database
│   │   ├── smtp/               # Email
│   │   ├── template/           # Templates
│   │   ├── crypto/             # Cryptography
│   │   └── compress/           # Compression
│   └── community/              # Community packages
├── spec/                       # Package specification
│   └── PACKAGE_SPEC.md
└── README.md                   # This file
```

## Package Format

Each package lives in `packages/<namespace>/<name>/` and contains:
- `nuxpackage.json` — Package manifest
- `main.nux` — Entry point
- Additional `.nux` files as needed

## Usage

```bash
# Install from registry
nux pkg install std::json
nux pkg install std::http

# Install community package
nux pkg install community::my-package

# List installed packages
nux pkg list

# Remove a package
nux pkg remove std::json
```

## Registry API

The registry is a static file server serving the `packages/` directory.

### Endpoints

| Endpoint | Description |
|----------|-------------|
| `GET /api/packages` | List all available packages |
| `GET /api/packages/:namespace/:name` | Get package info |
| `GET /packages/:namespace/:name/main.nux` | Download package source |
| `GET /api/search?q=query` | Search packages |

## Contributing

1. Fork this repository
2. Add your package under `packages/community/<your-package>/`
3. Include a `nuxpackage.json` manifest
4. Submit a Pull Request

## Documentation

See [nuxScript Docs](https://nux-script-docs.vercel.app/) for language documentation, examples, and guides.

## License

MIT
