# Product

## Register

brand

## Users

Irish self-employed people and small-business owners (Form 11 self-assessment filers) evaluating or already using the ROS Radar mobile app. Two contexts: prospects landing on the marketing page deciding whether to install, and existing app users arriving mid-task on a support or legal page (password reset, privacy policy, terms), usually on a phone.

## Product Purpose

Marketing and trust surface for the ROS Radar app. Three jobs: convert visitors into app installs/subscriptions (index), carry the legal/compliance pages the app and the app stores link to (privacy, terms — both must stay in sync with the in-app screens), and host small app-support utilities (password reset). Success: the site feels like the same precise instrument the app is, and every compliance link required for store submission resolves.

## Brand Personality

Technical, vigilant, trustworthy. Dark sci-fi "radar HUD": the product watches your expenses the way a radar watches airspace. Serious about Irish Revenue compliance without being corporate-sterile. Voice is plain and specific; legal content is presented with the same craft as marketing content.

## Anti-references

- Generic SaaS cream/pastel landing pages with mascot illustrations
- Corporate-bank sterility (navy suits, stock handshake photos)
- Glassmorphism-heavy dashboards; decorative blur as a default
- Template fintech landing pages (hero metric + gradient text + identical card grids)

## Design Principles

1. **Instrument, not brochure.** HUD details (mono labels, corner brackets, the grid backdrop) encode precision; they are the signature, used sparingly.
2. **One emerald.** `#10B981` carries the identity. Other hues are functional signals only (amber = caution, red = error, indigo = rare accent).
3. **Compliance is content.** Legal pages get real design attention; retention rules and GDPR rights are presented to be read, not buried.
4. **Motion respects the reader.** Subtle pulses and reveals; every animation has a `prefers-reduced-motion` fallback.
5. **Each page is self-contained.** CSS/JS inlined per page (no build step); the shared look is maintained by discipline — shell changes (nav, footer, tokens, fonts) are applied to every page.

## Accessibility & Inclusion

WCAG AA contrast on dark surfaces (body text ≥4.5:1); `prefers-reduced-motion` honored globally; visible keyboard focus; mobile-first responsive; fonts self-hosted (no third-party font requests).
