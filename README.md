# Matchpulse: "Why did that just happen?"

A live-match explainer for casual cricket fans. Tap a moment from a match, or type a question, and get a short plain-English (or Hinglish) explanation plus what it meant for your fantasy team.

**Live demo:** https://matchpulsedream11project.vercel.app/

## The problem

Casual fans hit moments they don't understand during a match: a DLS target, a run out, a free hit, a sudden bowling change. They either ignore it or leave the app to Google it. Matchpulse explains the moment in 2-3 lines and links it to fantasy impact, so the fan stays in the match.

## Features

- Timeline of key moments from one match (1st ODI, NZ v India, 4 Nov 2026)
- English / Hinglish toggle
- Ask your own question, answered live by Google Gemini
- Pick your fantasy captain and see how each moment affected them
- Prepared answers show up if the AI is unavailable or rate-limited

## How it works

- `index.html`: the whole front end, plain HTML/CSS/JS, no build step
- `api/explain.js`: a Vercel serverless function that calls the Gemini API
- The API key is stored only as a Vercel environment variable (`GEMINI_API_KEY`) and never reaches the browser
- The function limits prompt size, answer length and requests per visitor, and the system prompt restricts answers to cricket

## Run it yourself

1. Get a free key at https://aistudio.google.com/apikey
2. Import this repo into Vercel
3. Add `GEMINI_API_KEY` under Settings > Environment Variables (optional: `GEMINI_MODEL` to pick the model; backups are tried if it is busy)
4. Redeploy

## Limitations

- Match data is hardcoded sample data, not a live feed. Check official scorecards before relying on any number
- The rate limiter is in memory, so it is a soft limit
- AI answers can be wrong; they are limited to the match facts in the prompt

## Built with

Google Gemini API (live explanations), Claude (AI coding assistant), Vercel, vanilla JavaScript
