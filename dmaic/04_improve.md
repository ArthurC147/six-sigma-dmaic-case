# DMAIC — Improve Phase

## Improvement actions

| # | Action | Root cause addressed |
|---|---|---|
| 1 | Standardized triage checklist for Network tickets | Lack of triage standard |
| 2 | First-line diagnostics documentation (runbook) | Insufficient L1 documentation |
| 3 | Defined escalation SLA with ISP provider | Escalation delays |

## Expected impact

These actions mirror the real intervention applied in a comparable DMAIC
cycle at Vivo, which achieved a documented **13% MTTR reduction**. That
target is used here as the basis for the simulated "after" dataset
(`notebooks/03_improve_control.ipynb`), applying a -13% shift in mean
resolution time plus a proportional reduction in variability — the
expected statistical effect of standardizing a previously inconsistent
process.

## Result (simulated pilot)

| Metric | Before | After | Change |
|---|---|---|---|
| Mean MTTR | 30.9h | 27.0h | -12.6% |
| Process sigma | 16.9 | 14.9 | -11.8% |
| Cpk | -0.14 | -0.07 | improved, still not capable |
| SLA compliance | 43.2% | 50.3% | +7.1 pp |

**Honest reading of the result:** the improvement is real and
statistically meaningful, but a single DMAIC cycle does not make the
process fully capable (Cpk still below 1.0). This is the expected,
realistic outcome of a first improvement cycle — it justifies a second
cycle targeting the ISP escalation SLA specifically, since that is the
largest remaining lever.
