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

Copy `.env.example` to `.env.local` for local development. The Next.js app also
loads `frontend/.env.local` when running from `frontend/`.

```env
APP_JWT_SECRET=your-random-32-char-secret-here
```

## Deployment

For production deployment steps, see `DEPLOYMENT.md`.

### Vercel

1. Import the repository into Vercel.
2. Deploy from `main`; `vercel.json` sets the root directory to `frontend`.
3. Add the variables from `.env.example` in Vercel Project Settings.
4. Deploy with the default Next.js build command, `npm run build`.
