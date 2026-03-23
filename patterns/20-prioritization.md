# Ch. 20 — Prioritization

> Decide what the agent should work on first when tasks, budgets, and urgency compete.

[← Back to README](../README.md)

---

## What It Is

Prioritization is the pattern for ranking tasks, requests, or subtasks based on urgency, value, risk, deadlines, and resource constraints. In a real system, agents rarely have infinite compute or infinite time. Prioritization gives them a rational way to decide what gets attention first and what can wait.

---

## When to Use

- Agents handle many simultaneous requests
- Workloads have mixed criticality or SLA requirements
- Compute budgets or token budgets are constrained
- Multi-step plans generate more work than can be executed at once
- You need to balance urgency, value, and cost rather than optimize just one of them

---

## Key Implementation Insight

Attach **explicit priority metadata** to tasks — urgency, reward, budget, deadlines, risk — then use schedulers that support preemption and dynamic reprioritization. Simple heuristics often go far, but multi-objective optimization may be needed at scale. Also protect against starvation: low-priority work should not wait forever.

---

## Quick Checklist

- [ ] Priority metadata attached to all incoming tasks?
- [ ] Scheduler supports reprioritization or preemption?
- [ ] Time/token budget caps enforced?
- [ ] Priority decisions logged for audit and debugging?
- [ ] Starvation prevention defined for low-priority tasks?
- [ ] Priorities tied to business value, not just intuition?

---

## Related Patterns

- [Resource-Aware Optimization](16-resource-optimization.md) — prioritization decides where scarce resources go
- [Planning](06-planning.md) — plans often create queued subtasks that need ranking
- [Goal Setting and Monitoring](11-goal-setting.md) — priorities should align with explicit goals and success criteria
