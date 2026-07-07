# Changelog

All notable changes to Pheme will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project will adhere to [Semantic Versioning](https://semver.org/spec/v2.0.0.html) once v1.0.0 is released.

## [Unreleased]

### Added

- Project initialization: repository layout, Go module (Go 1.26), Apache 2.0 license.
- Project documentation: README, CONTRIBUTING, SECURITY, CHANGELOG.
- GitHub workflows and templates: PR template, issue notifier, docs publishing.

### Planned

- Go service: `remote_write` receiver + Alertmanager webhook + API server (single binary).
- Python service: seasonality-aware anomaly detector + correlation + LLM summary via LiteLLM.
- PostgreSQL + pgvector storage for anomalies, incidents, and runbook embeddings.
- Incident Timeline Grafana panel.
- Labelled dataset and evaluation harness (precision/recall/latency vs a static-threshold baseline).
- docker-compose dev environment (Prometheus, Postgres+pgvector, Grafana).

---

**Development branch**: `devel`
**Stable branch**: None yet (pre-release)
