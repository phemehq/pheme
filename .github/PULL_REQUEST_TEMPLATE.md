<!--
PR title should follow Conventional Commits, e.g.:
  feat(bridge): add remote_write receiver
Keep PRs small and single-responsibility.
-->

## Summary

Brief summary of changes and intent, not a file list.

## Related issue

<!-- Use "Closes #N" to auto-close on merge, or "Refs #N" if it only relates. -->

Closes #

## Type of change

- [ ] Bug fix (non-breaking)
- [ ] Feature (non-breaking)
- [ ] Breaking change
- [ ] Documentation update

## Testing

New or changed functionality requires automated tests (see CONTRIBUTING.md).

- [ ] `go test ./...` passes
- [ ] `pytest python/tests/` passes
- [ ] New/changed code has corresponding test cases
- [ ] Manual testing completed (if applicable)

**Test details:**

```text
Environment: (local, Docker, etc.)
Notes:
```

## Checklist

- [ ] PR title uses Conventional Commits.
- [ ] Change is single-responsibility and small enough to review in one sitting.
- [ ] Linting passes (`gofmt`, `golangci-lint`, `ruff`, `black`).
- [ ] Self-review completed; comments added for complex logic.
- [ ] Documentation updated if needed.
- [ ] Tests added or updated for all new functionality.
- [ ] CI checks pass.
