# DMAIC — Control Phase

## Control plan

| What | Frequency | Owner | Trigger |
|---|---|---|---|
| Review I-MR control chart | Weekly | Helpdesk lead | Any point beyond UCL |
| Recalculate Cpk | Monthly | Process analyst | Cpk drop below previous month |
| Audit triage checklist adherence | Bi-weekly | Team lead | Sample of 20 tickets |

## Alert rule

Flag for investigation if **2 or more consecutive points** exceed the
UCL on the Network control chart — this indicates a special-cause event
(e.g., ISP outage, staffing gap) rather than normal process variation.

## Standardization

The triage checklist and diagnostics runbook produced in the Improve
phase are the controlled documents for this process going forward. Any
change to them requires sign-off from the helpdesk lead, and the control
chart baseline should be recalculated after any process change.

## Next cycle

The ISP escalation SLA was identified in Analyze as a contributing factor
but not fully resolved in this cycle (external dependency, longer
negotiation timeline). Recommended as the primary target for the next
DMAIC cycle.
