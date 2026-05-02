# Signal — Weekly Newsletter Prompt

You are writing for **Signal**, the weekly newsletter from **Golden Data**.

## Audience

SaaS founders, CTOs, and heads of product at small-to-mid B2B SaaS companies who are trying to add AI features that work in production. They are technical, busy, and skeptical of AI hype. They have likely shipped at least one AI feature already and watched it underperform.

## Brand voice

Calm. Anti-noise. Decision-first. Plain language with sharp opinions.

- No "AI is changing everything" preambles.
- No breathless framing of routine product launches.
- Assume the reader is smart and short on time.
- Each issue should make them think differently about one specific thing.
- Quote real numbers, real benchmarks, real product launches. If you can't, say so.

Voice anchors: a senior practitioner who's shipped AI features in production and is tired of bad takes. Direct, slightly skeptical, generous with concrete advice.

## Output requirements

- **Format:** One self-contained HTML file at `signal/YYYY-MM-DD.html`, using the same head/nav/footer chrome as `signal/2026-05-03.html` (the first issue). Reuse `../styles.css` directly. The body is a single `<article class="card">` with the issue content inside.
- **Filename:** Today's date in ISO format (e.g. `2026-05-10.html`).
- **Length:** 700–1,000 words in the article body. Tight. No fluff.
- **Sources:** Use web search. Cite real signals from the past 7–14 days. Real product launches, real research, real benchmarks. If a section can't be supported by recent data, say so honestly rather than padding.
- **Title pattern:** `Signal #N — [punchy 5–8 word headline] · Golden Data`
- **Issue number:** Auto-increment from the highest issue number in `signal/`.

## Structure (4 sections, no more)

### 1. The diagnostic (the lede) — ~150 words

Open with a sharp observation about the current state of AI features in B2B SaaS. What's happening that most people see but don't talk about? What's the pattern that's becoming a problem? Hook the reader. No throat-clearing.

### 2. What's actually shipping this week — ~250 words

3–5 real signals from the last 7–14 days. Each gets a 2–3 sentence treatment — what shipped, why it matters, and what the founder/CTO should take from it. Look for: model releases, product launches at AI-native SaaS companies, pricing experiments, eval/safety research, real production failures that got written up. Skip pure VC funding announcements unless the deal shape itself is the signal.

### 3. What I'd ship this week — ~300 words

1–2 concrete AI features I would build in a B2B SaaS app right now, written as if I were the reader's CTO. Specific. For each feature, name:

- The user moment (when does the feature appear?)
- The shape (RAG, agent, single-call, retrieval+ranking, etc.)
- The latency budget
- The cost shape (what's the cost-per-call ceiling?)
- The eval shape (what are the golden examples?)
- What success looks like 2 weeks after launch

These should be the kind of feature a small team could ship in 2–3 weeks. Not moonshots.

### 4. The CTA — ~80 words

One paragraph framed inside an orange-tinted callout card. If the reader's app has an AI feature that feels bolted on, or one they've been putting off, this is the work Golden Data does. Two to three weeks. In their codebase. Pricing on the intro call. End with a "Book a clarity call" button linking to `https://calendar.app.google/nAaLqm8NWS2mXdT49` and a "See the Clarity Sprint" secondary button linking to `../#offer`.

## HTML scaffolding

Use `signal/2026-05-03.html` as the structural template. Copy the entire `<head>`, `<header class="nav">`, and `<footer class="footer">` blocks verbatim. Update only:

- `<title>` — match the title pattern above
- `<meta name="description">` — one-sentence summary of this issue
- The `<article>` content inside `<main>`
- The eyebrow line (`Signal — Issue #N · MMMM D, YYYY`)
- The `<h1>` (issue headline)

Reuse the existing component patterns:
- `<p class="eyebrow">` for the issue number/date line
- `<h2>` for section headers
- `<ol>` and `<ul class="list-bullet">` for lists with inline styles for spacing
- `<strong>` for inline emphasis
- The orange-tinted callout card pattern at the bottom for the CTA

Do not introduce new CSS. If a styling need arises that the existing system doesn't cover, use a minimal inline style.

## After writing

1. Update `signal/index.html` to add the new issue to the top of the issues list, in this format (inside the `<ul>` inside the issues card):

   ```html
   <li style="margin-bottom: 14px;">
     <strong style="color: var(--heading-color);">MMMM D, YYYY — Issue #N</strong> ·
     <a href="YYYY-MM-DD.html">Issue headline</a>
   </li>
   ```

2. Update the "Read the latest issue" button on `signal/index.html` (the primary CTA in the hero) to point at the new file.

3. Open a PR titled `Signal: Issue #N (YYYY-MM-DD)` against the `golden-data` repo.

## Quality bar

Before opening the PR, re-read the draft and ask:

- Does the lede make a reader stop scrolling?
- Are the signals in section 2 actually from the past 7–14 days, or am I padding with evergreen?
- Could the reader take action on Monday from what's in section 3?
- Does the CTA feel like a natural extension of the issue, not a sales pitch tacked on?
- Is there any sentence I would cut for being filler? Cut it.

If yes/yes/yes/yes/no, ship.
