# MoonLeaf Studio — website

The marketing site for **MoonLeaf Studio**, a tiny iOS app studio.
A single-file, dependency-free static page (HTML + CSS + a little vanilla JS),
ready to host on **GitHub Pages**.

> Live: `https://moonleaf-studio.github.io/moonleaf-studio/`
> (once Pages is enabled)

[![Deploy to GitHub Pages](https://github.com/MoonLeaf-Studio/moonleaf-studio/actions/workflows/deploy.yml/badge.svg)](https://github.com/MoonLeaf-Studio/moonleaf-studio/actions/workflows/deploy.yml)

## What's inside

```
moonleaf-studio/
├── index.html                 # the entire website (self-contained)
├── 404.html                   # styled not-found page
├── .nojekyll                  # serve files as-is (skip Jekyll)
├── .github/workflows/deploy.yml  # auto-deploy to Pages on push to main
├── README.md
├── LICENSE
└── .gitignore
```

No build step, no `node_modules`. Fonts load from Google Fonts at runtime.

## Run it locally

Just open `index.html`, or serve it (recommended, so relative paths behave):

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

## Publish to GitHub

### 1. Create the repo and push

With the GitHub CLI:

```bash
cd moonleaf-studio
gh repo create moonleaf-studio --public --source=. --remote=origin --push
```

…or with plain git (after creating an empty repo on github.com):

```bash
cd moonleaf-studio
git remote add origin git@github.com:MoonLeaf-Studio/moonleaf-studio.git
git push -u origin main
```

> This folder is already a git repo with an initial commit on `main`,
> so you only need to add the remote and push.

### 2. Turn on Pages

**Option A — GitHub Actions (included workflow, recommended).**
Repo → **Settings → Pages → Build and deployment → Source: GitHub Actions**.
Every push to `main` then runs `.github/workflows/deploy.yml` and publishes.

**Option B — Deploy from a branch.**
Repo → **Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)`**.
The `.nojekyll` file ensures everything is served verbatim. (You can delete
the workflow if you use this option.)

## Custom domain (optional)

Add a `CNAME` file containing your domain (e.g. `moonleaf.studio`), point your
DNS to GitHub Pages, then set the domain under **Settings → Pages**.

```bash
echo "moonleaf.studio" > CNAME && git add CNAME && git commit -m "Add custom domain" && git push
```

## Editing

Everything lives in `index.html`: the `:root` CSS variables near the top hold
the palette (night greens, mint, moon-gold, lilac), and each `<section>` is
labeled. App cards, copy, and links are plain HTML — swap the placeholder
`hello@moonleaf.studio` and `#` links for live ones.

## License

[MIT](./LICENSE).
