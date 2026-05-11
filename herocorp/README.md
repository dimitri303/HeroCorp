# HeroCorp Help Center — Demo Site

Static help center built specifically to be ingested by Zendesk's AI agent during your demo.

## Deploy to GitHub Pages (5 min)

1. Create a new GitHub repo (e.g. `herocorp-support`).
2. Drop all these files into the repo root.
3. Push.
4. **Settings → Pages** → Source: `Deploy from branch`, branch: `main`, folder: `/ (root)`.
5. Your URL: `https://<username>.github.io/<repo-name>/`

Paste that URL into Zendesk's AI agent setup screen.

## What's in here

- `index.html` — Help center landing page with 15 articles in 3 categories
- `styles.css` — Minimal stylesheet
- `articles/` — 15 individual help articles

## Critical: do this 48 hours before the panel

1. Deploy to GitHub Pages
2. Paste the URL into Zendesk's AI agent setup
3. Wait for ingestion to complete
4. Test by asking the agent: "my gems didn't arrive", "how do I set up 2FA", "what's your refund policy"
5. Confirm it pulls clean answers with the right citations

## The hero article

`articles/missing-gems.html` is written for the demo scenario in your prep doc — the player who bought 5,000 gems for a time-limited event. The agent should be able to answer that question entirely from this article.
