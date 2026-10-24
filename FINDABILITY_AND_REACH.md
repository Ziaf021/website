# Getting found when people search "Zia Farooq"

A brand-new site on a `github.io/website` subpath has almost no authority yet, so
it won't rank for your name overnight. Ranking for a personal name is mostly about
**backlinks from pages that already rank for you** plus **telling Google the site
exists**. Here's the high-impact checklist, roughly in order.

## 1. Tell Google the site exists (do this first)

- [ ] Go to **Google Search Console** → <https://search.google.com/search-console>
- [ ] Add a **URL-prefix property** for `https://ziaf021.github.io/website/`
- [ ] Verify (the easiest method is the HTML-tag: paste the `<meta>` it gives you
      into `_quarto.yml` under `include-in-header`, re-publish, then click Verify —
      I can wire that tag in for you).
- [ ] Submit your sitemap: `https://ziaf021.github.io/website/sitemap.xml`
      (Quarto generates it automatically).
- [ ] Repeat with **Bing Webmaster Tools** → <https://www.bing.com/webmasters>

## 2. Link to the site from pages that already rank for your name

Google associates your name with your site when trusted profiles link to it. Add
`https://ziaf021.github.io/website/` to the "website/homepage" field on:

- [ ] **Google Scholar** (Profile → Edit → Homepage)
- [ ] **ORCID** (Websites & social links)
- [ ] **LinkedIn** (Contact info → Website)
- [ ] **Umeå University staff page** (ask to add a personal-website link)
- [ ] **ResearchGate**
- [ ] **GitHub** profile (bio website field)
- [ ] **X/Twitter** bio (`@DrFarooq_writes`)

These are the single biggest lever for name-search ranking.

## 3. Remove the competing old site

- [ ] Delete the old `faruk-xia.quarto.pub` site (sign in at
      <https://quartopub.com>). Two sites for the same person split your search
      signal and confuse visitors. *(Your CV PDF also still prints that old link —
      worth updating the PDF too.)*

## 4. Get a real domain (biggest branding upgrade)

- [ ] Buy `ziafarooq.org` (or `.com`) from any registrar (~$12/yr) and point it at
      GitHub Pages (I've kept the setup notes in `GITHUB_PAGES_SETUP.md`). A clean
      `ziafarooq.org` is far more memorable and ranks better for your name than a
      github.io subpath.

## 5. Keep feeding it

- [ ] Publish blog posts regularly — fresh, keyword-relevant content (WNV, climate
      & health, R tutorials) is what pulls in search traffic over time.
- [ ] Share each post on LinkedIn and X; your pages already emit rich link previews.

## Already done on the site

- Name-forward `<title>` and meta description, plus `author` and `keywords` tags.
- A sitemap and Open Graph / Twitter cards for clean sharing.
- Google Analytics is wired in, so you can see what's working.

Realistically, expect a few weeks (and the backlinks above) before you rank on
page one for "Zia Farooq". Steps 1–3 are what move the needle fastest.
