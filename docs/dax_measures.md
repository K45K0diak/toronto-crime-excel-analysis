# DAX measures

All four measures live on the data model table `Incidents`. The table keeps that name for compatibility with the workbook; every row in it is an offence, and the measures are labelled accordingly.

## Offence Count
```dax
COUNTROWS(Incidents)
```
Counts offence rows in whatever the PivotTable or slicer is currently showing.

## Population
```dax
SUM(Neighbourhoods[POPULATION_2025])
```
Sums 2025 resident population across the neighbourhoods in view, reached through the relationship on `HOOD_158`.

## Offences per 1,000 Residents
```dax
DIVIDE([Offence Count], [Population], 0) * 1000
```
Offences divided by resident population. Over the full 2022-2025 range this is a four-year cumulative figure (55.34 city-wide), not an annual rate (about 13.8 per year).

## % of All Offences
```dax
DIVIDE(
    [Offence Count],
    CALCULATE([Offence Count], ALL(Neighbourhoods))
)
```
Each neighbourhood's share of all offences. `CALCULATE` with `ALL(Neighbourhoods)` removes the neighbourhood filter from the denominator only, so the numerator is filtered and the denominator is the total.