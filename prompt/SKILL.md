---
name: "daily-tech-news"
description: "Daily global tech news digest as a newspaper-style HTML page (AI, disruptive tech, vendor releases, M&A). Use for tech news, AI news, the daily digest, or any work in the Daily Tech Dose folder."
---

# Daily Tech News Digest

Produce a source-linked, newspaper-style page of the most important global tech news from the last 24 hours. Each story shows a headline and a short crux; clicking it expands a one-page-read detail with the industry impact.

## Home folder
All work for this skill lives in the user's **Daily Tech Dose** folder (`/Users/Bejoy Jacob/Claude Projects/Daily Tech Dose`). Whenever a task touches that folder, follow this skill. Existing files there:
- `YYYY-MM-DD-tech-news.html` - one dated edition per day.
- `daily-tech-dose-artifact-source.html` - the same page with a "Fetch Latest News" button and `<!--CONTENT START-->` / `<!--CONTENT END-->` markers around the stories. When updating it, replace only what sits between those markers (plus the date in `<title>` and the masthead), keeping the button, its CSS and script intact.
- Before building, check the newest dated file to find the last digest date (see Workflow step 1) and to match its structure.

## Scope
1. AI innovations (models, agents, research, chips, regulation)
2. Emerging and disruptive tech (quantum, robotics, semiconductors, energy-tech, autonomy)
3. Vendor releases and announcements (Salesforce, ServiceNow, Workday, SAP, Oracle, Microsoft, Google, AWS, Apple, Meta, OpenAI, Anthropic, Nvidia, xAI, Mistral, cybersecurity and data vendors)
4. Mergers, acquisitions, major funding and IPOs

## Workflow
1. Set the window: from the last digest's date to today (default last 24h if there is none), but never more than the last 5 days.
2. Run parallel web searches per scope area and per vendor, with global angles (Asia, Europe, India, Middle East). Include month/year in queries.
3. Verify with primary sources and reputable outlets; label unconfirmed items "Rumor" or "Reported". Confirm dates fall in the window.
4. Select the top 10-15 items by industry impact; skip empty categories.
5. Build the HTML page (below), save as `YYYY-MM-DD-tech-news.html` in the Daily Tech Dose folder, update `daily-tech-dose-artifact-source.html` with the same content, present the page, and give a 2-3 line chat summary.

## Page design (strict)
Simple, traditional newspaper layout. Black text on a light white background, matching the Claude desktop UI. No colors, gradients, images, or emojis.

- **Masthead**: centered serif title "Daily Tech Dose", date and coverage window beneath, thin black rules above and below.
- **Layout**: a lead story at the top (larger headline), then stories in a 2-3 column grid on desktop (single column on mobile), grouped under small-caps section headings: AI Innovations, Emerging & Disruptive Tech, Vendor Releases, Mergers & Acquisitions, Watch List. Thin black rules between sections and stories.
- **Collapsed story**: bold serif headline, small gray-free uppercase meta line (source, date), and a 2-3 line crux.
- **Expanded story** (click headline or card to toggle; use `<details>/<summary>` so it works without JS): a one-page read of about 120-200 words with what happened, key facts and figures, and a labeled **Impact on the tech industry** paragraph that is specific (who is affected, which markets or vendors, what to watch). End with a "Read source" link.
- **Type**: serif (Georgia, "Times New Roman") for headlines and body; system sans-serif only for small meta labels. Body 16-17px, line-height 1.5, max width about 1100px, generous whitespace.
- **Colors**: text `#1a1a1a` or black, background `#faf9f5` (light warm white), rules `#1a1a1a`. Nothing else.
- Everything in one self-contained HTML file with inline CSS; no external assets.

### Skeleton
```html
<body>
<header class="masthead"><h1>Daily Tech Dose</h1><p>Wednesday, October 21, 2026 · Coverage: last 24 hours</p></header>
<section><h2>AI Innovations</h2>
 <div class="grid">
  <article><details><summary><h3>Headline</h3><p class="meta">Source · Date</p><p class="crux">Two-three line crux.</p></summary>
   <div class="detail"><p>Expanded one-page read.</p><p><strong>Impact on the tech industry:</strong> ...</p><p><a href="URL">Read source</a></p></div>
  </details></article>
 </div>
</section>
</body>
```
CSS essentials: `body{background:#faf9f5;color:#1a1a1a;font-family:Georgia,serif}`, `summary{cursor:pointer;list-style:none}`, `.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(300px,1fr));gap:24px}`, `h2{font-variant:small-caps;border-top:2px solid #1a1a1a;border-bottom:1px solid #1a1a1a}`.

## Rules
Every item has a working source link and date. Never invent facts, figures, or quotes. Keep the crux to 2-3 lines and each expanded read to one screen. Paraphrase, don't copy article text. If a category has no real news, omit it.