# `llm/`: Google Gemini clients

Thin wrappers around the Google Gemini API. This is the **only** module that talks to the
LLM provider, so swapping models or providers changes only this directory.

## What goes here

- **Chat client** (`gemini-2.5-flash`): normal and streaming completions
- **Embedding client** (`gemini-embedding-001`): batched embedding for ingestion,
  single-query embedding for retrieval
- Timeouts, retries with exponential backoff, and rate-limit handling
- Token-usage accounting, which feeds the persisted turn and tracing

## Planned files

- `chat.py`
- `embeddings.py`
- `retry.py`: shared retry/backoff policy
