# `data/`: raw source documents

Input for the ingestion job: official BME VIK documents the chatbot answers from.

## What goes here

- PDFs: curricula, study and exam regulations, subject descriptions, guides
- Snapshots of faculty web pages
- Course catalog export(s)

## Notes

- **Contents are git-ignored** because of file size and redistribution rights. Only this
  README is committed. Document where each source comes from (URL, date fetched) in
  `SOURCES.md` here, so the corpus can be rebuilt.
- Descriptive file names help citations, e.g. `2025-26_study_regulations.pdf`.
