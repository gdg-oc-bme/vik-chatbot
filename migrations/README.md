# `migrations/`: database schema migrations

Alembic migrations for the PostgreSQL database. This is the only way the schema changes.
Never edit tables by hand.

## What goes here

- Enabling the `vector` (pgvector) extension
- Tables: `sessions`, `messages`, `chunks`, `feedback` (see `src/vik_chatbot/db/`)
- Indexes:
  - HNSW (or IVFFlat) index on `chunks.embedding` for vector search
  - GIN index on `chunks.tsvector` for keyword search
  - B-tree indexes on `content_hash`, `course_code`, `messages.session_id`

## Planned files

- `env.py`, `script.py.mako`: Alembic boilerplate
- `versions/`: one file per migration
