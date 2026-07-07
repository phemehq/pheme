# Pheme: Observability Intelligence Layer

Pheme plugs into an existing Prometheus and Grafana stack and adds an intelligence layer on top:
seasonality-aware anomaly detection, time and label correlation into incidents, and a cited,
restrained AI summary. It is additive and read-only. Remove Pheme and your stack is unchanged.

## What it does

- **Anomaly detection**: a seasonality-aware detector over a curated metric set, benchmarked
  against a static-threshold baseline on a labelled dataset with real precision/recall numbers.
- **Correlation**: groups related anomalies by time and label proximity into incidents,
  measurably reducing alert noise.
- **AI incident summary**: cites the signals and runbook sections it used and never asserts an
  unverified root cause.
- **Grafana native**: one Incident Timeline panel.
- **Read-only**: ingests via `remote_write` and an Alertmanager webhook; never mutates Prometheus,
  Thanos, or Grafana state.

## Architecture

```text
Existing stack (read-only)
   remote_write --+
   Alertmanager --+--> Go service (ingest + API) --> PostgreSQL + pgvector
                                                          ^
                       Python service (detect + correlate + summarize via LiteLLM)
                                                          |
                                            Grafana: Incident Timeline panel
```

Two backend processes, one Grafana panel, one database:

- **Go binary**: `remote_write` receiver + Alertmanager webhook + API server.
- **Python service**: anomaly detector + correlation + LLM summary (via LiteLLM).
- **Grafana panel**: Incident Timeline (TypeScript).
- **PostgreSQL + pgvector**: anomalies, incidents, and runbook embeddings.

## Repository layout

```text
cmd/pheme/       Go binary: remote_write receiver + Alertmanager webhook + API
pkg/             Go shared libraries (metrics, storage)
python/pheme/    Python service: detector + correlation + summary
python/tests/    Python tests
eval/            Labelled dataset + evaluation harness
integrations/    Incident Timeline Grafana panel (TypeScript)
deploy/          docker-compose stack for local development
docs/            Architecture and API docs
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for setup, code style, and workflow.

## Security

To report a vulnerability, see [SECURITY.md](SECURITY.md).

## Future goals

Deliberately out of the current build, revisited once the core is proven: Thanos history backfill,
multi-tenant ingestion, a multi-model detector ensemble, topology-aware causal correlation, an eBPF
network mapper, ClickHouse for columnar query volume, Redis caching, conversational AI chat, and
multi-turn RCA.

## License

Apache License 2.0. See [LICENSE](LICENSE).

**Status**: Early development.
