# `channels/`: other chat channels (later)

Placeholder for additional front ends such as **Discord** and **Telegram** bots.

Like `ui/`, each channel is a **client of the API**. It maps a channel user or thread to a
`session_id` and calls the same HTTP endpoints. Channels never call the chat service,
database or LLM directly.

## Planned layout

- `discord/`
- `telegram/`
