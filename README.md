# Amit Kumar — Wiki-Style SEO Profile Build

This package is a standalone, self-hosted **Wikipedia-style biography page**
for Amit Kumar, built with full on-page SEO. It's meant to be uploaded to a
site you control (GitHub Pages, Vercel, Netlify, your own domain, etc.) so
it can get indexed by Google and other search engines under your name.

## What's in the folder

| File | Purpose |
|---|---|
| `index.html` | The actual wiki-style article page — content, layout, and every SEO tag |
| `sitemap.xml` | Tells search engines which pages exist and how important/fresh they are |
| `robots.txt` | Tells crawlers they're allowed to index the site and where the sitemap lives |
| `README.md` | This file |

## SEO elements built into `index.html`, and why each one matters

**Title tag & meta description**
The `<title>` and `<meta name="description">` are what actually show up as
the blue link and the snippet text in Google search results. Both are
written to include the name, the "known for" projects, and role keywords
(MLOps Engineer, kernel developer) so the page ranks for searches combining
those terms.

**Meta keywords / author / robots**
Secondary signals. `robots` explicitly tells crawlers to index the page and
follow its links, with large image previews and unlimited snippet length
allowed.

**Canonical tag**
`<link rel="canonical">` prevents duplicate-content issues if the same page
ever gets copied, mirrored, or served from multiple URLs — it tells search
engines which URL is the "real" one to rank.

**Open Graph tags (`og:*`)**
Control how the page looks when shared on LinkedIn, Facebook, WhatsApp, or
Slack — title, description, and a preview image (1200×630, replace the
placeholder path with a real image once you have one).

**Twitter Card tags**
Same idea as Open Graph, but for X/Twitter's card renderer.

**JSON-LD structured data (schema.org `Person` + `ProfilePage`)**
This is the most important technical piece. It's a machine-readable block
describing who Amit is, his affiliation, location, skills (`knowsAbout`),
and `sameAs` links to his GitHub/LinkedIn/portfolio. This is what lets
Google understand "Amit Kumar" as a distinct entity and connect his profiles
together, which is a prerequisite for richer search results and for the
name to surface correctly in Knowledge Graph–style lookups over time.

**Semantic HTML5 structure**
`<header>`, `<main>`, `<article>`-style sectioning, one `<h1>`, and a clean
`<h2>`/`<h3>` hierarchy for every section (Biography, Education, Projects,
Research, etc.). Search engines weight headings heavily when figuring out
what a page is "about" — this structure makes the topic map obvious.

**Internal table of contents with anchor links**
Every section has an `id`, and the TOC links to them (`#mykernel`,
`#threatvision-ai`, etc.). This mirrors how real Wikipedia articles are
structured, improves on-page navigation (a positive UX/SEO signal), and can
produce sitelinks-style jump-to-section results in Google.

**Descriptive, keyword-rich body copy**
Every project, skill, and publication is described in full sentences (not
just bullet fragments), so the page has genuine indexable text around each
keyword rather than being a bare list — this is what search engines need to
associate the page with long-tail queries like "MyKernel 64-bit x86_64
kernel creator" or "hybrid face recognition QR attendance system paper."

**References & External Links sections**
Wikipedia-style citation list plus outbound links to the real GitHub,
LinkedIn, and portfolio — this both matches the "wiki" format you asked for
and reinforces entity relationships between this page and Amit's other
profiles (helps with `sameAs` disambiguation above).

**Accessibility touches that double as SEO signals**
A skip-to-content link, `alt`-ready image placeholder, visible focus states
via native semantics, and a single clear `<h1>` — accessible pages tend to
rank better because they're easier for crawlers to parse the same way
they're easier for screen readers to parse.

## What you need to do before publishing

1. **Replace placeholder URLs.** Every `https://amit123103.github.io/SmartPortfolio/...`
   URL (in the meta tags, JSON-LD, sitemap, and robots.txt) should be
   swapped for wherever you actually host this file, if different.
2. **Add a real profile photo** at `assets/profile.jpg` and a real
   1200×630 share image at `assets/og-cover.png`, then update the `<meta
   property="og:image">`, `<meta name="twitter:image">`, and JSON-LD
   `image` fields to point to them.
3. **Submit the sitemap to Google Search Console** (and Bing Webmaster
   Tools) once the page is live, pointing at `sitemap.xml`.
4. **Get a few real backlinks** — link to this page from the GitHub profile
   README, the LinkedIn "Featured" section, and the existing SmartPortfolio
   site. Inbound links are still one of the strongest ranking signals for a
   personal-name page.
5. **Keep `dateModified` in the JSON-LD current** whenever you update the
   content, so search engines know the page is actively maintained.

## Validating the build

- Run the HTML through Google's [Rich Results Test](https://search.google.com/test/rich-results)
  to confirm the JSON-LD `Person` markup parses cleanly.
- Run [PageSpeed Insights](https://pagespeed.web.dev/) once it's hosted —
  the page is a single static file with no render-blocking scripts, so it
  should score well by default.
- Check `sitemap.xml` loads correctly at `<your-domain>/sitemap.xml` and
  that `robots.txt` correctly references it.
