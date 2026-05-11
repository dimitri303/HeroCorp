# HeroCorp Help Center — Zendesk-Style Hierarchy

Built to mirror Zendesk's own help center structure so their AI agent crawler recognises the content hierarchy correctly.

## Structure

The site follows Zendesk's exact URL convention: **Home → Category → Section → Article**.

```
/                                                  → redirects to /hc/en-us/
/hc/en-us/                                         → Help center home
/hc/en-us/categories/account-and-security/         → Category page
/hc/en-us/sections/signing-in/                     → Section page
/hc/en-us/articles/missing-gems/                   → Article page
/sitemap.xml                                       → Lists all 26 URLs for the crawler
/robots.txt                                        → Allows Zendesk's crawler explicitly
```

**3 categories → 7 sections → 15 articles.**

## Crawler-friendly signals included

Every page has:
- `<html lang="en-us">` — for Zendesk's locale detection
- `<meta http-equiv="Content-Language" content="en-us">` — backup locale signal
- `<title>` tag — Zendesk crawler primary title source
- `<meta name="description">` — for snippet rendering
- Breadcrumbs linking up the hierarchy
- Semantic HTML (`<h1>`, `<h2>`, `<ol>`, `<ul>`)

Plus:
- `sitemap.xml` listing all 26 URLs
- `robots.txt` explicitly allowing `Zendesk/External-Content` user agent

## Deploy

1. **Wipe your current HeroCorp repo** (delete the old files), or create a fresh repo.
2. Drop all files from this zip into the repo root.
3. Push.
4. GitHub Pages should automatically serve from `/`.
5. Verify the live URL works: **https://dimitri303.github.io/HeroCorp/hc/en-us/**

Click around — categories → sections → articles. Confirm breadcrumbs and links work.

## In Zendesk

Try the web crawler again with this **Start URL**:

```
https://dimitri303.github.io/HeroCorp/hc/en-us/
```

This time the crawler will see:
- A proper help-center-shaped hierarchy it recognises
- A sitemap.xml at the root telling it exactly which pages to index
- All 15 articles linked via category and section pages (so the crawl will reach them)
- Clean HTML with no nav junk, footer cruft, or marketing content to filter out

You may also want to set **Maximum crawling depth** to 4 (Home → Category → Section → Article = depth 4) if Zendesk asks.

## What the AI agent should be able to answer

After ingestion, test these:
- "I bought 5,000 gems but they have not arrived and the event ends in 2 hours" → **missing-gems**
- "How do I set up 2FA?" → **two-factor-authentication**
- "What is your refund policy?" → **refund-policy**
- "My controller is not working on PC" → **controller-setup**
- "Someone hacked my account" → **account-recovery**
- "How do I get into the Sundered Spire beta?" → **closed-beta-access**

If the AI agent cites the article and links back to the right `/hc/en-us/articles/{slug}/` URL, you are set for the demo.

## Backup plan

If the web crawler still struggles (sometimes it just does on free trial tiers), the CSV I made earlier (`herocorp-knowledge.csv`) imports directly without any crawler needed. Same content, different ingestion path.
