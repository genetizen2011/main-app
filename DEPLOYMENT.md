# Deployment Guide

This is the no-AI version of the genome engineering app.

- `frontend`: Next.js app for Vercel, including same-origin API routes
- `backend`: legacy FastAPI service retained for reference

## Frontend: Vercel

1. Import the repository into Vercel.
2. Set the root directory to `frontend`.
3. Set build command to `npm run build`.
4. Set output/framework to Next.js.
5. Add:

```env
APP_JWT_SECRET=replace-with-a-long-random-secret
```

The app calls only relative `/api/...` routes, so no public API base URL is required.

## Optional Legacy Backend

The FastAPI backend can still be run separately for reference or migration work.
If deploying it, add these backend variables:

```env
DATABASE_URL=postgresql://postgres:YOUR-PASSWORD@db.rxmacxsziqsqyzzdljrk.supabase.co:5432/postgres
JWT_SECRET_KEY=replace-with-a-long-random-secret
ACCESS_TOKEN_EXPIRE_MINUTES=60
FRONTEND_ORIGIN=https://your-vercel-app.vercel.app
SUPABASE_URL=https://rxmacxsziqsqyzzdljrk.supabase.co
SUPABASE_ANON_KEY=your-supabase-anon-key
```

`DATABASE_URL` may use either `postgresql://` or `postgresql+psycopg://`.

## Backend: Render

1. Use the included `render.yaml` blueprint, or create a Render Web Service manually from this GitHub repository.
2. If configuring manually, set root directory to `backend`.
3. Set build command:

```bash
pip install -r requirements.txt
```

4. Set start command:

```bash
uvicorn main:app --host 0.0.0.0 --port $PORT
```

5. Add the same backend environment variables listed above.

Render health check path:

```text
/health
```

## Backend: Docker

The backend can also be deployed from `backend/Dockerfile`.

```bash
cd backend
docker build -t genome-app-no-ai-backend .
docker run -p 8000:8000 --env-file .env genome-app-no-ai-backend
```

## Post-Deploy Checklist

1. Register a test account from the frontend.
2. Run an analysis.
3. Save the analysis and confirm it appears on `/history`.

## Security Notes

- Never commit real `.env` files.
- Use a long random `APP_JWT_SECRET` in production.
- The in-app auth and cloud history store are in-memory for this MVP; use a database-backed store before relying on accounts for durable production data.
