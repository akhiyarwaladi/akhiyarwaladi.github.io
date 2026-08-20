# Master Guide: Building a Lecturer Portfolio Website with Quarto + GitHub Pages

**Last checked:** 19 August 2026  
**Goal:** Build a professional academic portfolio for a lecturer/researcher containing biodata, research, publications, teaching, learning materials/modules, projects, activities, and contact information, then deploy it with GitHub Pages.

---

## 1. Recommended architecture

For the first version, keep the architecture simple:

```text
Quarto source files (.qmd, .yml, .scss/.css)
                 |
                 | git push
                 v
          GitHub repository
      <username>.github.io
                 |
                 | quarto publish gh-pages
                 v
           gh-pages branch
                 |
                 v
            GitHub Pages
                 |
                 v
https://<username>.github.io
```

This is enough for a complete academic website. A database, VPS, WordPress installation, or backend server is not required for the normal portfolio.

### Recommended content model

```text
Home
├── About
├── Research
├── Publications
├── Teaching
│   ├── Courses
│   └── Learning Materials / Modules
├── Projects
├── Students / Supervision
├── Activities / Talks
├── Notes / Blog           (optional)
└── Contact
```

For the first release, prioritize **Home, About, Research, Publications, Teaching, Projects, and Contact**. Add the others after the core site is stable.

---

# 2. Important GitHub Pages visibility rule

## Can the repository be private?

Yes, but it depends on your GitHub plan.

| GitHub plan | Public repository + Pages | Private repository + Pages |
|---|---:|---:|
| GitHub Free (personal) | Yes | **No** |
| GitHub Free (organization) | Yes | **No** |
| GitHub Pro | Yes | Yes |
| GitHub Team | Yes | Yes |
| GitHub Enterprise Cloud | Yes | Yes |

GitHub's current documentation states that GitHub Pages is available from **public repositories on GitHub Free**, while public and private repositories are supported on GitHub Pro, Team, and Enterprise plans.

Official source:  
https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages

### Important distinction: private repository is not the same as private website

Even when the source repository is private, a normal GitHub Pages site is **public on the internet by default**. A truly privately published Pages site with access control requires an organization using GitHub Enterprise Cloud.

Official sources:

- https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
- https://docs.github.com/enterprise-cloud@latest/pages/getting-started-with-github-pages/changing-the-visibility-of-your-github-pages-site

### Recommendation for this portfolio

Use a **public repository on GitHub Free**.

That gives you:

- free GitHub Pages hosting;
- free GitHub Actions for a public repository;
- an easy-to-inspect source history;
- no server administration;
- a natural place to keep the portfolio under version control.

A public academic website should contain only material that is already intended to be public. **Never commit passwords, API keys, unpublished confidential material, student private data, internal documents, or sensitive files.**

If someday you specifically want the website source hidden while the website remains public, GitHub Pro can host Pages from a private source repository.

---

# 3. Repository naming: use a dedicated repository

For a personal root GitHub Pages site, create a repository named exactly:

```text
<github-username>.github.io
```

Example:

```text
akhiyarwaladi.github.io
```

The resulting default address is:

```text
https://akhiyarwaladi.github.io
```

GitHub distinguishes between:

- **User site**: `<username>.github.io` -> `https://<username>.github.io`
- **Project site**: another repository name -> `https://<username>.github.io/<repository-name>/`

Official source:  
https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages

For a permanent lecturer portfolio, the root user site is cleaner.

---

# 4. Live Quarto websites worth studying

Do not copy one site exactly. Instead, borrow the strongest design/content idea from several examples.

## 4.1 Beatriz Milz

**Live site:** https://beamilz.com/

Why it is useful:

- academic/personal identity is immediately clear;
- research, projects, talks, videos, and blog are easy to find;
- multilingual organization demonstrates that a personal site can grow without becoming confusing;
- clearly built with Quarto.

Borrow this idea: **simple landing page + clear content categories + approachable academic identity**.

Official Quarto Gallery entry:  
https://quarto.org/docs/gallery/

