# Blend — Landing (GitHub Pages)

Static, single-file landing page to validate the idea. No build step, no dependencies.
Tailwind is loaded from a CDN and all icons are inline SVG, so you can host it as-is.

## What's here

- `index.html` — the full landing page (hero, features, dual mode, testimonials, pricing, waitlist, footer).
- `.nojekyll` — tells GitHub Pages to serve files as-is (skip Jekyll processing).

## Preview locally

Just open the file in a browser:

```bash
open index.html
```

Or serve it (optional):

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy to GitHub Pages (GitHub Actions)

This folder is already its own git repo (`main` branch) with a ready-to-go
workflow at `.github/workflows/pages.yml`. It deploys the repo **root** (where
`index.html` and `.nojekyll` live) on every push to `main`.

### Steps

1. Create an empty repo on GitHub, e.g. `blend-landing` (no README/license, to avoid conflicts).

2. Point this local repo at it and push:

   ```bash
   # from this folder (github-page/)
   git remote add origin https://github.com/<user>/blend-landing.git
   git push -u origin main
   ```

3. In the repo on GitHub: **Settings → Pages → Build and deployment →
   Source: GitHub Actions**. (You only do this once.)

4. The `Deploy landing to GitHub Pages` workflow runs automatically. When it
   finishes (**Actions** tab), your site is live at:

   ```
   https://<user>.github.io/blend-landing/
   ```

Every later `git push` to `main` redeploys automatically. You can also trigger it
manually from the **Actions** tab (the workflow has `workflow_dispatch` enabled).

## Collecting signups

The waitlist form currently shows a thank-you message client-side only.
To actually capture emails while validating, point the `<form>` at a no-backend
service and remove the `onsubmit` handler:

- [Formspree](https://formspree.io): `<form action="https://formspree.io/f/XXXX" method="POST">`
- [Tally](https://tally.so) or Google Forms: embed or link out.

Search `#waitlist` in `index.html` to find the form.
