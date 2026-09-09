 Telegram Reward Bot — Vercel + Firestore

## Files
- `api/telegram.js` — webhook backend
- `public/userpanel.html` — Telegram Mini App
- `public/adminpanel.html` — admin UI
- `vercel.json` — Vercel routing

## Setup
1. Create a Firebase project and Firestore database.
2. Put the Firebase web config into both HTML files.
3. Set `BOT_TOKEN`, `WEBAPP_URL`, and Firebase config environment variables in Vercel.
4. Replace `YOUR_BOT_USERNAME` in `public/userpanel.html`.
5. Deploy to Vercel.
6. Set the Telegram webhook to `https://YOUR-DOMAIN/api/telegram`.
7. Set your bot's menu/web-app URL to the deployed `userpanel.html`.

### Vercel environment variables
`BOT_TOKEN`
`WEBAPP_URL`
`FIREBASE_API_KEY`
`FIREBASE_AUTH_DOMAIN`
`FIREBASE_PROJECT_ID`
`FIREBASE_STORAGE_BUCKET`
`FIREBASE_MESSAGING_SENDER_ID`
`FIREBASE_APP_ID`

## Important security note
The supplied specification explicitly uses the Firebase client SDK and a hard-coded admin key. That is not sufficient authentication for a production financial/reward system. Before real use, enforce Firestore Security Rules and server-side admin authentication, and validate Telegram WebApp init data server-side. The included admin key is a placeholder only.

## Firestore indexes
The user panel may need a composite index for `withdrawals` (`userId` + `createdAt`). Firebase will provide a link to create it when required.
