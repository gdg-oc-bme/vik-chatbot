# `ingestion/`: offline ingestion job

A re-runnable CLI that turns raw university documents into embedded, searchable chunks in
Postgres. It runs separately from the API (manually, or on a schedule).

## Stages

1. **Sources**: `data/*.pdf`, faculty web pages, course catalog export
2. **Parse**: extract text and tables per page and keep the source and page number
3. **Chunk by structure**: one course = one chunk where possible. Tag each chunk with
   `course_code`, `doc_type`, `academic year`
4. **Embed**: batched calls to `gemini-embedding-001`, with retries
5. **Upsert by hash**: idempotent. Skip chunks whose `content_hash` is unchanged,
   remove chunks of deleted documents, never wipe the table

## Planned files

- `cli.py`: entry point (`python -m vik_chatbot.ingestion ...`)
- `sources/`: one loader per source type (`pdf.py`, `web.py`, `catalog.py`)
- `parse.py`, `chunk.py`, `embed.py`, `upsert.py`
