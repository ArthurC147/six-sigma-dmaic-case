# Six Sigma DMAIC Case Study

![Six Sigma](https://img.shields.io/badge/Six%20Sigma-FFCC00?style=flat-square&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)

A full DMAIC cycle (Define, Measure, Analyze, Improve, Control) run on IT helpdesk data, built the same way the methodology behind my Lean Six Sigma Yellow Belt actually works, not just the vocabulary.

## Read the phases directly

Each phase has its own short write-up in `dmaic/`, which is closer to how a real Six Sigma project gets documented than cramming everything into one README:

- [`01_define.md`](dmaic/01_define.md), the charter: what's broken, what "fixed" means, and where the line is drawn
- [`02_measure.md`](dmaic/02_measure.md), the baseline, and the control chart method used to get it
- [`03_analyze.md`](dmaic/03_analyze.md), Pareto and the actual root causes
- [`04_improve.md`](dmaic/04_improve.md), what changed and what it did to the numbers
- [`05_control.md`](dmaic/05_control.md), how it stays fixed instead of drifting back

## The one thing worth understanding before the rest makes sense

This uses an Individuals (I-MR) control chart, not a plain mean plus or minus three standard deviations. The difference matters: a normal standard deviation gets pulled around by whatever outliers already happened, so it ends up measuring the problem instead of the baseline. An I-MR chart estimates variation from the moving range between consecutive points instead, which holds up better even when the process already has a few bad days in it.

```python
sigma = mean(abs(x[i] - x[i-1])) / 1.128
```

That `1.128` isn't arbitrary, it's a standard statistical constant (d2) for comparing two points at a time, the same one used in real SPC software.

## What the baseline looked like

Network tickets carried both the highest volume and the longest resolution time of any category, and alone accounted for 59% of all support hours logged, well past what a normal Pareto split usually looks like. Cpk against a 24 hour SLA came out negative, which is a specific and fairly bad signal: it means the average itself is already past the target, not just the slow outliers.

## What changed, and what didn't

The improvement plan (standardized triage checklist, better first-line documentation, a defined escalation SLA with the ISP) was modeled with a 13% reduction in mean resolution time, matching a real result from a similar DMAIC project I worked on. Cpk moved from -0.14 to -0.07. Better, clearly, but still not a capable process by the usual bar (Cpk above 1.0).

That's actually the honest outcome of most first DMAIC cycles. Claiming the process got fixed in one pass would be the less credible answer. The real next step, tightening the ISP escalation SLA specifically, is written up in the control phase doc rather than left for someone to guess at later.

## Running it

```bash
pip install -r requirements.txt
jupyter notebook
```

`01_measure.ipynb` → `02_analyze.ipynb` → `03_improve_control.ipynb`, in that order. The dataset (`data/raw/helpdesk_tickets.csv`) is small and synthetic, so it ships with the repo, nothing to download separately.

---

Arthur Cardoso · [LinkedIn](https://linkedin.com/in/arthur-cardoso-b3b1ba1ab) · [GitHub](https://github.com/ArthurC147)
