# Contributing to Pheme

## Security

Found a security vulnerability? See `SECURITY.md` for responsible disclosure.

## Code Style

- **Go**: `gofmt -w .` and `golangci-lint run ./...`
- **Python**: `black . --line-length=100` and `ruff check . --fix`; `mypy` on public APIs
- Max line length: 100 characters
- ASCII only; no em/en dashes or non-ASCII punctuation
- Write tests for all new functionality

## Setup

Install the git hooks once after cloning. They run formatting, linting, and a
conventional-commit check locally so problems surface before CI:

```bash
uv tool install pre-commit   # or: pipx install pre-commit
pre-commit install
```

`pre-commit install` wires up both the pre-commit and commit-msg hooks, as declared by
`default_install_hook_types` in `.pre-commit-config.yaml`.

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

- `feat:`     New feature
- `fix:`      Bug fix
- `docs:`     Documentation
- `test:`     Tests
- `refactor:` Code change that neither fixes a bug nor adds a feature
- `perf:`     Performance improvement
- `ci:`       CI/CD config and workflows
- `build:`    Build system or dependencies
- `chore:`    Other maintenance

## Developer Certificate of Origin (DCO)

Every commit must be signed off under the [Developer Certificate of Origin](https://developercertificate.org/).
The sign-off certifies that you wrote the change, or otherwise have the right to submit it under the
project's Apache 2.0 license. It is a single trailer line added automatically by `git commit -s`:

```text
Signed-off-by: Your Name <your.email@example.com>
```

Use the same name and email as your commit author identity. The [CNCF DCO2 app](https://github.com/apps/dco-2)
checks every pull request and reports which commits pass or fail; a failing check blocks the merge.

If a commit on your PR is missing its sign-off, amend it (`git commit --amend -s --no-edit` for the
last commit, or `git rebase --signoff <default-branch>` for the whole branch) and force-push your branch. If the
commits are already merged and can't be rewritten, the failed check links to DCO2's
[remediation commit](https://github.com/cncf/dco2#remediation-commits) instructions.

GPG signing (`git commit -S`) is encouraged for maintainers but is separate from the DCO sign-off,
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
