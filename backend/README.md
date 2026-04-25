# No-AI Backend Deployment

FastAPI backend for the no-AI genome engineering app.

## Required Environment Variables

```env
DATABASE_URL=postgresql://postgres:YOUR-PASSWORD@db.rxmacxsziqsqyzzdljrk.supabase.co:5432/postgres
JWT_SECRET_KEY=replace-with-a-long-random-secret
ACCESS_TOKEN_EXPIRE_MINUTES=60
FRONTEND_ORIGIN=https://your-frontend-domain.vercel.app
SUPABASE_URL=https://rxmacxsziqsqyzzdljrk.supabase.co
SUPABASE_ANON_KEY=your-supabase-anon-key
```

`DATABASE_URL` can be either `postgresql://` or `postgresql+psycopg://`; the app normalizes standard Supabase URLs automatically.

## Start Command

```bash
uvicorn main:app --host 0.0.0.0 --port $PORT
```

## Health Check

```text
/health
```

Expected response:

```json
{"status":"ok"}
```

## Notes

- Tables are created on startup from SQLAlchemy models.
- Auth routes require `DATABASE_URL` and `JWT_SECRET_KEY`.
- No OpenAI or AI endpoint exists in this backend.
