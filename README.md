# Golden Data

**Make the complex obvious.**

Golden Data ships the AI feature that makes the next step in your app obvious — designed against your real users, evaluated against real failure modes, handed off as production code in your codebase. Two to three weeks.

Built for SaaS founders and CTOs adding AI features to data-heavy products: sales operations tools, ad tech platforms, analytics platforms, BI products, and the modern data stack.

**Live site:** [browningtons.github.io/golden-data](https://browningtons.github.io/golden-data/)

---

## How I work

This is the operating manual under the hood of every engagement.

### Principles

**Decisions first.** Every engagement starts with a real user decision the AI feature is supposed to support, and the metric that says whether it's working.

**Clarity over volume.** If a feature doesn't change how the user behaves, it's noise. One feature shipped well beats three half-shipped.

**Speed with quality.** Conclusive answers, eval coverage, latency budgets, cost caps, on-time delivery. Boring is the goal.

**Human-in-the-loop.** I draft. Your team reviews. Nothing ships without alignment.

**Reproducibility.** Every prompt, every eval golden example, every cost number lives in your repo. Results can be rerun.

**Low drama.** Clear scope, clear cadence, clear ownership.

### Engagement flow

User moment → Spec → Eval setup → Build → Latency/cost validation → Handoff

1. **User moment.** What's the user about to do? Where does an AI feature change the next step?
2. **Spec.** One feature. Decision-first. The shape (RAG, agent, retrieval+ranking, etc.) and the constraints (latency, cost, accuracy, scale).
3. **Eval setup.** 50–100 golden examples before any production code is written. Without this, you're shipping vibes.
4. **Build.** In your codebase, in your stack. Latency budget, cost cap, observability — built in, not bolted on.
5. **Latency/cost validation.** Verify against the budget you signed off on. Tune until it holds.
6. **Handoff.** Working feature. Eval harness. Cost monitor. A short doc explaining what was shipped and why.

The shape is a 2–3 week **Clarity Sprint**. Pricing on the intro call.

---

## Who's behind it

Paul Brown — currently leading sales operations at a social media ad tech platform. Background in analytics engineering, senior data analyst leadership, and BI strategy. Roles I've held or operated alongside: Staff/Principal Analytics Engineer, Senior/Staff Data Analyst, Product Analytics Manager, BI/Analytics Director, Fintech/Compliance Analytics.

The features I build for clients are the ones I see my own teams actually need. I'm credible in the spaces I work in: sales ops, ad tech, analytics tooling, BI, the modern data stack. Outside those, I'll tell you I'm not the right person.

---

## Signal — the weekly newsletter

[Signal](https://browningtons.github.io/golden-data/signal/) is a weekly read for SaaS founders and CTOs adding AI features to data-heavy products — and the senior analytics ICs and BI leaders who use those products every day.

- **Cadence:** Sunday morning, weekly.
- **Length:** 700–1,000 words.
- **Voice:** First-person practitioner. Specific. Technical. Anti-noise.
- **Structure:** Diagnostic lede → what's shipping this week → what I'd ship in your app this week → CTA.

### How it's automated

A scheduled task (`signal-weekly` in `~/.claude/scheduled-tasks/`) runs every Sunday at 7 AM local. It:

1. Fetches [`prompts/signal-prompt.md`](prompts/signal-prompt.md) (the source of truth for audience, voice, structure, quality bar).
2. Researches the past 7–14 days of AI feature signals via web search.
3. Writes the issue as `signal/YYYY-MM-DD.md` with frontmatter using the `issue` Jekyll layout.
4. Updates `signal/index.html` — adds the issue to the list, repoints the hero CTA.
5. Opens a PR. Paul reviews and merges manually.

---

## Repo structure

```
golden-data/
├── README.md                  ← you are here
├── _config.yml                ← Jekyll config (baseurl, excludes)
├── _layouts/
│   ├── default.html           ← head + nav + footer chrome
│   └── issue.html             ← extends default; wraps issue body + CTA card
├── index.html                 ← homepage (standalone HTML, copied as-is)
├── styles.css                 ← shared design system
├── assets/                    ← logo, favicons, case-study images
├── signal/                    ← weekly newsletter
│   ├── index.html             ← Signal landing page (uses default layout)
│   └── YYYY-MM-DD.md          ← weekly issues (use issue layout)
└── prompts/
    └── signal-prompt.md       ← the prompt the weekly task fetches
```

GitHub Pages serves from the repo root with Jekyll. The site is available at `/golden-data/` until a custom domain is wired up.

---

## Contact

Email: [thegoldendata@gmail.com](mailto:thegoldendata@gmail.com)
[Book a clarity call](https://calendar.app.google/nAaLqm8NWS2mXdT49)
