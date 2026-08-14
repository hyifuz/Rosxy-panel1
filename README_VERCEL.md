# Rosxy Panel — Vercel Deployment

## Deploy

Upload this folder/repository to Vercel, or run:

```bash
npx vercel
```

No build command is required for the static panel.

## Health check

After deployment:

```text
https://YOUR-DOMAIN/health
```

Expected JSON:

```json
{
  "status": "ok",
  "service": "rosxy-panel",
  "version": "2.4",
  "platform": "vercel"
}
```

The previous long-running `server.py` is not used by Vercel. Vercel uses `api/health.js` as a serverless function.

## Telegram monitoring

Point the external monitor at:

```text
https://YOUR-DOMAIN/health
```

Keep the Telegram bot token on the external monitor, never in the browser files.

## Important

Firebase/client-side configuration remains subject to the Firebase security rules of the project. Never place service-account private keys or other server-only secrets in the HTML.
