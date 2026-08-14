# Rosxy Panel — GitHub + Vercel

## Deploy to Vercel

Connect this repository to Vercel or run:

```bash
npx vercel
```

No build command is required for the static panel.

## Health check

After deployment:

```text
https://YOUR-DOMAIN/health
```

The endpoint is served by `api/health.js`.

## Secrets

Never commit Telegram bot tokens, Firebase private keys, passwords, or other secrets to GitHub.

Use Vercel Environment Variables for server-side secrets:

```text
TELEGRAM_BOT_TOKEN
TELEGRAM_CHAT_ID
```

## Local preview

A static preview can be served with:

```bash
python -m http.server 8080
```

Then open `http://127.0.0.1:8080/`.

The Vercel health function itself is deployed by Vercel and is not available through the plain Python static server.

## Repository layout

- `index.html` — panel
- `api/health.js` — Vercel health function
- `vercel.json` — Vercel routing/security headers
- `.gitignore` — secret/local-file protection


## Authentication
This build uses a single dedicated Secret Admin login. Configure `ADMIN_USERNAME`, `ADMIN_PASSWORD`, and `ADMIN_SESSION_SECRET` in Vercel Environment Variables. Never commit them to GitHub.
