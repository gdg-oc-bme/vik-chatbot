# `config/`: shared settings

The **single place** where configuration is read. A `pydantic-settings` `Settings` class
loads values from environment variables and `.env`, validates them, and is passed to the
rest of the app. No other module reads `os.environ` directly.

## What goes here

- Model names: chat (`gemini-2.5-flash`) and embedding (`gemini-embedding-001`)
- Retrieval knobs: vector `k`, keyword `k`, RRF constant, rerank top-N (default 5),
  history window N
- `DATABASE_URL`, connection-pool size
- Gemini API key, timeouts, retry counts
- Rate-limit settings, CORS origins
- Tracing keys and on/off switch

## Planned files

- `settings.py`: the `Settings` class and a `get_settings()` factory

A matching `.env.example` at the repository root lists every variable.
