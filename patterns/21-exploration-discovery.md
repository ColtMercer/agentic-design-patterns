# Ch. 21 — Exploration and Discovery

> Let agents actively seek new information or strategies while managing uncertainty and risk.

[← Back to README](../README.md)

---

## What It Is

Exploration and Discovery covers the patterns that help agents go beyond known answers: curiosity-driven objectives, uncertainty-based querying, active learning, tree search, Monte Carlo exploration, and staged curricula. Rather than only exploiting what they already know, agents deliberately gather information and test options to reduce uncertainty.

---

## When to Use

- The agent faces unknowns and needs to gather more information
- Planning requires testing multiple future paths or strategies
- The system is learning from data collection over time
- Search or discovery quality matters more than immediate certainty
- There is value in asking better follow-up questions instead of guessing

---

## Key Implementation Insight

Balance **exploration vs. exploitation** explicitly. Use uncertainty estimates or information-gain heuristics to decide when to explore, and sandbox risky actions before they touch real systems. Log exploration trajectories so you can learn which paths were useful. In high-risk settings, conservative fallback policies and human oversight keep curiosity from becoming chaos.

---

## Quick Checklist

- [ ] Exploration budget defined explicitly?
- [ ] Uncertainty or information-gain estimate available?
- [ ] Risky exploration sandboxed before real execution?
- [ ] Exploration traces logged for offline analysis?
- [ ] Conservative fallback policy exists when uncertainty stays high?
- [ ] Human review added where exploratory actions could have serious consequences?

---

## Related Patterns

- [Planning](06-planning.md) — exploration can generate better plans by testing alternatives
- [Reasoning Techniques](17-reasoning-techniques.md) — structured search methods are a form of guided exploration
- [Learning and Adaptation](09-learning-adaptation.md) — exploration creates the data that future adaptation learns from
