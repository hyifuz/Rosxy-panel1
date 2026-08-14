# Rosxy Secret Admin — Single Access

This deployment uses **one dedicated administrator authentication path**.

Environment variables in Vercel:

```text
ADMIN_USERNAME=your_admin_username
ADMIN_PASSWORD=your_strong_admin_password
ADMIN_SESSION_SECRET=<32+ character random secret>
```

Generate a session secret:

```bash
python -c "import secrets; print(secrets.token_urlsafe(48))"
```

Admin endpoints:

- `POST /api/admin-login`
- `GET /api/admin-me`
- `POST /api/admin-logout`

There is no separate normal-user password login in this build.

Security properties:

- Credentials stay server-side in Vercel Environment Variables.
- Password is never embedded in `index.html`.
- Admin session is signed with HMAC-SHA256.
- Session cookie is HttpOnly, Secure, and SameSite=Strict.
- Sessions expire automatically.

For an additional production access layer, Vercel Deployment Protection/SSO can be enabled where supported.


## Telegram alerts
Set `TELEGRAM_BOT_TOKEN` and `TELEGRAM_CHAT_ID` only in Vercel Environment Variables. Never commit them to GitHub.
