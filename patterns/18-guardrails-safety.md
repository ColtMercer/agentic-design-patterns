# Ch. 18 — Guardrails / Safety Patterns

> Constrain agent behavior with layered safeguards before, during, and after generation or tool use.

[← Back to README](../README.md)

---

## What It Is

Guardrails are the safety architecture of an agent system. They include input sanitization, schema validation, policy-enforcing models, runtime restrictions, output filters, and human escalation paths. The point is defense in depth: no one safeguard is enough, especially once agents can call tools or take actions.

---

## When to Use

- Any production or semi-autonomous agent
- User-facing systems with safety, legal, or brand risk
- Agents with tool access or side effects
- Regulated workflows requiring policy enforcement and auditability
- Systems where prompt injection or unsafe tool calls are realistic threats

---

## Key Implementation Insight

Build **layered safety**, not a single classifier. Use lightweight checks up front, a mid-latency policy layer where needed, and post-generation filters plus human review for high-risk outputs. Log every safety decision for auditability. Test guardrails in shadow mode or canary mode before turning them into hard blockers.

---

## Quick Checklist

- [ ] Input sanitization applied at the entry point?
- [ ] Policy checks run before sensitive generation or tool use?
- [ ] Output filters in place for unsafe or non-compliant content?
- [ ] High-risk cases escalated to humans?
- [ ] Safety decisions logged with reasons?
- [ ] New rules tested in shadow/canary mode before hard enforcement?

---

## Related Patterns

- [Human-in-the-Loop](13-human-in-the-loop.md) — humans handle the exceptions guardrails surface
- [Exception Handling](12-exception-handling.md) — safety violations are another class of recoverable failure
- [Evaluation and Monitoring](19-evaluation-monitoring.md) — guardrails need continuous measurement and tuning
