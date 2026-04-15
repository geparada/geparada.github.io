# Guillermo E. Parada — personal academic website

Static website built with [Astro](https://astro.build/) and deployed to **GitHub Pages** via **GitHub Actions**.

- Framework: Astro 4.x (no UI framework, pure Astro components and CSS).
- Content: hand-written `.astro` pages under `src/pages/`.
- Hosting: GitHub Pages (root site at `https://geparada.github.io`).

## Local development

```bash
npm install
npm run dev        # start dev server at http://localhost:4321
npm run build      # build static site to dist/
npm run preview    # preview the built site locally
```

Node.js 18+ is required.

## Project structure

```text
guillermo-parada-site/
├── .github/workflows/deploy.yml   # GitHub Actions → GitHub Pages
├── astro.config.mjs               # site URL (root-site config)
├── public/
│   ├── Guillermo_Parada_CV.pdf    # downloadable CV
│   └── images/                    # static images (empty for now)
├── src/
│   ├── components/
│   │   ├── Header.astro
│   │   ├── Footer.astro
│   │   ├── PublicationCard.astro
│   │   └── ResearchCard.astro
│   ├── layouts/
│   │   └── Layout.astro
│   ├── pages/
│   │   ├── index.astro            # Home
│   │   ├── research.astro
│   │   ├── publications.astro
│   │   ├── software.astro
│   │   ├── cv.astro
│   │   └── contact.astro
│   └── styles/global.css
└── package.json
```

## Deployment — GitHub Pages

This site is configured as a **root user site** at `https://geparada.github.io`.

### One-time setup

1. Create a public GitHub repository named exactly **`geparada.github.io`** (under the `geparada` account).
2. Push this project to that repo on `main`:

   ```bash
   git init -b main
   git add .
   git commit -m "Initial commit: personal academic website"
   git remote add origin git@github.com:geparada/geparada.github.io.git
   git push -u origin main
   ```

3. On GitHub, open the repo → **Settings → Pages** → under **Build and deployment**, set **Source** to **GitHub Actions**.
4. The workflow at `.github/workflows/deploy.yml` will run on every push to `main` and publish the site.
5. The site will be live at `https://geparada.github.io`.

### Project-site alternative

If you prefer a project-site (`https://geparada.github.io/personal-website/`):

- Rename the repo `personal-website` and edit `astro.config.mjs` to add `base: '/personal-website'`.
- Update internal links if needed (Astro handles most of them automatically when you use the `base` setting via `BASE_URL`).

### Custom domain (optional, later)

1. Configure DNS with your domain provider (see GitHub Pages docs).
2. Add `public/CNAME` with the bare domain, e.g. `guillermoparada.com`.
3. Update `site` in `astro.config.mjs` and remove `base` if previously used.
4. In repo **Settings → Pages**, enable HTTPS once the certificate is issued.

## Content overview

| Page | File |
|---|---|
| Home | `src/pages/index.astro` |
| Research | `src/pages/research.astro` |
| Publications | `src/pages/publications.astro` |
| Software | `src/pages/software.astro` |
| CV | `src/pages/cv.astro` |
| Contact | `src/pages/contact.astro` |

The publication lists are plain JS arrays at the top of `publications.astro` and `index.astro` — easy to edit.

## Placeholders marked `TODO`

- ORCID iD on the Contact page.
- Any DOI/link flagged with the `todo` class will render with an italic muted style so they are easy to spot.

## Privacy

This repository contains only public-safe information: peer-reviewed or preprinted science, public
biography, public fellowship and training history, and public profile links. It does not contain
unpublished project plans, manuscript-review content, grant strategy, or private correspondence.
