# Six Sigma DMAIC Case Study

![Six Sigma](https://img.shields.io/badge/Six%20Sigma-FFCC00?style=flat-square&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)

> Full DMAIC cycle applied to an IT helpdesk ticket resolution process — control charts, Pareto analysis, process capability (Cpk), and a documented improvement plan.

---

## Business context

A helpdesk process with no statistical monitoring cannot answer basic
questions: which category of problem drives most of the delay? Is the
process even capable of meeting its SLA? This project applies the
5-phase DMAIC methodology (Define, Measure, Analyze, Improve, Control) —
the same framework behind the Lean Six Sigma Yellow Belt certification —
to answer those questions with data, not assumption.

This case study mirrors a real DMAIC project applied to a technical
support ticket workflow, which achieved a documented **13% MTTR
reduction** (Vivo Academy, Lean Six Sigma Yellow Belt). Public data is
used here since the original dataset is confidential; the same
statistical methodology is applied end-to-end.

---

## Problem → Solution → Result

| | |
|---|---|
| **Problem** | Network-category tickets drive 59% of total process time, with a baseline Cpk of -0.14 against a 24h SLA — the process mean itself exceeds the target |
| **Solution** | Full DMAIC cycle: I-MR control chart (Measure), Pareto + stratification (Analyze), standardized triage + documented improvement action (Improve), monitoring plan (Control) |
| **Result** | Simulated pilot shows -12.6% MTTR reduction and Cpk improving from -0.14 to -0.07 — real, measurable progress, with a second cycle recommended to reach full capability |

---

## DMAIC documentation

| Phase | File |
|---|---|
| Define | [`dmaic/01_define.md`](dmaic/01_define.md) — project charter, goal, scope |
| Measure | [`dmaic/02_measure.md`](dmaic/02_measure.md) — baseline data and control chart method |
| Analyze | [`dmaic/03_analyze.md`](dmaic/03_analyze.md) — Pareto, stratification, root cause |
| Improve | [`dmaic/04_improve.md`](dmaic/04_improve.md) — actions taken and simulated result |
| Control | [`dmaic/05_control.md`](dmaic/05_control.md) — monitoring plan and next cycle |

---

## Dataset

Simulated IT helpdesk ticket data (2,400 tickets, 6 categories), designed
to reflect a realistic Pareto distribution — a small number of categories
driving most of the total resolution time, which is the typical pattern
in real support operations.

```
data/
├── raw/
│   └── helpdesk_tickets.csv
└── processed/
    └── dmaic_kpi_summary.csv
```

---

## Statistical methods used

| Method | Where | Why |
|---|---|---|
| I-MR control chart | Measure, Improve | Correct SPC method for one-at-a-time (non-subgrouped) continuous data |
| Pareto by total impact | Analyze | Prioritizes by total time consumed, not just ticket count |
| Boxplot stratification | Analyze | Tests whether priority level explains the delay (it doesn't) |
| Process capability (Cpk, one-sided) | Measure, Improve | Quantifies whether the process can meet the SLA, not just whether the average looks fine |

---

## Project structure

```
six-sigma-dmaic-case/
├── data/{raw,processed}/
├── notebooks/
│   ├── 01_measure.ipynb
│   ├── 02_analyze.ipynb
│   └── 03_improve_control.ipynb
├── dmaic/
│   ├── 01_define.md ... 05_control.md
├── docs/screenshots/
├── requirements.txt
└── README.md
```

---

## How to run

```bash
git clone https://github.com/ArthurC147/six-sigma-dmaic-case.git
cd six-sigma-dmaic-case
pip install -r requirements.txt
jupyter notebook
# Run in order: 01_measure -> 02_analyze -> 03_improve_control
```

No external dataset download needed — `helpdesk_tickets.csv` is included
directly (small, synthetic, no licensing restriction).

---

## What I learned

- Prioritizing a Pareto by total impact (sum of hours) instead of raw
  count changes the answer — the highest-volume category and the
  highest-impact category are not always the same
- An Individuals (I-MR) chart, not a naive mean ± 3×std, is the correct
  way to estimate process variation for ticket-level data — using
  moving range avoids inflating sigma from single special-cause events
- A negative Cpk means the process average itself misses the target —
  a different (and more urgent) problem than a capable process with
  occasional outliers
- One DMAIC cycle rarely makes a broken process fully capable — showing
  a real, partial improvement and naming the next target is more honest
  and more useful than claiming the process is "fixed"

---

## Author

**Arthur Cardoso** — Industrial Engineering @ UFPR · Business & Customer Success Intern @ Telefônica Vivo · Lean Six Sigma Yellow Belt

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/arthur-cardoso-b3b1ba1ab)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/ArthurC147)
