# rahman-blitz

A pitch deck for MonEscrow, built as a stepped HTML presentation with a 3D phone demo.

## Stack

- One `index.html` with inline CSS and JS, plus a Three.js scene for the phone demo
- Node.js only for the helper scripts in `scripts/`

## Commands

| what | command |
|---|---|
| serve | open `index.html` in a browser; `scripts/` has a local server |
| env check | `npm run env:check` |

There is no build step and no test suite.

## Layout

- `index.html` — the deck. Each step is a panel; navigation advances one at a time.
- `logo.svg`, `logo-mark.svg`, `three-phone-demo.png` — static assets
- `DESIGN.md` — palette with computed ratios and the dial line

## Copy rules

This deck's subject line is `Silence pays. Objection pauses.` That is intentional and specific — do not soften it into generic pitch language. The same applies to every headline in the deck: each one makes a claim the next slide has to pay off. If a slide has nothing real to say, cut the slide.

No fabricated traction: no invented user counts, revenue, partnership logos or "backed by" claims.

## Design direction

`DESIGN.md` is the source of truth.

## Guardrails

- Every interactive element has a real behaviour or it is removed.
- Arrow keys advance the deck; they must not fight any other control.
- The 3D phone demo must degrade to a static image when WebGL is unavailable.
- Never delete or overwrite without an explicit instruction from Rahman.

## Verify a change

Open `index.html`, advance through every step with the keyboard alone, and confirm the phone demo renders or falls back cleanly.
