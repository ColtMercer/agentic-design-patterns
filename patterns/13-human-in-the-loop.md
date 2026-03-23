# Ch. 13 — Human-in-the-Loop

> Combine automated agent actions with targeted human judgment at the points where it matters most.

[← Back to README](../README.md)

---

## What It Is

Human-in-the-Loop (HITL) is the pattern for inserting human judgment into an agent's workflow at defined decision points — not everywhere (that defeats the purpose of automation), but specifically where the stakes are high, confidence is low, or regulatory/audit requirements demand it. The agent handles the high-volume, low-risk work; humans handle the exceptions and edge cases.

Well-designed HITL feels like a smart assistant that handles 90% autonomously and only surfaces the 10% that genuinely needs a human.

---

## When to Use

- High-risk or irreversible actions (send a legal document, process a large financial transaction, delete data)
- Low-confidence agent outputs where the model knows it's uncertain
- Regulated domains (healthcare, finance, legal) where human sign-off is legally required
- Content moderation or approval workflows
- As part of a learning loop — human corrections generate training signal

---

## Key Implementation Insight

Define **explicit escalation triggers** — don't make humans review everything. Trigger review on: confidence score below threshold, specific action types (irreversible, high-value), anomaly detection, or explicit uncertainty signals from the agent. **Minimize friction** for reviewers: pre-fill context, batch similar reviews together, provide one-click approve/reject. Log every human decision with context and reason — it's your audit trail and future training data. Feed corrections back into the model improvement pipeline.

---

## Quick Checklist

- [ ] Escalation triggers defined — confidence threshold, action type, risk level?
- [ ] Review UI designed to minimize friction (pre-filled context, clear approve/reject)?
- [ ] SLA defined for human review response time?
- [ ] All human decisions logged with context for audit?
- [ ] Corrections fed back into learning/improvement pipeline?
- [ ] Humans not overwhelmed — only genuine exceptions escalated?

---

## Related Patterns

- [Exception Handling](12-exception-handling.md) — the final escalation path when automated recovery fails
- [Learning and Adaptation](09-learning-adaptation.md) — human corrections are the highest-quality training signal
- [Guardrails / Safety](18-guardrails-safety.md) — guardrails determine what gets escalated to humans
