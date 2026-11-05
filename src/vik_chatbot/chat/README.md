# `chat/`: chat service (the per-turn pipeline)

Runs one user turn from question to persisted, cited answer. It is built from plain
functions or LCEL, with no globals, so each step can be tested and traced on its own.

## Pipeline

1. **Load history** (DB): the last N turns for this `session_id`.
2. **Rewrite query** (LLM): turns a follow-up ("and its prerequisites?") into a
   standalone question. Skipped when there is no history.
3. **Hybrid retrieve** (EMB, DB): delegated to `retrieval/`.
4. **Rerank** (LLM, optional): delegated to `retrieval/`; keeps the top 5.
5. **Generate, streamed** (LLM): grounded prompt from `prompts/`. The answer must
   cite `[doc, page]` and must say "I don't know" when the context lacks the answer.
6. **Persist turn** (DB): stores the answer, sources, latency and token counts.

## Planned files

- `service.py`: `answer_turn(...)` orchestrates steps 1–6 and yields tokens
- `history.py`: step 1
- `rewrite.py`: step 2
- `generate.py`: step 5, including citation formatting
- `persist.py`: step 6
- `types.py`: `Turn`, `Source`, `Answer` data classes
