# `vik_chatbot`: the Python package

All server-side code lives here: the online request path (API and chat service) and the
offline ingestion job. Both share the same config, DB layer and LLM clients.

| Sub-package      | Purpose                                                        |
|------------------|----------------------------------------------------------------|
| `config/`        | Typed settings loaded from environment / `.env`                |
| `api/`           | HTTP interface (FastAPI)                                        |
| `chat/`          | The per-turn chat pipeline (steps 1–6)                          |
| `retrieval/`     | Hybrid search, RRF fusion, optional reranking                   |
| `llm/`           | Gemini chat and embedding clients                              |
| `prompts/`       | Prompt templates                                                |
| `db/`            | Database models and repositories                                |
| `ingestion/`     | Offline, re-runnable ingestion CLI                              |
| `observability/` | Tracing, logging, metrics                                       |

## Design rules

- **No globals.** Clients, DB pools and settings are built once at startup (API lifespan
  or CLI entry point) and passed in explicitly. That keeps every step easy to test.
- **Plain functions first.** Pipeline steps are ordinary (async) functions. LCEL is
  allowed for composition but not required.
- **Imports flow one way:** `api → chat → {retrieval, llm, db, prompts}`,
  `ingestion → {llm, db}`. Nothing imports `api`.
