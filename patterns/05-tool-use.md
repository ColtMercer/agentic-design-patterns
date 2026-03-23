# Ch. 5 — Tool Use

> Give your agent deterministic external capabilities — APIs, search, databases, calculators — instead of asking it to invent answers.

[← Back to README](../README.md)

---

## What It Is

Tool Use augments an LLM with the ability to call external, deterministic systems: web search, database queries, calculators, code executors, APIs, file systems. The agent decides when a tool is needed, calls it with the right inputs, and incorporates the result into its reasoning. This is how you ground agents in reality instead of relying on (often wrong) parametric knowledge.

---

## When to Use

- You need reliable, up-to-date external data (current prices, live search, recent events)
- The task requires side-effecting actions (send email, create record, book appointment)
- Precise computation is needed (use a calculator, not LLM arithmetic)
- Domain-specific functionality exists as an API and shouldn't be reimplemented in prompts
- You want to reduce hallucinations by grounding responses in tool outputs

---

## Key Implementation Insight

Wrap every tool with a **strict typed I/O contract** — the LLM needs clear descriptions of what each tool does, what inputs it expects, and what it returns. Tool descriptions are part of your prompt engineering: vague descriptions lead to wrong tool selection. Implement **retries and fallbacks** for each tool, and **sandboxing** for side-effecting tools (you don't want to send 50 emails because the agent looped). Log all tool calls — they're your best debugging signal.

---

## Quick Checklist

- [ ] Every tool has a strict typed input/output schema?
- [ ] Tool descriptions clear enough for the LLM to select correctly?
- [ ] Retries and fallbacks defined per tool?
- [ ] Side-effecting tools sandboxed or require confirmation?
- [ ] Tool call logs retained for debugging and auditing?
- [ ] Invalid tool inputs handled gracefully (don't crash the agent)?

---

## Related Patterns

- [Planning](06-planning.md) — plans are often sequences of tool calls
- [Model Context Protocol (MCP)](10-mcp.md) — standardizes how tools are exposed and discovered
- [Exception Handling](12-exception-handling.md) — essential for handling tool call failures gracefully
