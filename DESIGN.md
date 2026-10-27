# MonEscrow: design direction

## What this is

A seven-slide concept deck for MonEscrow, a milestone-escrow idea. It runs on a 16:9 stage in a browser, with keyboard and touch navigation, and it is a pitch artefact, not a product. Nothing here is a working escrow.

## Direction

A dark screening room with one lit panel. The deck is a black room (`#030304`), the stage is a slightly lifted black (`#09090b`), and the only light comes from the copy and four semantic accents. The reference is a title card in a documentary: high contrast, tight tracking, one idea per frame, nothing competing for the eye. Dark is a decision here, not a default: the deck is projected or screen-shared in a dim room, and a white stage would light the room instead of the idea.

The stage grid (`3.75cqw` rules at 1.8% white) stays because it reads as a measuring surface for milestones, which is what the product sells.

## Palette

Defined in the `:root` block of `index.html`.

| token | value | use |
|---|---|---|
| `--bg` | `#09090b` | stage ground |
| room | `#030304` | the deck behind the stage |
| `--surface` | `#18181b` | card and note surfaces |
| `--border` | `#27272a` | hairline dividers only, never a control boundary |
| `--text` | `#f4f4f5` | headings and body, 18.10:1 on `--bg` |
| `--muted` | `#a1a1aa` | lede, captions, HUD, 7.76:1 on `--bg`, 6.91:1 on `--surface` |
| `--purple` | `#836ef9` | eyebrow labels, focus accent, 5.27:1 on `--bg` |
| `--green` | `#34d399` | release and success states only, 10.35:1 |
| `--amber` | `#fbbf24` | challenge window, waiting states, 11.92:1 |
| `--red` | `#f87171` | objection and freeze states only, 7.19:1 |

`--border` sits at 1.34:1 against `--bg`, well under the 3:1 non-text threshold. It is used as a hairline inside a card whose surface already separates it, never as the only edge of a control, so it is not carrying state. Any new interactive control needs a real 3:1 boundary and a focus ring.

## Type

- Everything: the system sans stack (`Inter, ui-sans-serif, system-ui`). A deck gets screen-shared through whatever the room's machine has; a webfont that fails to load would reflow every slide.
- `h1`: `clamp(42px, 5.1cqw, 98px)`, tracking `-.055em`, `max-width: 12ch`. Big and tight, one sentence per frame.
- `h2`: `clamp(34px, 3.45cqw, 66px)`, tracking `-.045em`.
- `.lede`: `clamp(18px, 1.55cqw, 30px)`.
- Eyebrows: `1.05cqw`, uppercase, `letter-spacing: .13em`, `--purple`.
- Nothing below 12px once the stage is at phone width; the `clamp()` floors are what hold that.

## Dial

```
ENERGY  4   /* full-bleed statement: one slide at a time, nothing else on screen */
RHYTHM  3   /* seven different compositions, none repeating the previous */
MOTION  2   /* per-step reveal plus a slide transition, both suppressed under reduced motion */
```

## Motion

Each `[data-step]` element fades, rises `1.3cqw` and un-blurs as you advance; slides cross-fade with a small `translateX`. Both exist to control the order in which the argument lands, which is what a deck is for. `@media (prefers-reduced-motion: reduce)` collapses every duration to `.001ms`, so the deck still steps but nothing travels.

## Allowed

- A near-black stage with a lifted black panel, because the room is dark and the slide is the light.
- One accent per state, and each accent names a state in the product (green release, amber wait, red objection). No accent is decoration.
- A 1.8%-white grid on the stage, as the milestone measuring surface.
- Speaker notes toggled with `N`, hidden from the projector by default.
- The blurred reveal on each step.

## Forbidden

- Fabricated traction: no user counts, no escrow volume, no logos, no testimonials, no "trusted by". The deck sells a mechanism, and it says so.
- Any claim that the escrow exists. There is no backend, no contract, no deployment.
- A gradient orb, glow, or mesh behind the hero. The one radial gradient in `--deck` is the room light, and it stays under 12% alpha.
- An eyebrow that repeats the headline it sits above.
- Em dash in shipped copy.
- Animation not covered by the reduced-motion block.
- Hardcoded `px` lengths inside the stage: every length is a `cqw` fraction or a `clamp()` with a `cqw` middle term.

## Where it lives

`index.html`: the `:root` custom properties at the top of the single `<style>` block, then per-component rules that only consume those properties.
