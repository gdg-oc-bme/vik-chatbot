# `evals/`: evaluation set and runner

Measures whether changes to prompts, chunking, retrieval or models make answers better or
worse. **Run before merging** any change that touches the pipeline.

## What goes here

- `golden.jsonl`: about 50 golden Q&As. Each holds a question, the expected answer (or key
  facts) and the expected source documents and pages. Cover both Hungarian and English
  questions, follow-ups, and questions the bot should decline.
- `run.py`: runs the golden set against the pipeline and writes a report
- `metrics.py`:
  - retrieval: hit@k / recall@k against the expected sources
  - answer: correctness and faithfulness (LLM-as-judge), citation accuracy
  - latency and token cost
- `reports/`: generated results (git-ignored)

Questions that come in through the feedback loop (thumbs-down) should be added to the golden
set once they are fixed.
