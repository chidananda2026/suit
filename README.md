# PreAI suite website (suite.preai.dev)

The suite's own site: one short landing page for the three products (PreAI
Sentry, Tokenvoy, Prahari) and their enterprise servers, plus the legal pages.
Same design system as the product sites, in the suite blue; each product keeps
its own colour (Sentry blue, Tokenvoy amber, Prahari teal).

Plain HTML, CSS and a few lines of JavaScript. No build step. The Inter font is
self-hosted, so no page makes a request to a third party.

## Preview

```bash
python -m http.server 8081 --directory suite-website   # then http://localhost:8081
```

## Layout

```
index.html               the landing page
terms.html               terms of use
privacy.html             privacy notice
refunds.html             refund policy
disclaimer.html          disclaimer: constant effort, honest limits, where responsibility ends
styles.css               the design system, self-hosted Inter, legal-page styles
main.js                  the mobile menu
assets/checkpoint.png    the hero picture: the gate explainer's opening frame, re-rendered without its heading, 1920×880
assets/checkpoint.webp   the same, smaller, served first
assets/fonts/            Inter, variable 400–800, one file per script subset (SIL OFL), copied from ../company-website
assets/*-icon.svg        the three product marks
```

## The landing page

Kept short on purpose (the user's call, 2026-11-05: "too lengthy, keep it
simple", then "add another 10% more"). Top to bottom:

1. **Hero:** "Your gates see a trusted process on the right account. We see the agent." with the picture.
2. **Gate by gate:** one table, ten rows: your gate, what it asks, what the suite asks instead. On a phone each row becomes a card.
3. **It already happened:** three public incidents, one per campaign line, dated, no source links.
4. **Who it's for:** six one-liners (CISO, SOC lead, CTO, compliance, CFO, board).
5. **Three products:** one card each, linking to the product's own site.
6. **Enterprise:** the four servers, one line each.
7. **Getting started:** the pilot in three steps (learn, protect, decide), then the Enterprise card.
8. **FAQ:** four questions; the last points to the disclaimer.

## Copy rules (the user's, 2026-11-05)

- **Sales and marketing level only.** Say what each product does for the buyer, not how it works inside: no hooks, algorithms, signature schemes or internal mechanisms.
- **Generic.** No counts, no region-specific identifiers, no regulation lists, no vendor lists.
- **No external references.** No links to news, analysts or other third parties. The only outbound links go to our own product sites and the Sanniddhi site. Incidents are described from public accounts, dated, in rounded terms, and the disclaimer covers them.
- **Sanniddhi-friendly disclaimers.** In the AI world nothing is a guarantee. We put in constant effort and keep updating; we are not responsible for data loss, hacks or anything beyond what the product can reasonably do or beyond our control. Phrased so that it does not blame or hurt the reader.
- **Nothing says "pending."** A gap goes to the roadmap.

## The legal pages

`terms.html`, `privacy.html`, `refunds.html` and `disclaimer.html` share the
landing page's header and footer, are marked `noindex`, and name Sanniddhi
Infosolutions Pvt Limited, Dubai, as the provider. Governing law is the UAE as
applied in Dubai. The liability cap in the terms (fees in the twelve months
before the claim, or one hundred US dollars) and the refund rules are drafts:
**have counsel review them before launch**, alongside the company site's legal
pages in `../company-website/`.

## Rebuilding the hero picture

The picture comes from the gate explainer's opening still,
`devtools/video/gates/build/html/still-00-opening-2.html`, with its panel
heading hidden (`visibility:hidden`, so the layout does not move), rendered
with headless Chrome at 1920×1080 and cropped to 1920×880. Save it as PNG and
as WebP (`quality=86`).

## Where the words come from

The gates table from the explainer's data (`../devtools/video/gates/gates.py`),
the incidents and audience lines from the marketing kit (`../docs/marketing/`),
the product and server lines from the product sites and the Enterprise SOC
README, all cut to sales level under the rules above.

## Before it goes live

- **Prahari's site** is linked as `https://prahari.preai.dev` until its domain is decided.
- **Domain.** Add a canonical URL and absolute `og:url` and `og:image` once `suite.preai.dev` is set up.
- **Calls to action** are `mailto:` links to `info@preai.dev`.
- **Legal review** of the four legal pages.
- **Outbound links** (the product sites, the Sanniddhi site) open in a new tab; in-page anchors and `mailto:` links do not.
