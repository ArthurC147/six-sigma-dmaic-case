# DMAIC — Measure Phase

## Data collection plan

- **Metric:** `resolution_hours` — time between ticket creation and resolution
- **Data source:** `data/raw/helpdesk_tickets.csv`, 2,400 tickets, 6 categories
- **Measurement system:** timestamps recorded automatically by the ticketing
  system (no manual measurement error expected)

## Baseline results

| Metric | Value |
|---|---|
| Tickets analyzed (Network) | 825 |
| Mean MTTR (baseline) | 30.9h |
| Process sigma (via moving range) | 16.9 |
| Cpk vs. 24h SLA | -0.14 (not capable) |
| SLA compliance | 43.2% |

A Cpk below 1.0 indicates the process is not capable of consistently
meeting the SLA — the negative value indicates the process **mean itself**
already exceeds the target, not just the tails of the distribution.

## Control chart method

An Individuals (I-MR) chart was used rather than an X-bar/R chart, because
tickets are logged one at a time (not in natural subgroups). Control
limits were calculated as:

```
sigma = mean(|x[i] - x[i-1]|) / 1.128   (d2 constant for n=2)
UCL = x_bar + 3 * sigma
LCL = max(0, x_bar - 3 * sigma)
```

See `notebooks/01_measure.ipynb` for the full calculation and chart.
