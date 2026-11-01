# Applicant-Level Credit Risk EDA

[![Validation](https://github.com/Ashik-Mohammed-S/Credit_EDA_Assignment/actions/workflows/validate.yml/badge.svg)](https://github.com/Ashik-Mohammed-S/Credit_EDA_Assignment/actions/workflows/validate.yml)

Describe repayment difficulty without overweighting applicants who have more historical loans.

Independent public portfolio work; historical educational notebooks remain under `historical/`. The current implementation and results described here take precedence over historical in-sample numbers.

## Data and approach

307,511 current applications and 1,670,214 previous applications, stored as checksum-verified compressed parts.

Aggregate previous applications by SK_ID_CURR before a one-to-one left join. Report target rates with observation counts across applicant groups instead of presenting exploratory associations as a deployed risk model.

## Current full-data result

| Measure | Current analysis | Baseline where applicable |
| --- | --- | --- |
| Current applications | 307,511 | — |
| Previous applications | 1,670,214 | — |
| Positive TARGET applications | 24,825 | — |
| Observed target rate | 8.073% | — |

Results are specific to the documented dataset and split. See generated `results/analysis.json` after execution for full metrics and assumptions.

## Run locally

Use the Python version in `.python-version`, then:

```sh
python -m pip install -r requirements.txt
python scripts/fetch_data.py
python scripts/run_notebook.py --mode full
```

Reference data is committed under `dataset/`, directly or as reconstructable compressed parts. The downloader verifies checksums and restores stored data offline. See [DATA.md](DATA.md) and [dataset-sources.json](dataset-sources.json) for provenance and upstream terms. Package installation and the spaCy model, where needed, require network access on a fresh machine.

## Review the implementation

Inspect the aggregation grain, one-to-one merge validation and group denominators. Start with [scripts/analysis.py](scripts/analysis.py), then the root notebook. The workflow validates dependencies, smoke checks and full-data notebook execution with dataset downloads disabled.

## Limitations

Descriptive historical analysis, not lending advice, causal inference or an automated eligibility decision. Source-group differences need context and cannot justify individual credit decisions.

[Method notes](ANALYSIS.md) · [All portfolio projects](https://github.com/Ashik-Mohammed-S/Ashik-Mohammed-S/blob/main/PORTFOLIO.md)
