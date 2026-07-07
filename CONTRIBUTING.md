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

# Commit with conventional format, signed off (DCO)
git commit -s -m "feat: description of change"

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

## Developer Certificate of Origin (DCO)

Every commit must be signed off under the [Developer Certificate of Origin](https://developercertificate.org/).
The sign-off certifies that you wrote the change, or otherwise have the right to submit it under the
project's Apache 2.0 license. It is a single trailer line added automatically by `git commit -s`:

```text
Signed-off-by: Your Name <your.email@example.com>
```

Use the same name and email as your commit author identity. A CI check rejects any pull request
whose commits are missing the sign-off.

Practical tips:

- Forgot on the last commit: `git commit --amend -s --no-edit`, then force-push your branch.
- Backfill a whole branch: `git rebase --signoff main`.
- GPG signing (`git commit -S`) is encouraged for maintainers but is separate from the DCO sign-off,
  which is required for everyone.

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
