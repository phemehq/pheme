# Contributing to Pheme

## Security

Found a security vulnerability? See `SECURITY.md` for responsible disclosure.

## Setup

**Prerequisites**: Go 1.26+, Python 3.11+, Docker, Docker Compose.

```bash
git clone https://github.com/phemehq/pheme.git
cd pheme

go mod tidy          # Go dependencies
uv sync              # Python dependencies
```

## Code Style

- **Go**: `gofmt -w .` and `golangci-lint run ./...`
- **Python**: `black . --line-length=100` and `ruff check . --fix`; `mypy` on public APIs
- Max line length: 100 characters
- ASCII only; no em/en dashes or non-ASCII punctuation
- Write tests for all new functionality

## Workflow

```bash
# Create feature branch
git checkout -b feature/my-feature

# Make changes and test
go test ./... && pytest python/tests/

# Commit with conventional format
git commit -m "feat: description of change"

# Push and open PR
git push origin feature/my-feature
```

## Commit Messages

Follow [conventional commits](https://www.conventionalcommits.org/):

- `feat:` New feature
- `fix:` Bug fix
- `docs:` Documentation
- `test:` Tests
- `chore:` Build, dependencies

## Testing

All new code must include tests:

```bash
# Go
go test -race ./...

# Python
pytest python/tests/
```

## Questions

Open a [GitHub issue](https://github.com/phemehq/pheme/issues) for bugs or feature requests.
