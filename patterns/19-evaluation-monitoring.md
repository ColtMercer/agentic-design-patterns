# Ch. 19 — Evaluation and Monitoring

> Measure agent correctness, robustness, latency, cost, and safety continuously — before and after deployment.

[← Back to README](../README.md)

---

## What It Is

Evaluation and Monitoring treats agent behavior like production software, not magic. Offline tests, synthetic benchmarks, human evaluation, live telemetry, structured logs, traces, and alerts work together to show whether the system is actually performing well. Without this pattern, regressions hide until users feel them.

---

## When to Use

- Any deployed agent or workflow
- Before rolling out model or prompt changes
- Systems exposed to changing data, user behavior, or cost pressure
- Safety-sensitive applications where regressions must be caught early
- Multi-agent or tool-using systems where failures are hard to debug without telemetry

---

## Key Implementation Insight

Implement **model CI** plus **runtime observability**. Run automated offline tests before release, then instrument live inputs, actions, tool calls, outputs, latency, and cost in production. Add alerts for regression thresholds. Human spot-checks are still necessary because many real failures are qualitative, not just numerical.

---

## Quick Checklist

- [ ] Offline regression suite exists and runs before release?
- [ ] Live latency, cost, and error metrics dashboarded?
- [ ] Human eval loop included for qualitative review?
- [ ] Inputs, tool calls, and outputs logged for reproduction?
- [ ] Alert thresholds defined for regressions?
- [ ] Canary/A-B framework available for changes?

---

## Related Patterns

- [Guardrails / Safety](18-guardrails-safety.md) — guardrails need monitoring to know if they're effective
- [Learning and Adaptation](09-learning-adaptation.md) — learned improvements should be validated continuously
- [Human-in-the-Loop](13-human-in-the-loop.md) — humans provide qualitative review where metrics miss nuance
