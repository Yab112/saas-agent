# Support Agent Backend (NestJS)

## Setup
1. copy `.env.example` to `.env` and fill in keys (DATABASE_URL, GEMINI_API_KEY, SENDGRID_API_KEY).
2. `npm install`
3. Start DB connectivity (Neon is hosted — no local DB needed).
4. `npm run start:dev`

## Endpoints
POST /tickets
- body: { text: string, email: string, source?: string }
- returns: created ticket and analysis (category, sentiment, etc.)

GET /tickets/unresolved
- returns unresolved tickets ordered by priority.

PUT /tickets/:id
- update ticket `status` or `category`.

## Notes
- `GEMINI_API_ENDPOINT` should point to Google Generative API endpoint; see `.env.example`.
- If `USE_QUEUE` is true you must provide `REDIS_URL` and implement QueueModule (I can add this).
