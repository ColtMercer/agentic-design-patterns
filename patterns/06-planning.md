# Ch. 6 — Planning

> Generate an explicit, machine-readable plan before executing — then monitor, replan, and adapt as needed.

[← Back to README](../README.md)

---

## What It Is

Planning separates the "thinking about what to do" phase from the "doing it" phase. The agent first generates a structured plan — an ordered sequence of steps with dependencies, conditions, and expected outputs — then hands it to an executor. If a step fails, the executor can trigger replanning rather than silently failing or hallucinating its way forward.

This is the difference between a chef who improvises at the stove (often fine for simple dishes, chaotic for a 12-course meal) and one who has a prep list and mise en place (reliable at scale).

---

## When to Use

- Tasks have multiple steps with dependencies between them
- Some steps can be parallelized if planned correctly up front
- You want to validate the approach before committing to expensive actions
- The task involves tool calls or external side effects that are hard to undo
- Multi-turn interactions where the agent needs to maintain a goal across many steps

---

## Key Implementation Insight

Store plans in a **machine-readable structure** (JSON with steps, conditions, expected outputs) rather than free-form text. Keep planning and execution as **separate phases** — the planner generates, the executor runs and monitors. Validate the plan before execution begins (is it coherent? are dependencies correct?). Build **replanning** into the executor: when a step fails or produces unexpected output, trigger a new planning cycle rather than continuing blindly. Combine with Parallelization to identify and run independent steps concurrently.

---

## Quick Checklist

- [ ] Plan is stored in machine-readable format (not free text)?
- [ ] Planning and execution are clearly separate phases?
- [ ] Plan validated before execution starts?
- [ ] Replanning triggered on step failure (not silent continuation)?
- [ ] Independent steps identified and parallelized where possible?
- [ ] Plan steps are atomic and individually verifiable?

---

## Related Patterns

- [Prompt Chaining](01-prompt-chaining.md) — a plan is executed as a chain
- [Reflection](04-reflection.md) — reflect on the plan before executing to catch issues early
- [Multi-Agent Collaboration](07-multi-agent.md) — planning assigns subtasks to the right agents
