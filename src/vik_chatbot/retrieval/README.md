# `retrieval/`: hybrid search and reranking

Finds the chunks most relevant to a (rewritten) question.

## Approach

- **Vector search**: embed the query with `gemini-embedding-001` and run a pgvector
  cosine-similarity search over `chunks.embedding`.
- **Keyword search**: Postgres full-text search over `chunks.tsvector`. This catches exact
  terms such as course codes (e.g. `BMEVIAUAC01`) that embeddings tend to blur.
- **Fusion**: Reciprocal Rank Fusion (RRF) merges the two ranked lists.
- **Metadata filters**: optional `course_code`, `doc_type`, `year` filters.
- **Rerank (optional)**: an LLM scores the fused candidates. Keep the top 5 and drop
  near-misses.

## Planned files

- `vector.py`, `keyword.py`: the two searches
- `fusion.py`: RRF (pure function, unit-tested)
- `rerank.py`: optional LLM reranker
- `filters.py`: metadata filter model
- `retriever.py`: `hybrid_retrieve(...)` ties it together
