# 🎯 Territory Slicer

A dynamic sales territory segmentation tool that lets you explore the "sweet spot" for splitting accounts between Enterprise and Mid-Market reps.

## What it does

- **Interactive threshold slider** — set the employee count that defines "Enterprise" vs "Mid-Market"
- **Equitable ARR distribution** — uses a greedy LPT algorithm to balance revenue across reps within each segment
- **Risk exposure analysis** — shows how churn risk concentrates per rep after ARR balancing
- **Growth potential view** — surfaces underpenetrated accounts with high expansion headroom
- **Before vs. after comparison** — demonstrates why segmentation improves on the generalist model

## Run locally

```bash
pip install -r requirements.txt
streamlit run app.py
```
s
## Project structure

```
territory-slicer/
├── app.py                  # Main Streamlit application
├── requirements.txt        # Python dependencies
├── data/
│   ├── reps.csv           # Sales rep roster with segments
│   └── accounts.csv       # Account data (ARR, employees, risk, etc.)
└── .streamlit/
    └── config.toml        # Theme configuration
```

## Algorithm

Uses the **Longest Processing Time (LPT)** greedy heuristic:
1. Sort accounts by ARR descending
2. Assign each account to the rep with the lowest current total ARR
3. Repeat until all accounts are assigned

This produces near-optimal balance (typically <3% CV) and is easy to explain and verify.
