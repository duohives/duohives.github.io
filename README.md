# DuoHives Static Site

This repo is now a plain static website (no Jekyll). Files under the repo root are served directly by GitHub Pages.

How it’s organized
- index.html: main landing page with all sections
- assets/css/style.css: compiled, production CSS
- assets/js/scripts.js: minimal JS for mobile menu
- images/: logos, features and illustration assets
- CNAME: custom domain configuration
- .nojekyll: tells GitHub Pages not to run Jekyll

Local editing
- Edit `index.html`, `assets/css/style.css`, `assets/js/scripts.js`, and files in `images/`.
- No build step is required.

Deploy
- On push to `main`, GitHub Actions uploads the repository files and deploys to GitHub Pages.
- Workflow: `.github/workflows/jekyll.yml` (name kept, but it deploys static files only).
