# Rosxy Panel Health Endpoint

The package now includes `server.py`.

Run:

```bash
python server.py
```

Then check:

```text
GET /health
GET /api/health
```

Successful response:

```json
{"status":"ok","service":"rosxy-panel","version":"2.4","uptime_seconds":12.34,"timestamp":1234567890}
```

The endpoint is intentionally lightweight and does not expose secrets, Firebase credentials, bot tokens, or user data.

For Telegram monitoring, run the monitor on a separate machine/process so it can still alert you if the panel server stops.
