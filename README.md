# Rival AI Mentor — Chatbot App

A simple, zero-dependency chatbot web app that talks to your **Hackathon Rivals API**
AI chat endpoint (the same one used by the "AI Chat (Rival AI Mentor)" request in Postman).

## What it does
- Clean chat UI (user + bot bubbles, typing indicator)
- Sends `POST {baseUrl}/api/ai-chat/ai` with a JSON body:
  ```json
  { "message": "your text", "history": [ { "role": "user", "text": "..." } ] }
  ```
- Expects a JSON response with a `reply` string field.
- Keeps the last few conversation turns as `history` for context (matching the API contract).

## How to run
No build step or install needed — it's a single HTML file.

**Option 1 — open directly:**
Double-click `index.html` to open it in your browser.

**Option 2 — serve it (recommended, avoids CORS quirks):**
```bash
cd chatbot
# Python 3
python -m http.server 5500
```
Then open http://localhost:5500

## Configure the API
Click **⚙ Settings** in the top-right of the app and set:
- **API Base URL** — where your server runs (e.g. `http://localhost:3000`)
- **Endpoint path** — defaults to `/api/ai-chat/ai`

These are saved in your browser's localStorage.

## Notes
- Your server must be running and must have `GROQ_API_KEY` configured (as noted in the
  Postman request documentation).
- If you see a CORS error, make sure your server allows requests from the app's origin,
  or serve the app from the same origin as the API.
