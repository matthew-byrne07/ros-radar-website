# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Marketing website for **ROS Radar**, an AI-powered receipt-scanning / expense-tracking mobile app for Irish self-assessment (Form 11, VAT3, Revenue compliance). Static site — no build step, no framework, no package manager, no tests. Deployed via GitHub Pages to the custom domain `rosradar.com` (see `CNAME` — do not delete this file or the domain mapping breaks).

## Development

Open the HTML files directly in a browser, or serve locally:

```
python -m http.server 8000
```

Deploying = pushing to `main` (GitHub Pages serves the repo root).

## Structure

Three self-contained pages, each with all CSS and JS inlined in the file (no shared stylesheet or script):

- `index.html` — landing page: hero with animated radar scope, bento feature grid, phone-frame screenshot showcase, how-it-works steps, pricing (single plan, €19.99/mo, 7-day trial), trust/compliance badges, CTA, footer.
- `privacy.html` — GDPR privacy policy (numbered card sections).
- `terms.html` — terms & conditions (numbered card sections).

Because styles and scripts are duplicated per file, **shared UI changes (nav, footer, brand, fonts, colors) must be applied to all three files** to stay consistent. The legal pages share a smaller common style block with each other; `index.html` has its own larger one.

## Conventions

- Dark sci-fi "radar HUD" theme. Design tokens live in each file's `:root` block (`--emerald: #10B981` is the brand color; fonts: Bricolage Grotesque for display, Hanken Grotesk for body, JetBrains Mono for HUD/mono accents, loaded from Google Fonts).
- All icons are inline SVG (Feather-style strokes); favicon is an inline `data:` SVG. No icon libraries.
- JS is vanilla and minimal: scroll progress bar, sticky-nav state, mobile menu toggle, IntersectionObserver reveal animations, count-up metrics, cursor spotlight/tilt effects. All motion respects `prefers-reduced-motion`.
- App screenshots in the showcase load from `images/` with an `onerror` fallback to a placeholder; the referenced PNGs (`home-screen.png`, `audit-shield.png`, `entry-methods.png`, `tax-preferences.png`) may not exist yet in the repo.

## Content constraints

- Tax/legal claims are specific to Irish law (Section 887 TCA 1997, VAT rates 23/13.5/9/0%, Form 11, GDPR/DPC). Keep factual claims consistent across all three pages — e.g. the AI model named, pricing, and retention periods appear on multiple pages.
- Contact emails use the `@rosradar.ie` domain; the site itself is served at `rosradar.com`.
