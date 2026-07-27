# DMAIC: Analyze Phase

## Pareto analysis

Ranking categories by **total hours consumed** (not ticket count) is the
correct prioritization method here. A category can have few tickets but still
dominate total process time.

| Category | Total hours | % of total | Cumulative % |
|---|---|---|---|
| Network | 25,490h | 59.3% | 59.3% |
| Software | 7,228h | 16.8% | 76.1% |
| Hardware | 4,016h | 9.3% | 85.4% |
| Printer | 3,775h | 8.8% | 94.2% |
| Access/Permissions | 1,847h | 4.3% | 98.5% |
| Email | 638h | 1.5% | 100.0% |

**Network alone accounts for 59.3% of all process time.** That's a single
category driving the majority of the problem, a stronger signal than the
classic 80/20 Pareto split.

## Stratification

A boxplot of Network resolution time by priority level (see
`notebooks/02_analyze.ipynb`) shows the delay is **not concentrated in any
single priority tier**. High and Critical tickets aren't resolved
meaningfully faster than Low or Medium ones, which is itself a finding:
priority tagging isn't currently driving triage behavior the way it should.

## Root cause analysis (5-Why / contributing factors)

1. **Escalation delays to third-party ISPs.** Network issues frequently
   require external vendor involvement, and there's no defined SLA with
   that vendor.
2. **Insufficient first-line diagnostics documentation.** L1 agents lack
   a standard checklist, leading to inconsistent initial triage quality.
3. **No standard triage checklist.** Without one, ticket handling time
   depends heavily on individual agent experience.

These three factors were selected as the improvement targets for this
cycle based on feasibility: they're internal process fixes, no vendor
contract renegotiation required in the short term.
