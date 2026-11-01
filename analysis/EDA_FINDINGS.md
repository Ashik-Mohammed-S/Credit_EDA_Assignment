# Credit application — full-variable findings

Analyzed 307,511 target-labeled records. Positive target count: 24,825; observed rate: 8.073%. Profiled 159 raw source columns and 137 analytical variables.

## Quality checks

- All 307,511 current records are retained; previous applications are not expanded into target-rate rows.
- All 122 current and 37 previous source columns are profiled, including fields with high missingness.
- Unknown categories are retained; employment sentinel 365243 is explicitly reported.
- Observed associations are not causal effects or lending/eligibility recommendations.

Highest raw-source missingness (original populations; no automatic column dropping):

| Source | Column | Missing | Missing % |
| --- | --- | --- | --- |
| previous_application_source | RATE_INTEREST_PRIVILEGED | 1,664,263 | 99.64% |
| previous_application_source | RATE_INTEREST_PRIMARY | 1,664,263 | 99.64% |
| current_application_source | COMMONAREA_MODE | 214,865 | 69.87% |
| current_application_source | COMMONAREA_AVG | 214,865 | 69.87% |
| current_application_source | COMMONAREA_MEDI | 214,865 | 69.87% |
| current_application_source | NONLIVINGAPARTMENTS_MEDI | 213,514 | 69.43% |
| current_application_source | NONLIVINGAPARTMENTS_MODE | 213,514 | 69.43% |
| current_application_source | NONLIVINGAPARTMENTS_AVG | 213,514 | 69.43% |
| current_application_source | FONDKAPREMONT_MODE | 210,295 | 68.39% |
| current_application_source | LIVINGAPARTMENTS_MODE | 210,199 | 68.35% |

The current employment-day field contains 55,374 instances of sentinel 365243. These applicants remain in the cohort; sentinel-aware analytical employment fields are missing. Source XNA/unknown categories are not reassigned to the majority group.

## Variable-level comparisons

Numeric target-group summaries include exact count, mean, standard deviation, median, quartiles, tail percentiles and range in numeric_by_target.csv. Missing, unknown and IQR-flagged values are retained and visible.

Leading binned associations (not ranked causal drivers or predictive validation):

| Variable | Binned Cramér’s V | Point-biserial r | Missing fraction |
| --- | --- | --- | --- |
| EXT_SOURCE_3 | 0.165 | -0.179 | 0.198 |
| EXT_SOURCE_2 | 0.159 | -0.160 | 0.002 |
| EXT_SOURCE_1 | 0.106 | -0.155 | 0.564 |
| employment_years | 0.090 | -0.075 | 0.180 |
| DAYS_EMPLOYED | 0.090 | 0.075 | 0.180 |
| OCCUPATION_TYPE | 0.080 | — | 0.313 |
| age_years | 0.079 | -0.078 | 0.000 |
| DAYS_BIRTH | 0.079 | 0.078 | 0.000 |
| previous_refusal_share | 0.078 | 0.078 | 0.054 |
| age_band | 0.076 | — | 0.000 |

Examples of higher observed rates among sufficiently populated categorical groups (all groups remain in the full export):

| Variable | Group | n | Positive | Rate | 95% Wilson |
| --- | --- | --- | --- | --- | --- |
| OCCUPATION_TYPE | Low-skill Laborers | 2,093 | 359 | 17.15% | 15.60% – 18.83% |
| OCCUPATION_TYPE | Drivers | 18,603 | 2,107 | 11.33% | 10.88% – 11.79% |
| OCCUPATION_TYPE | Waiters/barmen staff | 1,348 | 152 | 11.28% | 9.70% – 13.08% |
| NAME_EDUCATION_TYPE | Lower secondary | 3,816 | 417 | 10.93% | 9.98% – 11.96% |
| OCCUPATION_TYPE | Security staff | 6,721 | 722 | 10.74% | 10.02% – 11.51% |
| OCCUPATION_TYPE | Laborers | 55,186 | 5,838 | 10.58% | 10.32% – 10.84% |
| OCCUPATION_TYPE | Cooking staff | 5,946 | 621 | 10.44% | 9.69% – 11.25% |
| OCCUPATION_TYPE | Sales staff | 32,102 | 3,092 | 9.63% | 9.31% – 9.96% |
| OCCUPATION_TYPE | Cleaning staff | 4,653 | 447 | 9.61% | 8.79% – 10.49% |
| NAME_INCOME_TYPE | Working | 158,774 | 15,224 | 9.59% | 9.44% – 9.73% |
| previous_history | Mixed / other | 164,294 | 14,785 | 9.00% | 8.86% – 9.14% |
| NAME_EDUCATION_TYPE | Secondary / secondary special | 218,391 | 19,524 | 8.94% | 8.82% – 9.06% |

These are unadjusted historical associations. Small groups, correlated features, missingness, selection and multiple comparisons limit interpretation. Do not use these tables as lending eligibility rules or claims of campaign uplift. Correlation views are pairwise complete and scoped to selected continuous fields.

The interactive dashboard retains full denominators under its four cohort filters. Numeric bounds and category grouping are fixed globally. Raw source audits and correlation matrices remain full-cohort and are labeled accordingly.

