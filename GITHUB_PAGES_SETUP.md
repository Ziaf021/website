# Publishing to ziafarooq.org via GitHub Pages

This is the recommended way to serve your Quarto site at **ziafarooq.org** (Quarto
Pub cannot use custom domains). A `CNAME` file containing `ziafarooq.org` is already
in the project root, so GitHub Pages will pick up the domain automatically.

You only do steps 1–2 once. After that, publishing an update is a single command.

## Prerequisites

- [ ] A free **GitHub account** — <https://github.com/join>
- [ ] **git** installed — `git --version` (macOS: `xcode-select --install`)
- [ ] Quarto + R working locally (you already render successfully)

## 1. Put the project on GitHub

From a terminal in this folder:

```bash
git init                      # if not already a git repo
git add .
git commit -m "Personal website"
```

Create a new **empty** repository on GitHub (no README), e.g. named `website`, then:

```bash
git branch -M main
git remote add origin https://github.com/Ziaf021/website.git
git push -u origin main
```

- [ ] Repository pushed to GitHub.

> Note: `.RData`, `.Rhistory`, and large data can be excluded via `.gitignore`
> (you already have one). Keep the large thesis PDFs out of git if the push is slow.

## 2. Publish with Quarto

```bash
quarto publish gh-pages
```

This renders the site and pushes it to a `gh-pages` branch, then enables Pages.
Confirm the prompts. When it finishes it prints your `…github.io` URL.

- [ ] Site is live at `https://ziaf021.github.io/website/`.

## 3. Point ziafarooq.org at GitHub Pages

**In the GitHub repo:** Settings → Pages → "Custom domain" → enter `ziafarooq.org`
→ Save. Tick **Enforce HTTPS** once it becomes available.

**At your domain registrar** (where you bought ziafarooq.org), add these DNS records:

| Type  | Host / Name | Value |
|-------|-------------|-------|
| A     | @           | 185.199.108.153 |
| A     | @           | 185.199.109.153 |
| A     | @           | 185.199.110.153 |
| A     | @           | 185.199.111.153 |
| AAAA  | @           | 2606:50c0:8000::153 |
| AAAA  | @           | 2606:50c0:8001::153 |
| AAAA  | @           | 2606:50c0:8002::153 |
| AAAA  | @           | 2606:50c0:8003::153 |
| CNAME | www         | ziaf021.github.io. |

- [ ] Custom domain set in Settings → Pages.
- [ ] DNS records added at the registrar.
- [ ] Waited for propagation (minutes to a few hours) and confirmed
      <https://ziafarooq.org> loads with a valid certificate.

## Publishing future updates

Once set up, every update is just:

```bash
quarto publish gh-pages
```

(Optionally `git add . && git commit -m "update" && git push` to keep `main` in sync.)

---

### Alternative — Netlify (simplest, no git required)

1. `quarto render`
2. Drag the `_site/` folder onto <https://app.netlify.com/drop>.
3. Netlify → Domain settings → add `ziafarooq.org` and follow its DNS instructions.

Netlify is the easiest for drag-and-drop, but GitHub Pages keeps everything in one
versioned repo, which is the more common setup for academic sites.
