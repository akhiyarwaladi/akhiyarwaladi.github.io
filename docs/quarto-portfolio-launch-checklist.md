# Quarto Academic Portfolio, Build & Launch Checklist

Use this together with `quarto_portfolio_master_guide.md`.

## A. Before building

- [ ] Confirm GitHub username.
- [ ] Prepare professional headshot.
- [ ] Prepare short homepage biography.
- [ ] Prepare longer About biography.
- [ ] Prepare CV PDF.
- [ ] Collect ORCID, Google Scholar, GitHub, and professional contact links.
- [ ] Select 3-5 representative publications.
- [ ] Select 2-4 research themes.
- [ ] List courses to publish.
- [ ] Select 2-4 representative projects.

## B. GitHub repository

- [ ] Create `<username>.github.io`.
- [ ] Use **Public** visibility when using GitHub Free.
- [ ] Do not commit secrets or private student/internal data.
- [ ] Prepare the matching local project directory.

## C. Quarto project

```bash
quarto create project website <username>.github.io
cd <username>.github.io
git init
git branch -M main
git remote add origin https://github.com/<username>/<username>.github.io.git
quarto preview
```

- [ ] `index.qmd` created.
- [ ] `_quarto.yml` created.
- [ ] `about.qmd` created.
- [ ] Research page created.
- [ ] Publications section created.
- [ ] Teaching section created.
- [ ] Projects section created.
- [ ] Contact page created.

## D. Quality configuration

- [ ] Navbar has no more than necessary top-level items.
- [ ] Site search enabled.
- [ ] Favicon added.
- [ ] `site-url` configured.
- [ ] Open Graph enabled.
- [ ] Default social preview image added.
- [ ] Light/dark theme tested if enabled.
- [ ] Images have useful alt text.
- [ ] Mobile layout checked.
- [ ] CV link works.
- [ ] DOI/publication links work.
- [ ] Teaching downloads work.

## E. Git

Recommended `.gitignore`:

```gitignore
/.quarto/
/_site/
```

Then:

```bash
git status
git add .
git commit -m "Initial Quarto academic portfolio"
git branch -M main
git push -u origin main
```

## F. First GitHub Pages publish

```bash
quarto publish gh-pages
```

For a root user site (`<username>.github.io`):

- [ ] Open repository **Settings -> Pages**.
- [ ] Confirm publishing source is the `gh-pages` branch.
- [ ] Confirm root folder is selected.
- [ ] Open `https://<username>.github.io`.
- [ ] Enable HTTPS if the option is shown.

Official guide: https://quarto.org/docs/publishing/github-pages.html

## G. Verify live website

- [ ] Home page loads.
- [ ] All navbar links load.
- [ ] Headshot loads.
- [ ] Publications load.
- [ ] Teaching pages load.
- [ ] Project images load.
- [ ] Search works.
- [ ] Social/professional links work.
- [ ] No development/local paths appear.
- [ ] Test desktop.
- [ ] Test mobile.
- [ ] Test one second browser.

## H. Optional auto-deploy

After manual publishing works:

- [ ] Create `.github/workflows/publish.yml`.
- [ ] Use official Quarto GitHub Action.
- [ ] Enable repository Actions workflow **Read and write permissions**.
- [ ] Push a small test change to `main`.
- [ ] Confirm workflow completes successfully.
- [ ] Confirm live site updates.

Official reference: https://quarto.org/docs/publishing/github-pages.html#github-action

## I. Later improvements

- [ ] Custom SCSS.
- [ ] `_brand.yml`.
- [ ] Publication listing automation.
- [ ] Course-specific sidebars.
- [ ] Convert large modules into Quarto Books.
- [ ] Analytics if useful.
- [ ] Custom domain only after `github.io` version is stable.

## J. Useful live references

- Quarto Gallery, https://quarto.org/docs/gallery/
- Beatriz Milz, https://beamilz.com/
- Mike Mahoney, https://www.mm218.dev/
- Hamel Husain, https://hamel.dev/
- Andrew Heiss Teaching, https://www.andrewheiss.com/teaching/
- Python for Data Science, https://pythonds.linogaliana.fr/
- Official personal-website workshop, https://opensource.posit.co/blog/2024-12-04_websites-workshop/
