# `prompts/`: prompt templates

Every prompt the system sends to the LLM, kept as versioned templates separate from code.

## Planned templates

- `system.md`: assistant persona and rules (answer only from context, cite `[doc, page]`,
  reply in the user's language (Hungarian or English), say when unsure)
- `rewrite.md`: condense the chat history and a follow-up into a standalone question
- `rerank.md`: score the relevance of candidate chunks
- `generate.md`: grounded answer prompt with the retrieved context

## Rule

Any prompt change must be checked against the eval set (`evals/`) before merging.
