# Ch. 1 — Prompt Chaining

> Decompose a complex task into an explicit sequence of focused LLM calls where each step's output feeds the next.

[← Back to README](../README.md)

---

## What It Is

Prompt Chaining breaks a complex request into a pipeline of smaller, focused prompts. Each step has a well-defined input and output, and the output of one step becomes the input to the next. You can insert deterministic logic, tool calls, or validation between LLM steps to keep the chain grounded and correct.

Think of it as the difference between asking one person to "write a research report from scratch" vs. having a researcher gather facts, a writer draft from those facts, and an editor review the draft — each role focused on one thing.

---

## When to Use

- The task requires multiple distinct reasoning steps (research → draft → edit)
- A single prompt produces inconsistent or low-quality results
- You need to inject external tool calls or database lookups between reasoning steps
- You want explicit, auditable intermediate outputs for debugging or compliance
- The task involves data transformation pipelines (extract → transform → summarize)

---

## Key Implementation Insight

Design each step with a strict **input/output contract** — preferably machine-readable (JSON schemas work well). Validate and sanitize outputs between steps before passing them forward. Avoid passing raw, unstructured LLM outputs directly into the next prompt. Frameworks like LangChain, LangGraph, and LCEL make chain construction and error-handling straightforward — use them rather than rolling your own.

---

## Quick Checklist

- [ ] Each step has a defined input schema and expected output format?
- [ ] Validation/sanitization applied between every step?
- [ ] Deterministic tools (calculators, DB queries, APIs) used where LLM reasoning isn't needed?
- [ ] Error handling defined at each link — what happens if a step fails?
- [ ] Intermediate outputs logged for debugging?
- [ ] Tested with malformed or unexpected intermediate outputs?

---

## Related Patterns

- [Planning](06-planning.md) — generates the step sequence before execution begins
- [Routing](02-routing.md) — dispatches each step to the right model or specialist
- [Parallelization](03-parallelization.md) — run independent steps concurrently to reduce latency
