# Retail KPI Quality Framework

**Task:** Translate an ambiguous business request into measurable KPI definitions and a testable
data-quality agreement.

**Dataset:** `retail-orders-raw.csv` — intentionally imperfect commerce order data (RabTech Academy)
**Decision owner:** Revenue Operations Lead

## What's in this repo

| File | What it is |
|---|---|
| [`KPI_Dictionary.xlsx`](./KPI_Dictionary.xlsx) | 10 KPIs with formula, grain, filters, owner, and refresh cadence, plus a live formula-driven calculation sheet (no hardcoded numbers) |
| [`data_profile_notebook.ipynb`](./data_profile_notebook.ipynb) | Executable Jupyter notebook profiling the dataset for Completeness, Uniqueness, Validity, Consistency, and Freshness, ending in a PASS/FAIL scorecard |
| [`Data_Quality_Contract.md`](./Data_Quality_Contract.md) | The data-quality contract: thresholds per dimension, every known bad row named, and Block/Warn/Auto-fix/Escalate actions with owners and SLAs |
| [`retail-orders-raw.csv`](./retail-orders-raw.csv) | Source data |
| [`retail-data-dictionary.csv`](./retail-data-dictionary.csv) | Column definitions and quality rules used as the basis for all checks above |

## How the pieces connect

1. `retail-data-dictionary.csv` defines what each field *should* look like.
2. `data_profile_notebook.ipynb` checks the raw file against those rules and produces a scorecard.
3. `KPI_Dictionary.xlsx` defines the business KPIs built on top of the (cleaned) data, and includes
   a spreadsheet-native re-implementation of the same validity logic so the numbers can be
   cross-checked without running Python.
4. `Data_Quality_Contract.md` is the governance layer: what threshold breach triggers what action,
   and who owns it.

## Result on the raw file

Only 3 of 12 orders (`RT-1001`, `RT-1009`, `RT-1010`) pass every validity rule as received — see
`Data_Quality_Contract.md` for the full breakdown of what's wrong with the rest.
