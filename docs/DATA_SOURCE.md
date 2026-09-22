# Data source

The raw data is not stored in this repository. `mci_incidents.csv` is about 160 MB, over GitHub's 100 MB file limit, and both files are excluded by `.gitignore` for consistency.

## Where it comes from

Toronto Police Service Public Safety Data Portal: https://data.tps.ca

| Dataset | Saved as | Rows | Downloaded |
|---|---|---|---|
| Major Crime Indicators Open Data | `mci_incidents.csv` | 486,204 (423,899 distinct events) | September 2026 |
| Neighbourhood Crime Rates Open Data | `neighbourhood_rates.csv` | 158 | September 2026 |

The Major Crime Indicators extract covers offences reported from 2014 and runs to 30 June 2026. The portal listed it as updated on 16 July 2026.

## To reproduce

1. Go to https://data.tps.ca and search for each dataset name above.
2. Open the dataset, choose Download, and pick CSV. Large files can take one to two minutes to prepare.
3. Save them as `data\raw\mci_incidents.csv` and `data\raw\neighbourhood_rates.csv`.
4. Open `workbook/toronto_crime_analysis.xlsx`. Go to Data, Get Data, Data Source Settings.
5. Select each source, click Change Source, and browse to your copy of that CSV. Close.
6. Data, Refresh All. The first refresh takes one to three minutes.

The published workbook's queries point at a placeholder path, so step 5 is required before Refresh will work. Newer downloads will contain more recent data, so totals will differ from those reported in the README.