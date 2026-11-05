# `observability/`: tracing, logging, metrics

Makes every answer explainable after the fact.

## What goes here

- **Tracing**: a Langfuse / LangSmith span for every pipeline step (history, rewrite,
  retrieve, rerank, generate, persist), with inputs, outputs, latency and tokens
- **Logging**: structured (JSON) logging setup, with request and session IDs attached
- **Metrics**: latency, token usage, error rates, feedback ratio

Tracing must be switchable off through config and must never break a request when the
tracing backend is down.

## Planned files

- `tracing.py`: span helpers and decorators
- `logging.py`: logger configuration
