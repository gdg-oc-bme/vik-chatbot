# `db/`: database models and repositories

Access layer for the single PostgreSQL + pgvector database that holds **all** state.
Other modules call repository functions here and never write raw SQL themselves.

## Tables

| Table      | Contents                                                                 |
|------------|--------------------------------------------------------------------------|
| `sessions` | One row per conversation (`session_id`, timestamps)                      |
| `messages` | History: role, text, sources per answer, latency, tokens                  |
| `chunks`   | `text`, `embedding` (vector), `tsvector`, `course_code`, `doc_type`, `year`, `source`, `page`, `content_hash` |
| `feedback` | Rating and comment per answer (FK to `messages`)                          |

## Planned files

- `engine.py`: async engine and session/pool factory
- `models.py`: ORM / table definitions
- `repositories/`: `sessions.py`, `messages.py`, `chunks.py`, `feedback.py`

Schema changes are made as migrations in [`/migrations`](../../../migrations).
