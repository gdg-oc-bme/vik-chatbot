# `ui/`: Web UI

The student-facing chat interface. **Streamlit for now**; a React/Next.js frontend may
replace it later.

## Rules

- The UI is an **API client only**. It calls the FastAPI endpoints (JSON for requests,
  SSE for streamed answers) and never touches the database or Gemini directly.
- It holds only a `session_id`. All history lives on the server.
- It shows the sources (`[doc, page]`) under each answer and offers a thumbs up/down
  control that posts to `/feedback`.

## Planned files

- `app.py`: Streamlit entry point
- `api_client.py`: small HTTP/SSE client for the backend
