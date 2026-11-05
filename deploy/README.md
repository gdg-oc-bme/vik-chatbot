# `deploy/`: containers and deployment

Everything needed to run the system locally or on a server.

## Planned files

- `docker-compose.yml`: `postgres` (pgvector image), `api`, `ui`
- `Dockerfile.api`: FastAPI service; the ingestion CLI uses the same image
- `Dockerfile.ui`: Streamlit app
- Deployment notes for the target environment (TBD)

Secrets (Gemini API key, DB password) come from environment variables and are never
committed.
