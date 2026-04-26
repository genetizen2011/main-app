# Genome App No AI

Clean genome engineering MVP with Next.js, same-origin API routes, auth, saved analyses, history, and learning pages.

This version intentionally contains no OpenAI dependency, no `/ai/explain` endpoint, and no AI UI.

## Local Setup

### Frontend

```bash
cd frontend
npm install
npm run dev
```

The frontend runs at `http://localhost:3000`.

## Environment Variables

Copy `frontend/.env.example` to `frontend/.env.local` for local development:

```env
APP_JWT_SECRET=replace-with-a-long-random-secret
```

## Deployment

For production deployment steps, see `DEPLOYMENT.md`.

### Vercel

1. Import the repository into Vercel.
2. Set the root directory to `frontend`.
3. Add `APP_JWT_SECRET` as a project environment variable.
4. Deploy with the default Next.js build command, `npm run build`.
