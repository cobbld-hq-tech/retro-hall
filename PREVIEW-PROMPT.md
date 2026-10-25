# Reusable prompt: client concept mockups + desktop/mobile preview

Copy everything inside the fence, fill in the `{{ }}` slots, delete any line that doesn't apply.
Based on the Chicoco build (`concepts/index.html` + the two `.dc.html` concepts).

```text
Build homepage concept mockups for a client, plus a single preview page I can send them
that switches between the concepts and between desktop and mobile views.

## The client
- Business name: {{BUSINESS_NAME}}
- What they are: {{ONE_LINE_DESCRIPTION}}   (e.g. "Chicago-style roasted-chicken food truck")
- Location / service area: {{CITY_REGION}}
- Audience: {{WHO_BUYS}}
- Tone: {{3_ADJECTIVES}}   (e.g. "loud, local, no-nonsense")
- Brand assets I have: {{LOGO_FILES / COLORS / FONTS, or "none yet, propose some"}}
- Real photos: {{PATHS, or "none yet, use placeholders"}}

## Page content (every concept covers these)
- Hero: name, one-line pitch, primary CTA ({{CTA, e.g. "Call to order" / "Find the truck"}})
- {{SECTION_2, e.g. Menu with prices}}
- {{SECTION_3, e.g. Hours + location / map}}
- {{SECTION_4, e.g. Catering / events}}
- Footer: phone, address, socials, hours
- Facts to use verbatim: {{PHONE, ADDRESS, HOURS, PRICES, HOST/PARTNER NAMES}}
- Do not invent facts. Where something is unknown, use an obvious placeholder.

## Concepts
Make {{2}} distinct directions, each a separate self-contained HTML file in `concepts/`:
1. {{CONCEPT_A_NAME}}: {{one-sentence art direction}}
2. {{CONCEPT_B_NAME}}: {{one-sentence art direction}}
They should differ in layout and personality, not just color. Each must be fully
responsive (looks right at 1280px and at 390px), have favicon + SEO/OG meta, hover and
focus states, and no em dashes in copy.

## Preview page (`concepts/index.html`)
- Sticky dark control bar: client logo + name + "CONCEPT PREVIEW" label on the left;
  two segmented toggles in the middle: DESIGN ({{concept names}}) and VIEW (Desktop / Mobile);
  an "OPEN FULL PAGE ↗" link on the right that opens the current concept in a new tab.
- Under the bar: a "DRAFT" notice strip ("These are draft concepts, photos are placeholders,
  final images still to come") and a caption "SHOWING {{CONCEPT}} · {{VIEW}}".
- Stage: each concept loads in an iframe rendered at its real logical width
  (desktop 1280px, mobile 390px) and scaled down with CSS transform to fit the window.
  - Desktop: browser chrome with three traffic-light dots and a fake URL bar ({{domain}}).
  - Mobile: dark phone bezel with large rounded corners, no browser chrome.
- Show the whole page, not a scrolled viewport: measure each iframe's scrollHeight and size
  the frame to it, re-measuring periodically while fonts/images settle, with fallback heights.
- Keep all concept iframes loaded so switching is instant; crossfade between them.
- Loading state until the active iframe is ready. Works on a phone (the bar wraps,
  the stage scales down).
- Pressed toggle uses the brand accent ({{ACCENT_HEX}}); aria-pressed on the buttons.

## Deploy hygiene
Keep `concepts/` out of the production deploy (add it to `.vercelignore`) and keep raw
client photos out of git. When I pick a concept, I'll ask you to promote it to the root
`index.html` as the live site.
```

## Short version (when the client brief is already in the conversation)

```text
Using the brief above, make {{N}} homepage concepts ({{names + one-line directions}}) as
separate HTML files in concepts/, then a concepts/index.html preview page like the Chicoco
one: sticky bar with DESIGN and VIEW (Desktop/Mobile) toggles and an "Open full page" link,
a DRAFT notice, and each concept in an iframe at 1280px (browser chrome) or 390px (phone
bezel), scaled to fit and sized to the full page height. Keep concepts/ out of the deploy.
```
