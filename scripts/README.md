# `scripts/`: helper scripts

Small developer and operations utilities that are not part of the application itself.

## Examples of what goes here

- Starting a local dev environment (database and API)
- Resetting or seeding a local database
- Exporting thumbs-down feedback for review (feedback loop: review, then fix data or prompt)
- One-off data maintenance tasks

Reusable logic belongs in `src/vik_chatbot/`. Scripts should only call into it.
