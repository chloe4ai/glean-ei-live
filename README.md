# Glean · Enterprise Intelligence — static build

The deployable build of
**[glean-ei-fullstack](https://github.com/chloe4ai/glean-ei-fullstack)**, the full-stack
prototype built for the **Glean · Product Manager, Enterprise Intelligence** interview.

This repository holds only the compiled output: `index.html`, a hashed JS/CSS bundle under
`assets/`, and a `404.html` so client-side routes survive a deep link on static hosting.
**The source lives in the other repo** — read, run and change it there.

```bash
python3 -m http.server 4793 --directory .
```

## Why a second repository

The full-stack version runs a Node + Express backend: toggling a signal recomputes the
affected insights' composite confidence *on the server*, calibration feedback persists to
disk, and the agent streams its work over Server-Sent Events. None of that survives on
static hosting.

Rather than water the prototype down to something a static host could serve, the app was
given a build mode that swaps the API client for a client-side mock and the router for a
`HashRouter`. Every interaction behaves as it does against the real backend; only the
persistence boundary moves. That way the demo anyone can open in a browser and the app that
demonstrates real server-side recomputation are the same product, not two divergent ones.

The tradeoff worth naming: nothing here persists across a reload, and the confidence
recomputation you see is running in the browser rather than being defended by a server. If
that distinction is the interesting part — and for this prototype it is — run the full-stack
repo instead.

## What it is

A proactive intelligence surface on top of Glean's enterprise context layer. Instead of
searching, a leader is pushed what changed, where value is being created or lost, and where
to act — with provenance, calibrated confidence, a feedback loop, and human-in-the-loop
agents. The same engine re-skins across departments (Engineering → Revenue) through the
persona switch.

Styled to Glean's real design tokens: primary `#343BED`, fully-rounded pill buttons, large
light-weight headings with tight letter-spacing, monospace eyebrows, Switzer + Space Mono.

## Related

- [glean-ei-fullstack](https://github.com/chloe4ai/glean-ei-fullstack) — the source, with the
  real backend
- [glean-delivery-intelligence](https://github.com/chloe4ai/glean-delivery-intelligence) —
  the same thesis as a single-file prototype, with the signal catalog argued at more length
- [glean-compass-v2](https://github.com/chloe4ai/glean-compass-v2) — one narrow detector from
  the same family
