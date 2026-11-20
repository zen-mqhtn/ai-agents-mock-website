# Mock website for Zendesk AI agent demos

A fictional **"Acme Intranet"** (5 pages) that you can connect as a **web crawler knowledge source** for **Employee Service (ES) and CX AI agents**. You don't need admin rights on any real system, and you don't need scripts: GitHub Pages hosts it for free and **generates the sitemap automatically**.

> All content is fictional. Keep it that way: this repo and its website are public.

---

## Setup (about 2 minutes)

1. Click **Use this template → Create a new repository** (top right on this page).
   - Owner: your **personal** GitHub account
   - Name: e.g. `acme-intranet`
   - Visibility: **Public** (free GitHub Pages only works for public repos)
2. In your new repo: **Settings → Pages → Build and deployment**
   - Source: **Deploy from a branch**
   - Branch: **main**, folder **/ (root)** → **Save**
3. Wait 1–2 minutes (the build shows under the **Actions** tab), then open:
   - Website: `https://<your-github-user>.github.io/<repo>/`
   - Sitemap: `https://<your-github-user>.github.io/<repo>/sitemap.xml` (shows **5 URLs**)

That's it. The sitemap and `robots.txt` are generated with the right URLs for your repo.

---

## Connect it in Zendesk

Use the **sitemap URL** in both cases.

### ES AI agents
1. Admin Center → **AI → AI agents → Sources → Add source → Web crawler → Connect**.
2. Name: `Acme Intranet`, URL: your sitemap URL, **No authentication** → **Save**.
3. Open your ES AI agent → **Sources → Add source** → Web crawler → *Acme Intranet* → **Save**.
4. The crawler syncs **every 6 hours**. If you see 0 items, wait for the next sync before troubleshooting.

### CX AI agents
1. Knowledge admin → **Settings → Search settings → Crawlers → Manage → Add Crawler**.
2. Name: `Acme Intranet`, URL: your sitemap URL → **Sync**.
3. Use the crawled content as a knowledge source in your AI agent. See the Help Center article *"Connecting knowledge sources to power generative replies in AI agents"*.

---

## Edit content

- **Change a page:** open the `.html` file on GitHub → pencil icon → edit → **Commit changes**. The site updates within 1–2 minutes.
- **Add a page:**
  1. Copy `_template.html` and give it a name **without** the underscore (e.g. `expenses-faq.html`).
  2. Replace the `PLACEHOLDER` texts.
  3. Link the page from `index.html` (a card and a sidebar link).
  4. The sitemap picks it up automatically.
- **For CX demos:** replace the pages with customer-facing ones (FAQ, shipping, returns, warranty), and change the header text `ACME Intranet` on each page.

**Tip for demos:** give every fact a distinctive value and put it on **one** page only. Then you can see at a glance which source the AI agent cited, and anything made up stands out.

---

## What's on the pages (for writing demo questions)

| Page | Key facts |
|---|---|
| `hr-notifying-hr-about-parental-leave.html` | Notify HR **at least 15 weeks** before the due date. HR Business Partner contacts you **within 5 business days**. Return-to-work conversation **4 weeks** before return. |
| `working-hours-and-core-time.html` | Core hours **10:00–15:00**, flexible window **07:00–20:00**, max **10 hours/day**, breaks 30/45 min, no meetings on **Friday after 13:00** |
| `office-locations.html` | Offices in Berlin (HQ), Amsterdam, London, Austin. Reception **Mon–Fri 08:00–18:00**. Badges at reception. |
| `it-onboarding.html` | Day 1 checklist (laptop, MFA, password manager, VPN). Slack channels `#it-help`, `#it-security` |
| `index.html` | Start page with links to all pages |

Example question: *"I'm expecting a baby. When do I have to tell HR, and what are the core working hours?"* (Answer: 15 weeks before the due date; 10:00–15:00.)

---

## Rules (or the crawler won't work)

| Don't | Why |
|---|---|
| Add `sitemap.xml`, `robots.txt` or `.nojekyll` | Any of them switches off the automatic generation |
| Make the repo private | Free GitHub Pages and the crawler need a public site |
| Host the pages through ngrok or on your laptop | The crawler fetches pages as a headless browser and gets ngrok's warning page instead of your content (0 items). A laptop is also offline for many of the 6-hourly syncs. |
| Use real company or customer data | The website is public |

---

## Files

| File | Purpose |
|---|---|
| `_config.yml` | Turns on the automatic sitemap (`jekyll-sitemap`). Keeps `README.md` off the website. |
| `*.html`, `intranet.css` | The website |
| `_template.html` | Starter page for new pages (not published) |