---

## 4.2 Mike Mahoney

**Live site:** https://www.mm218.dev/

Why it is useful:

- concise biography;
- selected projects visible immediately;
- publications, presentations, CV, blog, GitHub, and professional links are close to the homepage;
- information hierarchy is strong even without excessive visual effects.

Borrow this idea: **homepage should surface selected work rather than act only as a table of contents**.

---

## 4.3 Hamel Husain

**Live site:** https://hamel.dev/

Why it is useful:

- strong technical writing / teaching emphasis;
- excellent example of using Quarto for a content-heavy professional identity;
- shows that a Quarto site can scale to many long-form technical articles.

Borrow this idea: **make useful technical/teaching content part of the portfolio itself**.

---

## 4.4 Andrew Heiss, Teaching page

**Live teaching page:** https://www.andrewheiss.com/teaching/

Why it is useful:

- courses are grouped by academic year;
- course descriptions are understandable before clicking;
- interactive resources are placed separately from formal courses;
- the page demonstrates how teaching history can remain navigable over many years.

Borrow this idea: **organize teaching resources by course and/or academic year instead of uploading one long file list**.

---

## 4.5 Python for Data Science

**Live site:** https://pythonds.linogaliana.fr/

Why it is useful:

- excellent reference for online teaching modules;
- uses navigable chapters;
- combines explanation, code, notebooks, and learning materials;
- demonstrates the direction the Teaching / Learning Materials section can eventually take.

Borrow this idea: **treat teaching materials as structured learning content, not merely a PDF download page**.

---

## 4.6 Official Quarto Gallery

**Gallery:** https://quarto.org/docs/gallery/

Use this when looking for new ideas. It contains examples of personal websites, blogs, courses, research-group sites, documentation, notebooks, dashboards, and books.

---

# 5. High-quality resources to learn Quarto website design

## Official Quarto website documentation

https://quarto.org/docs/websites/

Covers the overall website project model, navigation, search, footer, tools, and publishing.

## Official four-part Quarto personal website workshop

https://opensource.posit.co/blog/2024-12-04_websites-workshop/

This is especially useful because the sequence is close to the workflow needed here:

1. build the homepage;
2. add pages and navigation;
3. customize appearance with CSS/SCSS;
4. add listings for projects, talks, publications, or posts.

## About-page templates

https://quarto.org/docs/websites/website-about.html

Quarto currently includes built-in about layouts such as:

- `jolla`
- `trestles`
- `solana`
- `marquee`
- `broadside`

For a lecturer/researcher homepage, `solana`, `trestles`, or `broadside` are good starting points.

## Document listings

https://quarto.org/docs/websites/website-listings.html

Use listings for:

- publications;
- projects;
- courses;
- talks;
- blog/notes;
- learning resources.

This avoids manually updating a long index page every time a new item is added.

## Navigation and search

https://quarto.org/docs/websites/website-navigation.html

Quarto supports:

- top navbar;
- sidebar;
- combined navbar + sidebar;
- full-text site search.

For this portfolio, use a top navbar for the main portfolio and a sidebar only for large teaching/module sections.

## HTML themes and custom theming

https://quarto.org/docs/output-formats/html-themes.html

Quarto uses Bootstrap 5 and includes Bootswatch themes. It also supports custom SCSS themes and separate light/dark themes.

## Website tools: social preview, favicon, analytics, dark mode

https://quarto.org/docs/websites/website-tools.html

Important quality features include:

- favicon;
- Open Graph metadata;
- social preview images;
- Twitter/X card metadata;
- Google Analytics or Plausible Analytics;
- cookie consent where needed;
- dark mode.

## Brand system

Quarto supports `_brand.yml` for consistent visual branding across supported outputs.

Background and examples:

- https://quarto.org/docs/blog/posts/2024-11-25-1.6-release/
- https://quarto.org/docs/blog/posts/2025-01-15-quarto-tip-brand-positron/

This becomes valuable if the same visual identity will later be reused in presentations, reports, or teaching material.

## Citations and bibliography

