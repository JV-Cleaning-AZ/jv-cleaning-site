# JV Cleaning LLC website

Public website for JV Cleaning LLC (family-owned commercial cleaning in Arizona since 2002). Rhino Sweepers is its parking-lot sweeping division, not a separate company.

Live: https://jvcleaningaz.com (rhinosweepers.com redirects to /#rhino)

## Stack (fixed, do not change)

- Static HTML, no build step, no framework, no npm, no bundler.
- Netlify (free plan) auto-deploys every push to `main` in about 30 seconds.
- DNS lives in Cloudflare. Never touch DNS from here.
- Budget is zero. Never propose paid plans or tools.

## Files

- `index.html`: the whole one-page site. Inline CSS and JS on purpose.
- `thanks.html`, `404.html`: form success page and custom 404.
- `favicon.svg`: external favicon. Never use a data URI SVG favicon (it broke the head twice).
- `brand/`: images. `rhino-badge.webp` belongs only in the Rhino section.
- `_redirects`: keeps `/README.md` from being served.
- `_headers`: security headers.
- `robots.txt`, `sitemap.xml`: point to https://jvcleaningaz.com

## Hard rules

1. This repo is PUBLIC forever, including history. Never commit phone numbers not yet on the site, Forms CSV exports, customer data, original WhatsApp photos, EXIF data, secrets, or internal notes.
2. Zero unconfirmed claims. No insurance, licensing, certifications, response times, 24/7, testimonials, ratings, reviews, client names, or cities unless the owner confirmed them in writing. When data is missing, design without it. Never ship `[PENDING]` placeholders.
3. The Netlify form must keep: `name="quote"`, `method="POST"`, `data-netlify="true"`, `netlify-honeypot="company2"`, hidden `form-name` input, `action="/thanks.html"`. Netlify strips these attributes from the served HTML at build time; that is normal.
4. No em dashes anywhere (code comments, copy, commit messages). Use commas, colons, or parentheses.
5. Accessibility floor: WCAG AA contrast (CTAs use dark text `#1E2126` on orange `#E8641B`), `prefers-reduced-motion` stops every animation, `<noscript>` fallback keeps reveal content visible, tap targets 44px.
6. Motion: entrances ease-out, only transform and opacity, never animate content the user is reading or typing in.
7. Brand: carbon `#1E2126`, orange `#E8641B`, dark orange `#B84A0E` for small text on light backgrounds, bone `#F6F4F0`. Fonts: Barlow Condensed (display) + Barlow (text).

## Workflow

1. Edit locally, show the diff, wait for Gabriel's explicit yes before committing to `main` (main = production).
2. Small commits, plain English messages.
3. After every deploy, verify live with cache busting (`?v=<timestamp>`): page loads, form markup present, images 200, no `PENDING`, no stray markup in `<head>`.
