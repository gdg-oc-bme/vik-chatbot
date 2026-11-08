# `tests/`: automated tests

Pytest test suite.

| Directory       | Scope                                                                 |
|-----------------|-----------------------------------------------------------------------|
| `unit/`         | Pure logic, no network and no DB: RRF fusion, chunking, hashing, prompt rendering, schemas |
| `integration/`  | Real Postgres + pgvector (via docker-compose); Gemini is mocked. Covers API endpoints, repositories, ingestion upsert idempotency |
| `fixtures/`     | Small sample PDFs, pages and canned LLM responses                     |

Tests must never call the real Gemini API. Answer quality is measured by `evals/`, not by
these tests.
