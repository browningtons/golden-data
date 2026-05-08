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

## The newsletters

Two weekly letters share this repo, the same Jekyll layout, and the same Notion-backed editorial pipeline.

[**Signal**](https://browningtons.github.io/golden-data/signal/) is for SaaS founders and CTOs adding AI features to data-heavy products — and the senior analytics ICs and BI leaders who use those products every day.

- **Voice cast:** Michael Lewis (narrative) layered on Paul-as-practitioner.
- **Structure:** Diagnostic lede → what's shipping this week → what I'd ship in your app this week → CTA.

[**Movement**](https://browningtons.github.io/golden-data/movement/) is for senior analytics ICs and leaders actively managing their careers.

- **Voice cast:** Sam Harris (dry) primary, Hitchens supporting.
- **Structure:** Diagnostic lede → what's actually moving in the market → what I'd do this week → CTA.

Both letters: 700–1,000 words, no fluff, weekly cadence.

### How they're automated

A scheduled task fetches the relevant prompt ([`prompts/signal-prompt.md`](prompts/signal-prompt.md) or [`prompts/movement-prompt.md`](prompts/movement-prompt.md)) and runs the **4-phase routine** documented inside it:

1. **Publish.** Sweep the unified Notion DB for any rows where `Newsletter = X` and `Status = Approved`. Commit each to `signal/` or `movement/` and push to `main` (no PR for content drafts).
2. **Learn.** Read the 5 most recent Approved/Published rows. Highest-weight signal is the `Note to next draft` field; supporting signals are `Editorial Notes`, the `Edited Version` diff, `Voice Pass`, `Voice Score`, and `Reception`.
3. **Draft.** Web search for live signals from the past 7–14 days. Apply structure, voice, and topic priorities, weighted by what was learned.
4. **Write to Notion.** Create a new row in the GD Newsletter DB with `Status = Draft` and the full markdown in the page body. Paul reviews and approves in Notion; the next week's run publishes it.

The Notion DB is the source of truth for content and feedback. The repo is the publishing target. Approval moves a row through `Draft → In Review → Approved → Published → Archived`; the orthogonal `Voice Pass` field (`Off / Mixed / On`) and `Voice Score` (1–10) capture voice-cast quality independent of lifecycle.

---

## Repo structure

```
golden-data/
├── README.md                   ← you are here
├── _config.yml                 ← Jekyll config (baseurl, excludes)
├── _layouts/
│   ├── default.html            ← head + nav + footer chrome
│   └── issue.html              ← extends default; wraps issue body + CTA card
├── index.html                  ← homepage (standalone HTML, copied as-is)
├── styles.css                  ← shared design system
├── assets/                     ← logo, favicons, case-study images
├── signal/                     ← Signal newsletter
│   ├── index.html              ← Signal landing page (uses default layout)
│   └── YYYY-MM-DD.md           ← weekly issues (use issue layout)
├── movement/                   ← Movement newsletter
│   ├── index.html              ← Movement landing page
│   └── YYYY-MM-DD.md           ← weekly issues
└── prompts/
    ├── signal-prompt.md        ← Signal routine + voice + structure
    └── movement-prompt.md      ← Movement routine + voice + structure
```

GitHub Pages serves from the repo root with Jekyll. The site is available at `/golden-data/` until a custom domain is wired up.

---

## Contact

- Email: [thegoldendata@gmail.com](mailto:thegoldendata@gmail.com)
- [Book a clarity call](https://calendar.app.google/nAaLqm8NWS2mXdT49)
