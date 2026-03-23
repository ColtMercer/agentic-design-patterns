# Ch. 11 — Goal Setting and Monitoring

> Define explicit agent objectives, track progress toward them, and intervene when goals drift, stall, or conflict.

[← Back to README](../README.md)

---

## What It Is

Goal Setting and Monitoring gives agents explicit, structured objectives — not just a prompt to "do a good job." The pattern defines how to encode goals in a machine-readable format (with success criteria, time bounds, and priority weights), monitor progress at runtime, and trigger replanning or human escalation when the agent drifts off course, stalls, or encounters conflicting objectives.

Without this pattern, long-running agents silently wander. With it, they have a compass.

---

## When to Use

- Long-running agents or autonomous pipelines that operate over extended periods
- Multi-step tasks where you need to verify progress, not just final output
- Systems with multiple competing objectives that need explicit priority resolution
- Any agent where "did it actually accomplish the goal?" is not trivially checkable at the end
- Regulatory or compliance contexts requiring auditable goal tracking

---

## Key Implementation Insight

Make goals **explicit, structured, and machine-readable** — not just a natural language instruction. A goal spec should include: what success looks like (measurable criteria), time bounds, priority weight vs. other goals, and conditions for escalation. Implement lightweight **monitoring loops** that check progress metrics at intervals. Build **goal-revision handlers**: when drift is detected, the handler decides whether to replan, reduce scope, or escalate to a human. Conflicting goals should be resolved by priority weights, not silently ignored.

---

## Quick Checklist

- [ ] Goals are machine-readable with explicit success criteria?
- [ ] Time bounds and priority weights defined?
- [ ] Progress monitored at regular intervals (not just at completion)?
- [ ] Goal drift detection implemented with a defined escalation path?
- [ ] Conflicting goals resolved via priority — not ignored?
- [ ] Goal states logged for auditing and post-hoc analysis?

---

## Related Patterns

- [Planning](06-planning.md) — planning decomposes goals into executable steps
- [Evaluation and Monitoring](19-evaluation-monitoring.md) — goal monitoring is a specialized form of agent evaluation
- [Human-in-the-Loop](13-human-in-the-loop.md) — goal drift often triggers human escalation
