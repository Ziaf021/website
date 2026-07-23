# Rendering & publishing this website — checklist

This is a **Quarto** website whose pages execute **R** code, so it must be built on
your own machine (Quarto + R). The steps below take you from a fresh checkout to a
published site.

## 1. One-time setup

- [ ] Install **Quarto** (latest): <https://quarto.org/docs/get-started/>
      Verify: `quarto --version`
- [ ] Install **R** (≥ 4.2): <https://cran.r-project.org/>
- [ ] (Optional but recommended) Install **RStudio**.
- [ ] Open a terminal in this folder, or open `ZF_lWebpage.Rproj` in RStudio.

## 2. Restore the R packages

This project pins its packages with **renv** (`renv.lock`). Restore them once:

```r
# In R, from the project folder
install.packages("renv")   # if not already installed
renv::restore()            # installs the exact package versions in renv.lock
```

- [ ] `renv::restore()` completes without errors.

## 3. Preview while you work

```bash
quarto preview
```

- [ ] A local site opens in your browser and live-reloads on save.
- [ ] Check the **homepage hero**, the **berry navbar/buttons**, and that the
      **CV PDF** loads on the CV page.

## 4. Build the site

```bash
quarto render
```

- [ ] Build finishes with no errors; output lands in the `_site/` folder.
- [ ] Spot-check `_site/index.html`, `_site/ResearchProjects.html`,
      `_site/Resume.html` locally.

## 5. Publish

Publish to Quarto Pub (matches your existing `_publish.yml`):

```bash
quarto publish quarto-pub
```

- [ ] Confirm the target account/site when prompted.

## Custom domain (ziafarooq.org)

**Quarto Pub does not support custom domains.** A `quarto.pub` site will always
live at a `…quarto.pub/…` address. To serve the site at **ziafarooq.org**, publish
to a host that supports custom domains — GitHub Pages or Netlify (Netlify is what
sites like emitanaka.org use). A `CNAME` file containing `ziafarooq.org` is already
in the project root for the GitHub Pages route.

**Option A — GitHub Pages (free):**

1. Create a GitHub repository and push this project to it.
2. Run `quarto publish gh-pages`.
3. In the repo's **Settings → Pages**, set the custom domain to `ziafarooq.org`
   (the `CNAME` file is published automatically).
4. At your domain registrar, add DNS records pointing `ziafarooq.org` to GitHub
   Pages (an `ALIAS`/`A` record to GitHub's IPs, and a `CNAME` for `www`). See
   <https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site>.

**Option B — Netlify (free, easiest domains):**

1. Run `quarto render`, then drag the `_site/` folder into <https://app.netlify.com/drop>
   (or connect the GitHub repo for automatic builds).
2. In Netlify → **Domain settings**, add `ziafarooq.org` and follow the DNS
   instructions. See <https://quarto.org/docs/publishing/netlify.html>.

DNS changes can take a few hours to propagate.

## Troubleshooting

- **A package is missing / render stops on `library(...)`** → run
  `renv::restore()` again, or `renv::install("<pkg>")` then `renv::snapshot()`.
- **CV PDF doesn't appear** → confirm `Zia-Farooq_CV20260202.pdf` is in the project
  root (it is declared under `resources:` in `Resume.qmd`).
- **Navbar/buttons aren't berry** → ensure `brand.scss` is present and that
  `_quarto.yml` lists `theme: [lumen, brand.scss]`.
- **GitHub contribution calendar is blank on the About page** → it loads a remote
  script; it only renders when the page is served (e.g. via `quarto preview`) and
  online, not from a raw local file.
- **Force a clean rebuild** → delete the `_site/` and `.quarto/` folders, then
  `quarto render`.
