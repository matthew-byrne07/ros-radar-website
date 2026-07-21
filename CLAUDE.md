# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Marketing website for **ROS Radar**, an AI-powered receipt-scanning / expense-tracking mobile app for Irish self-assessment (Form 11, VAT3, Revenue compliance). Static site — no build step, no framework, no package manager, no tests. Deployed as **Cloudflare Worker static assets** (see `wrangler.jsonc` — assets served from the repo root) to the custom domains `rosradar.ie` and `www.rosradar.ie`.

Legacy note: the site previously deployed via GitHub Pages to `rosradar.com`; `CNAME` is a leftover from that setup. Cloudflare ignores it — it only matters if GitHub Pages is still enabled on the repo (in which case pushing to `main` also publishes a second copy at rosradar.com). Whether rosradar.com should redirect, stay, or be dropped is an open decision.

## Development

Open the HTML files directly in a browser, or serve locally:

```
python -m http.server 8000
```

(or `npx wrangler dev` for a Cloudflare-faithful preview).

Deploying = `npx wrangler deploy` from the repo root. Pushing to GitHub does **not** publish the Cloudflare site (but see the GitHub Pages caveat above). `.assetsignore` keeps meta files (CLAUDE.md, configs, dotfolders) out of the deployed assets.

## Structure

Four self-contained pages, each with all CSS and JS inlined in the file (no shared stylesheet or script):

- `index.html` — landing page: hero with animated radar scope, bento feature grid, phone-frame screenshot showcase, how-it-works steps, pricing (single plan, €19.99/mo, 7-day trial), trust/compliance badges, CTA, footer.
- `privacy.html` — GDPR privacy policy (numbered card sections). Content must stay in sync with the in-app privacy screen (`privacy_policy_screen.dart` in the app repo); the app links to `https://rosradar.ie/privacy`.
- `terms.html` — terms & conditions (numbered card sections). Same sync rule with the in-app terms screen.
- `reset-password.html` — Supabase password-reset completion page for the mobile app, served at `https://rosradar.ie/reset-password`. Uses only the public Supabase URL + anon key (safe client-side). Themed to match the rest of the site.

Because styles and scripts are duplicated per file, **shared UI changes (nav, footer, brand, fonts, colors) must be applied to all themed files** to stay consistent. The legal pages share a smaller common style block with each other; `index.html` has its own larger one.

## Conventions

- Dark sci-fi "radar HUD" theme in the app's warm palette. Design tokens live in each file's `:root` block (`--brand: #F4600F` orange is the brand color, pink `#E83D5F` is the secondary accent, dark neutrals are warm-tinted — matches the app's `rosradar-colors.css`; fonts: Bricolage Grotesque for display, Hanken Grotesk for body, JetBrains Mono for HUD/mono accents — self-hosted from `fonts/`, not Google Fonts).
- Brand mark is the radar-dial logo (`logo-mark.png` at repo root, masters in the app repo under `ui design/logo/`); favicons are real files (`favicon.ico`, `favicon-32.png`, `apple-touch-icon.png`). Non-logo icons are inline SVG (Feather-style strokes). No icon libraries.
- JS is vanilla and minimal: scroll progress bar, sticky-nav state, mobile menu toggle, IntersectionObserver reveal animations, count-up metrics, cursor spotlight/tilt effects. All motion respects `prefers-reduced-motion`.
- App screenshots in the showcase load from `images/` with an `onerror` fallback to a placeholder; the referenced PNGs (`home-screen.png`, `audit-shield.png`, `entry-methods.png`, `tax-preferences.png`) may not exist yet in the repo.

## Content constraints

- Tax/legal claims are specific to Irish law (Section 887 TCA 1997, VAT rates 23/13.5/9/0%, Form 11, GDPR/DPC). Keep factual claims consistent across all three pages — e.g. the AI model named, pricing, and retention periods appear on multiple pages.
- Contact emails use the `@rosradar.ie` domain, matching the site's `rosradar.ie` domain.
