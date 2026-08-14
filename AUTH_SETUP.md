# Advanced Rosxy Panel Authentication

Set these Vercel Environment Variables:

```text
PANEL_PASSWORD=<strong-unique-password>
PANEL_SESSION_SECRET=<random-32+-character-secret>
```

Recommended: generate the session secret locally:

```bash
python -c "import secrets; print(secrets.token_urlsafe(48))"
```

The password is never embedded in `index.html`. The server checks it inside the Vercel function and issues an HttpOnly, Secure, SameSite=Strict session cookie.

Endpoints:

- `POST /api/auth-login`
- `GET /api/auth-me`
- `GET /api/auth-logout`

For stronger production protection, put Vercel Deployment Protection/SSO in front of the project as an additional layer.