https://quarto.org/docs/authoring/citations.html

Quarto supports BibTeX/BibLaTeX and CSL. Keep a `references.bib` file when citation-aware pages are useful.

## Citeable web articles

https://quarto.org/docs/authoring/create-citeable-articles.html

Useful later if technical notes or tutorials on the website should themselves expose citation metadata.

## GitHub Pages publishing

https://quarto.org/docs/publishing/github-pages.html

This is the primary deployment reference for the setup below.

---

# 6. Content preparation before coding

Prepare the following before spending time on design.

## Identity assets

- professional headshot;
- preferred displayed academic name;
- lecturer/researcher title;
- university/faculty/program affiliation;
- short biography (around 80-150 words for homepage);
- longer biography for About;
- professional email;
- CV PDF;
- ORCID;
- Google Scholar;
- GitHub;
- LinkedIn, if desired.

## Research content

For each research theme, prepare:

- title;
- 1-2 sentence explanation understandable outside the narrow field;
- representative image/figure if available;
- 2-4 representative publications/projects.

Avoid presenting research interests as only a long keyword list.

## Publications

For every publication ideally keep:

```text
Title
Authors
Year
Venue
DOI / publisher URL
Abstract or 2-3 sentence summary
PDF (if legally shareable)
Code URL
Dataset URL
BibTeX
Thumbnail / representative figure (optional)
```

## Teaching

For each course:

```text
Course name
Course code (optional)
Short description
Semester/year
Syllabus / RPS (if public)
Modules
Slides
Labs / notebooks
Datasets
Assignments or exercises intended for public release
```

Do **not** publish private student information, answer keys that should remain confidential, internal credentials, or copyrighted material that you do not have permission to redistribute.

---

# 7. Install the tools

## 7.1 Install Quarto

Official download page:

https://quarto.org/docs/download/

After installation, verify:

```bash
quarto --version
```

## 7.2 Recommended editor

VS Code works well for this workflow. Install the Quarto extension if desired.

You should also have Git installed:

```bash
git --version
```

---

# 8. Create the GitHub repository

On GitHub:

1. Click **New repository**.
2. Name it exactly:

   ```text
   <username>.github.io
   ```

3. If using **GitHub Free**, choose **Public**.
4. Add a short description, for example:

   ```text
   Academic portfolio, research, publications, and teaching resources.
   ```

5. Create the repository.

For the first setup, it is fine to create it without extra generated files and initialize the project locally.

---

# 9. Create the local Quarto website and connect it to GitHub

Example workflow:

```bash
quarto create project website <username>.github.io
cd <username>.github.io
git init
git branch -M main
git remote add origin https://github.com/<username>/<username>.github.io.git
```

Then preview:

```bash
quarto preview
```

Quarto opens a local development address in your browser. Keep `quarto preview` running while editing; most changes will appear automatically.

If creating the project through VS Code/Positron instead, the resulting structure is equivalent.

---

# 10. Recommended project structure

Use a scalable structure from the beginning:

```text
<username>.github.io/
├── _quarto.yml
├── _brand.yml                 # optional, recommended later
├── styles.css
├── index.qmd
├── about.qmd
├── research.qmd
├── contact.qmd
├── cv/
│   └── cv.pdf
├── publications/
│   ├── index.qmd
│   ├── paper-01/
│   │   └── index.qmd
│   └── paper-02/
│       └── index.qmd
├── projects/
│   ├── index.qmd
│   ├── project-01/
│   │   └── index.qmd
│   └── project-02/
│       └── index.qmd
├── teaching/
│   ├── index.qmd
│   ├── data-mining/
│   │   ├── index.qmd
│   │   ├── module-01.qmd
│   │   └── module-02.qmd
│   └── artificial-intelligence/
│       └── index.qmd
├── activities/
│   └── index.qmd
├── posts/                     # optional blog / technical notes
├── images/
│   ├── profile.jpg
│   ├── og-image.png
│   └── projects/
├── references.bib             # optional
├── .gitignore
└── README.md
```

