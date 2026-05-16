# Field Guide — Golden Data

> **The math is the credibility. The tone is the relief.**

This site inherits Paul Brown's portable design system. See the canonical Field Guide in [debt-snowball-dolphin/DESIGN.md](https://github.com/browningtons/debt-snowball-dolphin/blob/main/DESIGN.md) for the system in full. This doc is the per-app surface: palette, persona, three questions, hero outcome.

**Stack note.** Golden Data is a Jekyll + plain HTML/CSS site (GitHub Pages), not a React/Tailwind/shadcn app. The spine *principles* (tokens, state coverage, light + dark, accessibility floor) apply. The spine *implementation rules* that assume React (`theme.ts`, Tailwind v4 `@theme inline`, shadcn aliases, Lucide React, `ThemeProvider`) are N/A here — the equivalents live in [`styles.css`](styles.css).

---

## The Five Principles

These hold across every app in the portfolio. The palette and persona change. The principles do not.

1. **Lead with relief before education.** Every landing screen states the outcome first ("you are not stuck", "you have a path"). Education comes only after the user can breathe.
   - _Surface translation:_ a CTO landing here is tired of AI theater. The hero says "make the complex obvious" — relief is intellectual ("this person gets it"), not emotional.
2. **One question per screen.** A screen earns its place by answering exactly one of: _what is my first win?_ · _what do I do next?_ · _how do I keep this alive?_
   - _Surface translation:_ for a consulting site, the three questions are recast (see below). Same constraint: one question per section.
3. **The math is credibility. The tone is relief.** Charts, numbers, dates — all true and load-bearing. Voice — warm, plainspoken, never preachy. Neither replaces the other.
   - _Surface translation:_ "Eval-first. Latency budget. Cost cap. 2–3 weeks." is the math. The dry, anti-fluff Paul-as-operator voice is the tone.
4. **Estimates first, real numbers next.** Don't gate the first useful answer behind perfect data. Let the user start rough and tighten over time.
   - _Surface translation:_ N/A — no user-entered data on this surface. Principle is inherited for any future app-surface added to this repo.
5. **Private by default.** Local-first storage. Sharing is opt-in and progress-shaped, never "I owe $X" disclosure.
   - _Surface translation:_ N/A — no user data captured. Principle is inherited for the same reason.

---

## This App

