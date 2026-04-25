# Deployment Guide

This is the no-AI version of the genome engineering app.

- `frontend`: Next.js app for Vercel
- `backend`: FastAPI service for Railway or Render

## Backend: Railway

1. Create a Railway project from this GitHub repository.
2. Set the service root directory to `backend`.
3. Railway can use `backend/railway.json`, or set this start command:

```bash
uvicorn main:app --host 0.0.0.0 --port $PORT
```

4. Add backend environment variables:

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

1. Create a Render Web Service from this GitHub repository.
2. Set root directory to `backend`.
3. Set build command:

```bash
pip install -r requirements.txt
```

4. Set start command:

```bash
uvicorn main:app --host 0.0.0.0 --port $PORT
```

5. Add the same backend environment variables listed above.

## Frontend: Vercel

1. Import this repository into Vercel.
2. Set root directory to `frontend`.
3. Set build command to `npm run build`.
4. Add frontend environment variable:

```env
NEXT_PUBLIC_API_URL=https://your-backend-service-url
```

5. Deploy.

## Post-Deploy Checklist

1. Visit `https://your-backend/health` and confirm `{"status":"ok"}`.
2. Register a test account.
3. Run an analysis.
4. Save the analysis.
5. Confirm it appears on `/history`.

## Security Notes

- Never commit real `.env` files.
- Use a long random `JWT_SECRET_KEY` in production.
- Restrict CORS with `FRONTEND_ORIGIN` set to the deployed Vercel URL.