Do not create every folder immediately if there is no content yet. The structure is the target architecture.

---

# 11. Starter `_quarto.yml`

A strong first configuration is:

```yaml
project:
  type: website

website:
  title: "Akhiyar Waladi"
  description: "Lecturer, researcher, publications, projects, and teaching resources."
  site-url: "https://akhiyarwaladi.github.io"
  favicon: images/favicon.png
  image: images/og-image.png
  open-graph: true
  twitter-card: true
  search: true
  back-to-top-navigation: true

  navbar:
    left:
      - text: Home
        href: index.qmd
      - text: About
        href: about.qmd
      - text: Research
        href: research.qmd
      - text: Publications
        href: publications/index.qmd
      - text: Teaching
        href: teaching/index.qmd
      - text: Projects
        href: projects/index.qmd
      - text: Contact
        href: contact.qmd
    right:
      - icon: github
        href: https://github.com/<username>
        aria-label: GitHub

  page-footer:
    left: "© Akhiyar Waladi"
    right: "Built with Quarto"

format:
  html:
    theme:
      light: cosmo
      dark: darkly
    css: styles.css
    toc: true

execute:
  freeze: auto
```

### Notes

- Replace placeholder URLs before publishing.
- `site-url` is important for correct absolute social-preview metadata.
- `open-graph: true` improves link previews on services such as LinkedIn and other apps that use Open Graph.
- `search: true` becomes increasingly valuable when teaching pages grow.
- `freeze: auto` is useful if pages contain executable Python/R/Julia content and the computation should not run every time the site is rebuilt on GitHub.

Official website options:  
https://quarto.org/docs/reference/projects/websites.html

---

# 12. Design the homepage as an academic landing page, not a CV dump

A recommended homepage information order:

```text
[Headshot]   Name
             Lecturer | Researcher | Educator
             Short 2-3 sentence introduction
             [Publications] [Research] [Teaching] [CV]

Selected Research
-----------------
Research theme 1 | Research theme 2 | Research theme 3

Featured Publications
---------------------
Publication 1
Publication 2
Publication 3

Teaching
--------
Course 1 | Course 2 | Course 3

Selected Projects / Activities
------------------------------
Project cards

Professional links / Contact
```

### Avoid on the homepage

- full multi-page CV copied into the homepage;
- 30-publication bibliography;
- large tables;
- too many institutional details above the research identity;
- excessive animations;
- several different accent colors;
- low-resolution profile photos.

The homepage should answer within a few seconds:

1. Who is this person?
2. What does this person work on?
3. What can I explore here?
4. How can I contact or verify this person's work?

---

# 13. Create the About page

Quarto has purpose-built personal About templates.

Example:

```yaml
---
title: "About"
image: images/profile.jpg
about:
  template: solana
  image-shape: rounded
  links:
    - icon: envelope
      text: Email
      href: mailto:your-email@example.com
    - icon: github
      text: GitHub
      href: https://github.com/<username>
---
```

Below the header, include only useful sections such as:

```markdown
## Biography

## Research interests

## Education

## Academic experience

## Professional service
```

Keep the formal downloadable CV available separately.

Official About-page documentation:  
https://quarto.org/docs/websites/website-about.html

---

# 14. Build Publications with Quarto listings

Do not maintain a giant hand-written list if the publication count will grow.

Recommended structure:

```text
publications/
├── index.qmd
├── publication-a/
│   └── index.qmd
├── publication-b/
│   └── index.qmd
└── publication-c/
    └── index.qmd
```

Example metadata for one publication page:

```yaml
---
title: "Example Publication Title"
description: "A concise plain-language explanation of the paper."
date: 2026-01-01
categories: [Machine Learning, Computer Vision]
author:
  - name: "Author One"
  - name: "Author Two"
doi: "10.xxxx/example"
image: thumbnail.png
---
```

Then `publications/index.qmd` can use a listing:

```yaml
---
title: "Publications"
listing:
  contents: "**/index.qmd"
  type: default
  sort: "date desc"
  fields: [date, title, description, categories]
---
```