| | |
|---|---|
| **Domain** | AI-feature consulting for SaaS founders and CTOs in data-heavy products (sales ops, ad tech, analytics, BI, modern data stack). |
| **Persona** | **Paul-as-operator**, with **Patrick McKenzie** as silent influence — precise, plainspoken, financial-blog cadence, dry footnotes, anti-theater. |
| **Primary** | `#0F3D57` (Pacific Deep Blue — authority, research-publication blue) |
| **Accent** | `#F04A00` (International Orange — warning-flag orange, used for primary CTAs and emphasis) |
| **Interaction** | `#2CB6C0` (Fog Teal — links, pills, data-viz accent) |
| **Background** | `#F8FAFC` (Paper — cool-neutral near-white; see Decision Log for why this overrides the spine's warm-off-white default) |
| **Reference vibes** | Patrick McKenzie / Bits about Money (operator voice, dry precision) · Stripe Press (restrained, content-forward) · FT Weekend / Pacific Standard (research-publication typography and palette) |
| **Hero outcome** | _"An AI feature shipped in production, in your codebase, in 2–3 weeks."_ |
| **Three questions** | _Have they actually done this?_ · _What's the deliverable, concretely?_ · _What does it cost me to find out?_ |
| **What makes it sing** | The reader is treated as a peer ("I won't waste your time"), not a lead. "Boring is the goal." "No chatbot in the corner." |
| **Tradeoffs locked in** | Static Jekyll site, no JS framework. No analytics. No live chat. CTA is email — friction is the filter. |
| **Status** | Tier 4 shipped — tokens, typography, full 5-state component coverage, focus rings, semantic status tokens, hand-tuned dark mode with persisted toggle. The full spine. |

---

## Tokens

Defined in [`styles.css`](styles.css) `:root` block. Consumed via CSS variables.

| Token | Current value | Spine slot | Notes |
|---|---|---|---|
| `--paper` | `#F8FAFC` | `--background` | Cool-neutral override of the spine's warm-off-white. See Decision Log. |
| `--card-bg` | `#FFFFFF` | `--surface-raised` | Pure white card surface — intentional per-app override; printed-page feel for the operator/research register (Stripe Press does the same). |
| `--blue` | `#0F3D57` | `--primary` | Pacific Deep Blue. Passes "no generic blue" — has conviction. |
| `--orange` | `#F04A00` | `--accent` | International Orange. Warm, decisive CTA. |
| `--teal` | `#2CB6C0` | _no exact spine slot_ | "Interaction color" — links, pills, data-viz accent, and aliased to `--focus`. |
| `--ink` | `#0F172A` | `--text` | Dark charcoal, not pure black. ✓ |
| `--muted` | `rgba(15,23,42,0.72)` | `--text-muted` | ✓ |
| `--success` | `#2D6A4F` | `--success` | Warm forest, not Slack green. ✓ |
| `--warning` | `#A8541C` | `--warning` | Sienna, not yellow. ✓ |
| `--error` | `#9F2D2D` | `--error` | Brick red. ✓ |
| `--focus` | `var(--teal)` | `--focus` | Aliased to Fog Teal — already the interaction color; pops against orange + blue without competing. ✓ |

Soft variants defined and consumed throughout: `--orange-soft`, `--blue-soft`, `--blue-border`, `--teal-soft`, `--teal-halo` (focus halo), plus `--success-soft` / `--warning-soft` / `--error-soft`. Inline `rgba()` literals in components have been consolidated to these tokens.

---

## Typography

The spine prescribes Satoshi / Geist Sans / Geist Mono. This site uses **Geist Sans** (body + headings) and **Geist Mono** (numeric/code). Satoshi is skipped — Geist Sans with `letter-spacing: -0.02em` lands the same operator/research register without a third font load.

| Role | Family | Used for |
|---|---|---|
| Body + heading | **Geist Sans** (`var(--font-sans)`) | All text. Variable WOFF2, weights 100–900. |
| Numeric / mono | **Geist Mono** (`var(--font-mono)`) | `.step-num` step badges; any future money / dates / counts. |

Self-hosted in [`assets/fonts/`](assets/fonts) as variable WOFF2 (Geist 28KB + Geist Mono 31KB, latin subset). Loaded via `@font-face` with `font-display: swap`. No CDN dependency.

Type scale used (informal):

| Use | Size | CSS source |
|---|---|---|
| Hero h1 | `clamp(34px, 4vw, 52px)` | [`styles.css:66`](styles.css:66) |
| Section h2 | `24px` | [`styles.css:71`](styles.css:71) |
| Card h3 | `18px` | [`styles.css:79`](styles.css:79) |
| Body | `15–16px` | various |
| Eyebrow / kicker | `13px` uppercase | [`styles.css:411`](styles.css:411) |
| Micro / caption | `11–13px` | various |

Closes to a six-step scale but not formalized. `display: 48` (spine's reserved size for primary outcomes) is unused — the hero clamp tops out at 52px which is in the same register.

---

## Visual Hierarchy

Hierarchy of attention on the landing page:

1. **Hero outcome** — "Make the complex obvious" + the subtitle (2–3 weeks, your codebase)
2. **Proof of credibility** — the "What you get" value card immediately right of the hero
3. **What I do next** — the three-tile process row (Spec / Build / Ship)
4. **The deliverable** — the Clarity Sprint offer card
5. **The receipts** — the Ogden case study (the only case study; chosen because the lens transfers)
6. **The CTA** — email, no form

Feels like _an operator's notebook with a CTA at the bottom_. Not _a deck_.

---

## Voice

This site is cast as **Paul-as-operator** with **Patrick McKenzie** as silent influence.

Notes on register:

| ✗ Avoid | ✓ Use |
|---|---|
| "Unlock the power of AI for your business" | "Ship an AI feature that makes the next step obvious" |
| "Transform your data with cutting-edge AI" | "Eval-first. Latency budget. Cost cap. Boring is the goal." |
| "Schedule a free consultation today!" | "Email me." |
| "Our AI solutions empower teams..." | "I draft. Your team reviews. Nothing ships without alignment." |
| "World-class expertise in..." | "I'll tell you if I'm not the right person." |

The newsletter voices are cast separately and live in their respective prompts:
- **Signal** — Michael Lewis (narrative) layered on Paul-as-practitioner. See [`prompts/signal-prompt.md`](prompts/signal-prompt.md).
- **Crafting** — Reynolds-meets-Bateman. Reynolds for the fourth-wall winks; Bateman for the dry deadpan. See [`prompts/crafting-prompt.md`](prompts/crafting-prompt.md).

The site's voice (this doc) and the newsletter voices coexist by audience: site = front-door, newsletters = sustained practitioner notes.

---

## Spine Rules (inherited)

The following come from the canonical Field Guide and are not relitigated here. See [debt-snowball-dolphin/DESIGN.md](https://github.com/browningtons/debt-snowball-dolphin/blob/main/DESIGN.md) for the full text:

- **Spacing.** Multiples of 4 or 8. No nested cards.
- **State coverage.** Buttons define 5 states (default, hover, active, disabled, focus); inputs define 5 (default, hover, focus, disabled, error). Focus rings always visible. ✅ _Shipped Tier 3 — see [`styles.css`](styles.css)._
- **Light + dark.** Hand-tuned, never mechanically inverted. ⚠️ _Gap — dark mode not wired. See Tier 4._
- **Accessibility floor.** WCAG AA contrast, no color-alone status, action-oriented button labels. ✅ _Focus rings wired via `:focus-visible` on all tabbable elements; status colors are not color-alone (paired with copy/icons by convention)._

**N/A on this stack** (Jekyll + plain CSS):
- shadcn alias mapping
- Tailwind v4 `@theme inline`
- Lucide React for icons (this site uses inline SVGs in HTML, which is fine)
- `ThemeProvider` / `useTheme` (a one-line `data-theme` toggle on `<html>` is the Jekyll equivalent and is the path forward if Tier 4 ships)

---

## Tier Menu (pending work)

All four tiers shipped. The spine is fully implemented for this stack.

| Tier | Scope | Why it shipped |
|---|---|---|
| ~~**Tier 1 — Tokens**~~ | ✅ Pre-existing. Palette + semantic roles defined in `:root`. | Was already in place when the field guide was first drafted. |
| ~~**Tier 2 — Typography**~~ | ✅ Shipped 2026-05-11. Geist Sans + Geist Mono self-hosted in [`assets/fonts/`](assets/fonts); six-step scale exposed as `--text-*` tokens in `:root`. | The biggest visual lift for a content site — tightens the operator/research register. |
| ~~**Tier 3 — Components & a11y**~~ | ✅ Shipped 2026-05-11. Buttons: default/hover/active/disabled/focus. Inputs: default/hover/focus/disabled/error (base ruleset, no inputs on the surface today). `--focus` aliased to Fog Teal; `:focus-visible` ring on every tabbable element. Semantic `--success` / `--warning` / `--error` tokens added with soft variants. Inline `rgba()` consolidated into soft-tint tokens. Pure-white `--card-bg` documented as intentional. | Closes the accessibility floor and the state-coverage spine rule. |
| ~~**Tier 4 — Dark mode**~~ | ✅ Shipped 2026-05-11. `[data-theme="dark"]` overrides in [`styles.css`](styles.css) (cool blue-charcoal palette, lifted Pacific Blue + International Orange for legibility). Pre-paint script in `<head>` reads `localStorage['gd-theme']` (falling back to `prefers-color-scheme`). Header toggle persists user choice. All dark rules confined to one block — light mode unchanged. | Useful for newsletter long-form reading. Honors system preference by default. |

The field guide is complete for this surface. The next move is consumption — every new page should pull from these tokens, not introduce new hex values.

---

## Per-App Components

Patterns specific to this surface, not part of the spine.

### Newsletter cluster (nav)

A grouped pill in the primary nav that contains both newsletters (Signal · Crafting) with a small accent-colored eyebrow badge reading "NEWSLETTER." Visually separates the publication arm of the site from the consulting nav items (What I do / Clarity Sprint / Proof / About / Contact).

- **Where:** [`_layouts/default.html`](_layouts/default.html), [`index.html`](index.html) — nav region
- **Markup:** `<span class="nav-newsletters">` wrapping a `.nav-newsletters-label` (the eyebrow badge), two `<a>` links, and a `·` divider
- **Styles:** [`styles.css`](styles.css) — `.nav-newsletters` (orange-bordered pill on `--orange-soft`), `.nav-newsletters-label` (solid `--orange` badge), `.nav-newsletters-divider` (`--muted` middle dot)
- **Hidden on mobile** — the rest of `.navlinks` is hidden under 900px; the cluster follows the same rule.
- **Why a cluster rather than two more nav items:** Signal and Crafting are sibling letters from the same studio — they should read as one editorial body, not two separate menu entries competing with Clarity Sprint. The eyebrow badge labels the function ("Newsletter") so the names can stay clean.

---

## Decision Log

| Date | Decision | Rationale |
|---|---|---|
| 2026-05-11 | Cast persona as Paul-as-operator + Patrick McKenzie silent influence | Site's existing copy ("Eval-first. Boring is the goal. No chatbot in the corner.") was already in this register. Codifies what shipped. |
| 2026-05-11 | Primary `#0F3D57` (Pacific Deep Blue) | Research-publication blue. Passes "no generic blue" — has conviction. Pairs with International Orange for the operator/financial-research vibe (FT, Bits about Money). |
| 2026-05-11 | Accent `#F04A00` (International Orange) | Warning-flag orange, not VC-pitch orange. Decisive CTA color. Saturated enough to carry the "watch this" weight without feeling promotional. |
| 2026-05-11 | Background `#F8FAFC` overrides the spine's warm-off-white default | This is a research/operator surface for CTOs, not a financial-stress surface. Cool-neutral white reads correctly for the reference vibes (Stripe Press / Patrick McKenzie / FT). Warm off-white would push toward "lifestyle blog." Spine principle preserved, hex value adapted to the persona. |
| 2026-05-11 | Skip React-stack spine rules (shadcn, Tailwind v4 `@theme inline`, Lucide, `ThemeProvider`) | The repo is Jekyll + plain CSS. Spine *principles* port; *implementation rules* would be cargo. |
| 2026-05-11 | Tier 2 — Adopt Geist Sans + Geist Mono, skip Satoshi | Geist Sans with `letter-spacing: -0.02em` lands the operator/research register without a third font load. Self-hosted variable WOFF2 (latin subset, ~60KB total). |
| 2026-05-11 | Tier 3 — `--focus` aliased to `--teal` (Fog Teal) | Already the interaction color; pops against the orange CTA and blue text without introducing a fourth color. Spine asks for "visible + calm, usually a lighter primary" — Fog Teal lands the same brief. |
| 2026-05-11 | Tier 3 — Keep `--card-bg` pure white as a per-app override | Operator/research register (Stripe Press, FT) reads correctly on pure-white card surfaces. Warm-tint cards would push toward "lifestyle blog." Spine rule preserved on body background (`--paper`); card override documented. |
| 2026-05-11 | Tier 3 — Button focus uses `box-shadow` halo; everything else uses `outline` | Outline on a rounded button clips visibly at the corners; `box-shadow: 0 0 0 3px var(--teal-halo)` wraps cleanly. All other tabbables use the modern accessible default of `outline: 2px solid var(--focus); outline-offset: 2px`. |
| 2026-05-11 | Tier 4 — Cool blue-charcoal dark background (`#121821`), not warm sepia | Operator/research register (FT, HN dark) reads correctly on cool dark surfaces. Warm-amber dark mode would push toward "lifestyle blog dark" and break the persona. |
| 2026-05-11 | Tier 4 — Brand lifts: Pacific Blue `#0F3D57` → `#5BA4D1`, International Orange `#F04A00` → `#FF6610`, Fog Teal `#2CB6C0` → `#33C2CC` | Spine: "Primary shifts brighter for legibility on dark surfaces. Accent stays warm; lightens slightly." Lifted blue and teal lift legibility; orange shifts one hair brighter without losing the International Orange family identity. |
| 2026-05-11 | Tier 4 — Pre-paint script in `<head>` (not just `prefers-color-scheme`) | Inline `<script>` sets `data-theme` before the stylesheet loads, preventing a flash of wrong theme when a saved preference differs from the OS. Honors `prefers-color-scheme` only when no saved choice exists. |
| 2026-05-11 | Tier 4 — Confine all dark-mode rules to one block at the end of `styles.css` | Light mode is the canonical surface. Quarantining dark overrides means a future light-mode change can't accidentally regress dark, and reverting dark mode (if ever needed) is a clean diff. |
| 2026-05-15 | Add the Newsletter cluster pattern to the primary nav (Signal · Crafting under an orange "NEWSLETTER" badge) | Crafting page existed but wasn't linked. Pairing the two letters under one labeled pill reads as one editorial body and keeps the consulting nav items uncluttered. Per-app pattern, not spine. |
| 2026-05-15 | Introduce `--orange-hover` / `--orange-active` tokens in both `:root` and `.dark` blocks; delete the dark-mode `.btn-primary` component overrides | The hover/active hexes were the only state colors hardcoded outside the token block. Tokenizing means dark mode resolves through the same rule path as light, so eight lines of `[data-theme="dark"] .btn-primary` overrides could be removed. Reduces drift; light/dark stay in sync structurally. |
| 2026-05-15 | Correct DESIGN.md — newsletter is "Crafting" (Reynolds-meets-Bateman), not "Movement" (Sam Harris / Hitchens) | DESIGN.md was stale. The active prompt is [`prompts/crafting-prompt.md`](prompts/crafting-prompt.md); the voice cast there is Reynolds-meets-Bateman. Doc now matches source of truth. |
| 2026-05-15 | Delete unused `.shot-placeholder` ruleset | Confirmed dead — defined in `styles.css`, referenced in zero HTML. Held two Tailwind-slate hex literals (`#f1f5f9`, `#cbd5e1`). Removed rather than tokenized; deletion is the cheaper fix. |

---

_The math is the credibility. The tone is the relief. Build accordingly._
