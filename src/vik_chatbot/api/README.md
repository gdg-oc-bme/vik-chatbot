# `api/`: FastAPI application

The HTTP interface for every client (Web UI, future Discord/Telegram bots). This layer stays
thin: it validates input, scopes everything to a `session_id`, calls the chat service and
maps results to HTTP responses. **No business logic lives here.**

## Endpoints

| Method   | Path              | Purpose                                              |
|----------|-------------------|------------------------------------------------------|
| `POST`   | `/chat`           | Send a message; the answer streams back as SSE        |
| `GET`    | `/sessions/{id}`  | Fetch a session's history, including sources          |
| `DELETE` | `/sessions/{id}`  | Delete a session and its messages                     |
| `POST`   | `/feedback`       | Rate an answer (thumbs up/down and an optional comment) |

## Responsibilities

- Request/response validation (Pydantic schemas)
- History scoped strictly by `session_id`
- Async handlers and token streaming over Server-Sent Events
- Rate limiting
- Real HTTP error codes (400/404/422/429/502/504), not `200` with an error body
- Building shared clients at startup (lifespan) and injecting them as dependencies

## Planned files

- `app.py`: app factory and lifespan (creates DB pool and Gemini clients)
- `routes/`: `chat.py`, `sessions.py`, `feedback.py`
- `schemas.py`: request/response models
- `dependencies.py`: FastAPI dependency providers
- `errors.py`: exception → HTTP status mapping