You can also use a grid layout for more visual publication cards.

Official listings documentation:  
https://quarto.org/docs/websites/website-listings.html

### Publication quality rule

For important papers, add a **plain-language summary and key contribution**. Do not make visitors infer the value of the research only from the paper title and abstract.

Where appropriate provide:

```text
[DOI] [Publisher] [PDF] [Code] [Dataset] [BibTeX]
```

Only provide PDFs you are legally permitted to distribute.

---

# 15. Use BibTeX when useful

Keep shared citation data in:

```text
references.bib
```

Quarto can use BibTeX/BibLaTeX/CSL to generate citations and bibliographies.

Official citation guide:  
https://quarto.org/docs/authoring/citations.html

For a portfolio, you do not necessarily need to generate the entire Publications page from a `.bib` file in version 1. It is often easier to create richer publication pages with metadata first and introduce automation later.

---

# 16. Build the Teaching section in two levels

Use two concepts:

## Level A, Courses

```text
Teaching
├── Data Mining
├── Artificial Intelligence
├── Cloud Computing
└── Statistics
```

Each course landing page can show:

- description;
- learning objectives;
- semester/year;
- syllabus/RPS if public;
- modules;
- slides;
- notebooks;
- datasets;
- recommended readings.

## Level B, Learning materials/modules

Example:

```text
Data Mining
├── 01 Introduction
├── 02 Data Preparation
├── 03 Classification
├── 04 Clustering
├── 05 Association Rules
└── Exercises
```

This is where Quarto is especially strong because a module can include:

- Markdown explanation;
- equations;
- figures;
- tables;
- executable Python/R code;
- Jupyter output;
- references;
- cross-references;
- callout boxes.

If one course grows into a large textbook-like resource, later turn that course into a **Quarto Book**.

Quarto Books:  
https://quarto.org/docs/books/

---

# 17. Create a Projects page

Use a grid listing with a representative image for each project.

Each project card/page should answer:

```text
What problem is being solved?
What is your role?
What technology/method is used?
What was produced?
Where can someone see the paper/code/demo?
```

Good project metadata:

```yaml
---
title: "Project Name"
description: "One-sentence description."
date: 2026-01-01
categories: [AI, IoT]
image: thumbnail.jpg
---
```

Avoid listing only software names or buzzwords.

---

# 18. Add professional visual quality

## Use one visual identity

Choose:

- one primary accent color;
- one secondary color if genuinely necessary;
- a consistent heading font;
- a highly readable body font;
- consistent border radius and spacing.

Do not make every section use a different color.

## Use `_brand.yml` later

Once the visual direction is stable, move core identity settings to `_brand.yml` so the brand can be reused across website pages, presentations, reports, and possibly teaching outputs.

## Light and dark mode

A simple Quarto configuration is:

```yaml
format:
  html:
    theme:
      light: cosmo
      dark: darkly
```

Official theming guide:  
https://quarto.org/docs/output-formats/html-themes.html

## Typography

The official Quarto personal-site workshop specifically points learners to font and contrast resources while teaching CSS/SCSS customization.

Resources:

- Google Fonts: https://fonts.google.com/
- Bootstrap Icons: https://icons.getbootstrap.com/
- Colour Contrast Checker: https://colourcontrast.cc/

Use web fonts sparingly; two font families are usually enough.

---

# 19. Improve accessibility

For every meaningful image, provide alt text:

```markdown
![Diagram showing the model evaluation workflow](images/workflow.png)
```

Also:

- use real headings (`##`, `###`) instead of bold text as fake headings;
- maintain sufficient color contrast;
- do not encode meaning using color alone;
- make link text descriptive;
- test keyboard navigation;
- test mobile widths;
- keep font sizes readable;
- avoid huge animated elements.

Accessibility is part of site quality, not an optional visual extra.

---

# 20. Add social metadata and preview images

In `_quarto.yml`:

```yaml
website:
  site-url: "https://<username>.github.io"
  image: images/og-image.png
  open-graph: true
  twitter-card: true
```

