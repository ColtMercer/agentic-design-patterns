# Ch. 4 — Reflection

> Add a critic/reviewer loop so the agent evaluates and iteratively improves its own outputs.

[← Back to README](../README.md)

---

## What It Is

Reflection is a feedback loop pattern where an agent generates an output (Producer), then a second pass critiques it (Critic), and the process repeats until quality criteria are met or a stop condition is hit. The Producer and Critic can be the same model with different prompts, or separate specialized models.

This mirrors how a software team does code review — the author writes, the reviewer critiques, the author revises, repeat.

---

## When to Use

- Output quality, factual correctness, or constraint adherence is critical
- Code generation that needs to compile and pass tests
- Long-form content that needs to meet specific criteria (tone, structure, accuracy)
- Planning where plans need to be validated against constraints before execution
- Any task where "first draft" quality is consistently insufficient

---

## Key Implementation Insight

**Separate Producer and Critic roles clearly** in your prompts — the Critic should be given explicit evaluation criteria, not a vague "is this good?" instruction. Define a concrete **stopping condition** (max N iterations, or a specific signal like `APPROVED`) to prevent infinite loops. Track conversation state across iterations so context isn't lost. Be deliberate about the latency and cost trade-off — each iteration adds 1–2x the original cost and latency.

---

## Quick Checklist

- [ ] Producer and Critic prompts are clearly separated with distinct roles?
- [ ] Critic has explicit, measurable evaluation criteria (not just "improve this")?
- [ ] Stopping condition defined — max iterations or approval signal?
- [ ] State and context preserved across reflection iterations?
- [ ] Latency and token budget accounted for in production SLAs?
- [ ] Critic output is structured enough to drive targeted revisions?

---

## Related Patterns

- [Prompt Chaining](01-prompt-chaining.md) — reflection is often implemented as a specialized chain
- [Planning](06-planning.md) — reflect on a plan before executing it
- [Human-in-the-Loop](13-human-in-the-loop.md) — replace or augment the Critic with a human reviewer for high-stakes output
