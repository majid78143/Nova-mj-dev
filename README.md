# Nova Arena

Mobile-first Discord community hub starter with a custom homepage, live-chat surface, giveaways, weekly leaderboard preview, roles/badges, developer profile, and profile-ring previews.

## Current source

- `src/` contains the responsive React/Vite web client.
- The shared API server exposes the starter community, chat, and giveaway contracts under `/api`.
- `lib/api-spec/openapi.yaml` is the API contract source of truth.
- `.env.example` lists the values needed to connect Firebase, Discord OAuth, the Discord bot, owner/developer identities, admin login, and push notifications.

## Environment values

### Browser-safe Firebase values

These are used by the web client and may use the `VITE_` prefix:

- `VITE_FIREBASE_API_KEY`
- `VITE_FIREBASE_AUTH_DOMAIN`
- `VITE_FIREBASE_PROJECT_ID`
- `VITE_FIREBASE_STORAGE_BUCKET`
- `VITE_FIREBASE_MESSAGING_SENDER_ID`
- `VITE_FIREBASE_APP_ID`
- `VITE_FIREBASE_VAPID_KEY`

### Server-only values

Never put these in browser code:

- `DISCORD_BOT_TOKEN`
- `DISCORD_CLIENT_ID`
- `DISCORD_CLIENT_SECRET`
- `DISCORD_GUILD_ID`
- `OWNER_DISCORD_ID`
- `DEVELOPER_DISCORD_ID`
- `ADMIN_EMAIL`
- `ADMIN_PASSWORD`
- `SESSION_SECRET`
- `FIREBASE_CLIENT_EMAIL`
- `FIREBASE_PRIVATE_KEY`
- `FIREBASE_DATABASE_URL`

`GIVEAWAY_TIMEZONE` defaults to `Asia/Kolkata`.

## Integrations still to connect

The UI is ready for the live integration layer, while the included API uses safe in-memory demo data so the preview is immediately usable. Connecting Firebase and Discord requires the user's Firebase project and Discord application credentials. The production integration will use Firestore for durable records, Realtime Database for presence/live events, Discord OAuth2 for website login, and a Discord bot for channel/role/message mirroring.

HTML uploads are intended to be parsed as text, sanitized, and stored as Firestore text records with a generated shareable design URL. Uploaded files should not be persisted as files.