This helps produce richer previews when your website or article is shared on compatible social/professional platforms.

Official source:  
https://quarto.org/docs/websites/website-tools.html

Create a clean default preview graphic containing only essential branding, not a screenshot of the entire homepage.

---

# 21. Add site search early

Enable:

```yaml
website:
  search: true
```

Search becomes particularly useful when modules, publications, and technical notes grow.

Official navigation/search guide:  
https://quarto.org/docs/websites/website-navigation.html

---

# 22. Analytics: optional, not required for launch

Do not delay the portfolio launch because analytics are not configured.

Later, Quarto supports integrations including Google Analytics and Plausible Analytics.

Official documentation:  
https://quarto.org/docs/websites/website-tools.html

If using tracking that relies on cookies, review the relevant privacy/cookie-consent requirements. Quarto provides cookie-consent configuration for supported use cases.

---

# 23. Create `.gitignore`

For a `gh-pages` publishing workflow, start with:

```gitignore
/.quarto/
/_site/
```

If using executable notebooks, do **not** automatically ignore `_freeze/` if you rely on Quarto's `freeze: auto` workflow; the official GitHub Actions guidance describes committing cached computation results when using that strategy.

Official deployment reference:  
https://quarto.org/docs/publishing/github-pages.html

---

# 24. Test locally before every important publish

Run:

```bash
quarto preview
```

Before committing a major change, also test a full render:

```bash
quarto render
```

Check:

- no broken internal links;
- navigation works;
- images load;
- PDF links work;
- mobile layout is acceptable;
- publication cards are not missing metadata;
- no local/private file path is visible;
- no secrets appear in source files.

---

# 25. Make the first Git commit

```bash
git status
git add .
git commit -m "Initial Quarto academic portfolio"
git branch -M main
git push -u origin main
```

Verify the source files appear in the repository.

---

# 26. First deployment to GitHub Pages, recommended simple method

Quarto's official documentation describes `quarto publish gh-pages` as the straightforward publishing workflow.

Run from the project directory:

```bash
quarto publish gh-pages
```

On the first run, Quarto will create a `gh-pages` branch and publish the rendered site there.

Official source:  
https://quarto.org/docs/publishing/github-pages.html

---

# 27. Special step for `<username>.github.io` repositories

A root user site behaves slightly differently from a normal project repository.

After the first:

```bash
quarto publish gh-pages
```

open the GitHub repository and go to:

```text
Settings
  -> Pages
  -> Build and deployment
```

Set the publishing source to the `gh-pages` branch (root folder) if GitHub has not already selected it.

The Quarto documentation explicitly notes that user sites served at `https://<username>.github.io/` need the source branch switched to `gh-pages` when using this workflow.

Official source:  
https://quarto.org/docs/publishing/github-pages.html#user-site

Then visit:

```text
https://<username>.github.io
```

---

# 28. Normal update workflow after the first deployment

Edit the source files, test locally, then:

```bash
quarto preview
```

Commit your changes:

```bash
git add .
git commit -m "Update publications and teaching materials"
git push
```

Then publish:

```bash
quarto publish gh-pages
```

This manual workflow is completely adequate for the first version.

---

# 29. Optional: automatic deployment with GitHub Actions

After the manual deployment is working reliably, automate it.

First run a local publish at least once:

```bash
quarto publish gh-pages
```

Then create:

```text
.github/workflows/publish.yml
```

Example based on Quarto's official workflow:

```yaml
on:
  workflow_dispatch:
  push:
    branches: main

name: Quarto Publish

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - name: Check out repository
        uses: actions/checkout@v4

      - name: Set up Quarto
        uses: quarto-dev/quarto-actions/setup@v2

      - name: Render and Publish
        uses: quarto-dev/quarto-actions/publish@v2
        with:
          target: gh-pages
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

Then in GitHub check:

```text
Settings
  -> Actions
  -> General
  -> Workflow permissions
  -> Read and write permissions
