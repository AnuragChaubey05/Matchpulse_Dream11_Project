# Why Did That Just Happen?

Tap any moment from a real cricket match (NZ vs India, 1st ODI, 4 Nov 2026) and get the rule in plain English or Hinglish, plus what it meant for your fantasy team. Ask your own questions with live AI (Google Gemini).

## Files

- `index.html`: the whole app (no build step)
- `api/explain.js`: small server function that calls Gemini. Your API key stays here, never in the page.

## Deploy (about 10 minutes)

### 1. Get a free Gemini key
1. Go to https://aistudio.google.com/apikey and sign in with Google.
2. Click **Create API key** and copy it.

### 2. Put the code on GitHub
1. Create a new repository on github.com (for example `why-did-that-just-happen`).
2. Click **uploading an existing file**, drag in everything from this folder (`index.html`, `api` folder, `package.json`, `README.md`, `.gitignore`), and click **Commit changes**.

### 3. Deploy on Vercel (free)
1. Go to https://vercel.com and sign in with GitHub.
2. Click **Add New → Project**, pick your repository, and click **Deploy**.
3. Open the project, go to **Settings → Environment Variables**, and add:
   - `GEMINI_API_KEY` = your key
   - (optional) `GEMINI_MODEL` = a model name from https://aistudio.google.com if the default stops working. The default is `gemini-2.5-flash`.
4. Go to **Deployments**, open the latest one, and choose **Redeploy** so it picks up the key.
5. Open your Vercel link. Click a moment, then press the AI button. The first question box answer should now be written live.

If the key is missing or the server can't be reached, the page still works and shows prepared answers.

## Notes

- GitHub Pages alone cannot run live AI because it has no server. Use Vercel (it deploys from the same GitHub repo).
- Never paste your API key into `index.html` or commit it to GitHub.
- The server function caps prompt size, answer length and requests per visitor. These limits are best-effort.
- Match details come from a sports data feed and live match blogs. Check the official scorecard before quoting numbers.
