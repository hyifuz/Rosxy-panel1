# Telegram Alert Configuration

Do **not** put the Telegram bot token in `index.html`, JavaScript shipped to the browser, GitHub, or this ZIP.

In Vercel → Project → Settings → Environment Variables, create:

```text
TELEGRAM_BOT_TOKEN=<your_bot_token>
TELEGRAM_CHAT_ID=<your_chat_id>
```

The values are read only by Vercel server-side functions.

The supplied bot token was pasted into chat, so for production security you should rotate/revoke that token with BotFather and use the newly generated token as the Vercel environment variable.

`/api/telegram-config` only reports whether the values are configured; it never returns the token.
