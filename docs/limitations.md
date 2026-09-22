# Limitations

**Counting basis.** This analysis counts by occurrence year. Toronto Police publish neighbourhood figures by report year. For 2025 assaults the two bases give 23,578 and 24,648 against a published 24,686; matched on report year the difference is 0.15%.

**Offences, not events.** The source records one row per offence. 486,204 rows correspond to 423,899 distinct events, so one occurrence with several charges appears several times. All counts are offence counts, and the published figures reconcile against the offence count.

**Unassigned neighbourhoods.** 7,459 rows with no assigned neighbourhood (`NSA`) were excluded.

**Population vintage.** `POPULATION_2025` is applied to all four years, so 2022-2024 use a later population figure.

**Location offsetting.** Toronto Police move incident locations to the nearest road intersection for privacy. Neighbourhood assignment is approximate, especially near boundaries.

**Per-capita denominators.** Rates on small populations (8,000 to 10,400 residents) are sensitive to a handful of offences. Residential population is the wrong denominator where far more people visit or work than live; identifying those places is judgement from neighbourhood names. The per-capita figure of 55.34 per 1,000 is four-year cumulative, about 13.8 per year.

**Forecast test.** Six months is a small out-of-sample test. All six actuals inside a 95% interval is consistent with a well-specified model but not proof of accuracy. June 2026 is probably understated because offences reported in July are not in the extract.

**Data currency.** The extract runs to 30 June 2026; the portal listed an update on 16 July 2026. Partial-year 2026 data is excluded from the analysis and used only to test the forecast.