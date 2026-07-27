# DMAIC: Control Phase

## Control plan

| What | Frequency | Owner | Trigger |
|---|---|---|---|
| Review I-MR control chart | Weekly | Helpdesk lead | Any point beyond UCL |
| Recalculate Cpk | Monthly | Process analyst | Cpk drop below previous month |
| Audit triage checklist adherence | Bi-weekly | Team lead | Sample of 20 tickets |

## Alert rule

Flag for investigation if **2 or more consecutive points** exceed the
UCL on the Network control chart. That pattern points to a special-cause
event (an ISP outage, a staffing gap) rather than normal process variation.

## Standardization

The triage checklist and diagnostics runbook produced in the Improve
phase are the controlled documents for this process going forward. Any
change to them requires sign-off from the helpdesk lead, and the control
chart baseline should be recalculated after any process change.

## Next cycle

The ISP escalation SLA was identified in Analyze as a contributing factor
but wasn't fully resolved in this cycle, since it depends on an external
party and a longer negotiation timeline. It's the recommended primary
target for the next DMAIC cycle.