```

After this, a push to `main` can automatically rebuild/publish the site.

Official workflow reference:  
https://quarto.org/docs/publishing/github-pages.html#github-action

### Executable Python/R code

If website pages execute Python or R, do not make CI complexity the first problem you solve. Start with:

```yaml
execute:
  freeze: auto
```

Render computations locally and commit the frozen results. Later, if reproducible CI execution is genuinely needed, configure Python/R environments in the workflow.

---

# 30. Add HTTPS

GitHub Pages supports HTTPS. In the repository:

```text
Settings -> Pages -> Enforce HTTPS
```

Official documentation:  
https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https

---

# 31. Custom domain, optional later

Do not buy/configure a domain until the `github.io` version works properly.

Later you can point a custom domain such as:

```text
example.com
www.example.com
```

Quarto's GitHub Pages documentation recommends adding a `CNAME` file to the Quarto project root so it is preserved during rendering/publishing.

Official resources:

- https://quarto.org/docs/publishing/github-pages.html#custom-domain
- https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site

The hosting can remain on GitHub Pages; the domain registration is the part that normally costs money.

---

# 32. Quality roadmap: build in phases

## Phase 1, Functional portfolio

Complete:

- [ ] repository;
- [ ] homepage;
- [ ] About;
- [ ] Research;
- [ ] Publications;
- [ ] Teaching;
- [ ] Projects;
- [ ] Contact;
- [ ] working GitHub Pages deployment.

Do not spend days perfecting CSS before this exists.

## Phase 2, Better information architecture

Add:

- [ ] publication listings;
- [ ] project listings;
- [ ] course structure;
- [ ] full-text search;
- [ ] selected/featured content on homepage;
- [ ] CV download;
- [ ] ORCID / Scholar / GitHub links.

## Phase 3, Visual polish

Add:

- [ ] custom SCSS;
- [ ] stable color palette;
- [ ] typography;
- [ ] high-quality headshot;
- [ ] thumbnails;
- [ ] favicon;
- [ ] Open Graph preview image;
- [ ] light/dark mode;
- [ ] `_brand.yml`.

## Phase 4, Teaching platform

Add course material progressively:

- [ ] module pages;
- [ ] exercises;
- [ ] Jupyter/Python examples;
- [ ] downloadable resources;
- [ ] references;
- [ ] course-specific sidebar;
- [ ] convert large courses into Quarto Books when useful.

## Phase 5, Automation

Only after content is stable:

- [ ] GitHub Actions auto-publish;
- [ ] publication metadata automation if desired;
- [ ] analytics;
- [ ] custom domain;
- [ ] content update workflow.

---

# 33. Suggested content update routine

A portfolio becomes stale when updating it is difficult. Keep the workflow simple.

### New publication

```text
1. Add publication page/metadata.
2. Add DOI and permitted links.
3. Add 2-3 sentence plain-language summary.
4. Add thumbnail if useful.
5. Preview.
6. Commit and publish.
```

### New course/module

```text
1. Add/update course landing page.
2. Add module .qmd.
3. Add code/notebook/assets.
4. Preview mobile + desktop.
5. Commit and publish.
```

### New project

```text
1. Add project page.
2. Explain problem and contribution.
3. Add representative visual.
4. Link paper/code/demo if public.
5. Commit and publish.
```

---

# 34. Recommended design principles for this specific academic portfolio

1. **Lead with academic identity, not administrative biodata.**
2. **Show 3-5 selected works before showing complete archives.**
3. **Give every important publication a plain-language explanation.**
4. **Make teaching materials directly useful to students.**
5. **Use cards/listings for scannable content, but avoid making every paragraph a card.**
6. **Keep navigation to roughly 6-8 top-level items.**
7. **Use one consistent visual identity.**
8. **Make the website mobile-friendly.**
9. **Optimize images before committing them.**
10. **Keep PDFs and large datasets out of the repository when an external canonical source is better.**
11. **Link to DOI, ORCID, Scholar, GitHub, and institutional profiles instead of duplicating everything.**
12. **Treat accessibility and social metadata as part of professional quality.**

---

# 35. What should NOT be in the repository

Especially if the repository is public, never commit:

```text
.env
API keys
cloud credentials
private SSH keys
passwords
private student data
unreleased confidential manuscripts
internal university documents not meant for publication
copyrighted books/slides you cannot redistribute
large raw research datasets that belong elsewhere
```

Use `.gitignore` for local/generated files and keep secrets outside the website project.

---

# 36. Recommended first-week build order

Use this sequence rather than trying to finish everything at once:

```text
1. Create public <username>.github.io repository.
2. Install Quarto and verify it.
3. Create website project.
4. Create navbar and basic pages.
5. Build a clean homepage.
6. Add About.
7. Add 3 selected publications.
8. Add current teaching courses.
9. Add 2-3 selected projects.
10. Configure social links and CV.
11. Preview and fix mobile layout.
12. Publish to gh-pages.
13. Verify GitHub Pages source branch.
14. Test the live site.
15. Only then improve custom CSS/SCSS.
```

The objective of version 1 is **a useful live academic portfolio**, not a perfect design system.

---

# 37. Minimal launch criteria

The website is ready for its first public release when all of these are true:

- [ ] Homepage explains who you are and what you work on.
- [ ] Profile photo is clear and appropriately sized.
- [ ] About page is complete.
- [ ] At least three representative publications are available.
- [ ] Research themes are explained in plain language.
- [ ] Teaching page lists current/relevant courses.
- [ ] At least some learning materials are useful, not placeholder pages.
- [ ] Projects page has representative work.
- [ ] Professional links work.
- [ ] Contact information is available.
- [ ] Site search works if enabled.
- [ ] No broken images or links.
- [ ] Mobile layout has been checked.
- [ ] No secret/private files are present in Git history.
- [ ] GitHub Pages deploy succeeds.
- [ ] HTTPS works.

---

# 38. Source/reference list

## Quarto official

- Main website guide: https://quarto.org/docs/websites/
- Gallery: https://quarto.org/docs/gallery/
- About pages: https://quarto.org/docs/websites/website-about.html
- Navigation/search: https://quarto.org/docs/websites/website-navigation.html
- Listings: https://quarto.org/docs/websites/website-listings.html
- Website tools/social metadata/analytics: https://quarto.org/docs/websites/website-tools.html
- Website options: https://quarto.org/docs/reference/projects/websites.html
- HTML themes: https://quarto.org/docs/output-formats/html-themes.html
- Citations: https://quarto.org/docs/authoring/citations.html
- Citeable articles: https://quarto.org/docs/authoring/create-citeable-articles.html
- Quarto Books: https://quarto.org/docs/books/
- GitHub Pages publishing: https://quarto.org/docs/publishing/github-pages.html
- Personal website video series: https://opensource.posit.co/blog/2024-12-04_websites-workshop/
- Quarto downloads: https://quarto.org/docs/download/

## GitHub official

- What is GitHub Pages: https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages
- Create a Pages site: https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
- Configure publishing source: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
- HTTPS: https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https
- Custom domains: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
- Pages access control: https://docs.github.com/enterprise-cloud@latest/pages/getting-started-with-github-pages/changing-the-visibility-of-your-github-pages-site

## Live examples

- Beatriz Milz: https://beamilz.com/
- Mike Mahoney: https://www.mm218.dev/
- Hamel Husain: https://hamel.dev/
- Andrew Heiss teaching: https://www.andrewheiss.com/teaching/
- Python for Data Science: https://pythonds.linogaliana.fr/

---

# 39. Final recommendation

For the initial version:

```text
Framework:       Quarto
Source control:  GitHub
Repository:      <username>.github.io
Visibility:      Public (GitHub Free)
Hosting:         GitHub Pages
First publish:   quarto publish gh-pages
Automation:      GitHub Actions after manual deployment works
Domain:          github.io first; custom domain later
Content style:   Academic portfolio + useful teaching resources
```

This gives the best balance of cost, maintainability, academic publishing features, and long-term usefulness for a lecturer/researcher portfolio.
