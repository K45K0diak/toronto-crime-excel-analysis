# Incidents query (Power Query M)

```powerquery
let
    Source = Csv.Document(File.Contents("C:\Users\your-username\OneDrive\Desktop\toronto-crime-excel\data\raw\mci_incidents.csv"),[Delimiter=",", Columns=31, Encoding=65001, QuoteStyle=QuoteStyle.None]),
    #"Promoted Headers" = Table.PromoteHeaders(Source, [PromoteAllScalars=true]),
    #"Changed Type" = Table.TransformColumnTypes(#"Promoted Headers",{{"OBJECTID", Int64.Type}, {"EVENT_UNIQUE_ID", type text}, {"REPORT_DATE", type datetime}, {"OCC_DATE", type datetime}, {"REPORT_YEAR", Int64.Type}, {"REPORT_MONTH", type text}, {"REPORT_DAY", Int64.Type}, {"REPORT_DOY", Int64.Type}, {"REPORT_DOW", type text}, {"REPORT_HOUR", Int64.Type}, {"OCC_YEAR", Int64.Type}, {"OCC_MONTH", type text}, {"OCC_DAY", Int64.Type}, {"OCC_DOY", Int64.Type}, {"OCC_DOW", type text}, {"OCC_HOUR", Int64.Type}, {"DIVISION", type text}, {"LOCATION_TYPE", type text}, {"PREMISES_TYPE", type text}, {"UCR_CODE", Int64.Type}, {"UCR_EXT", Int64.Type}, {"OFFENCE", type text}, {"CSI_CATEGORY", type text}, {"HOOD_158", type text}, {"NEIGHBOURHOOD_158", type text}, {"HOOD_140", type text}, {"NEIGHBOURHOOD_140", type text}, {"LONG_WGS84", type number}, {"LAT_WGS84", type number}, {"x", type number}, {"y", type number}}),
    #"Removed Other Columns" = Table.SelectColumns(#"Changed Type",{"EVENT_UNIQUE_ID", "REPORT_DATE", "OCC_DATE", "REPORT_YEAR", "OCC_YEAR", "OCC_MONTH", "OCC_DAY", "OCC_DOW", "OCC_HOUR", "DIVISION", "LOCATION_TYPE", "PREMISES_TYPE", "OFFENCE", "CSI_CATEGORY", "HOOD_158", "NEIGHBOURHOOD_158"}),
    #"Filtered Rows" = Table.SelectRows(#"Removed Other Columns", each ([HOOD_158] <> "NSA")),
    #"Filtered Rows1" = Table.SelectRows(#"Filtered Rows", each [OCC_YEAR] >= 2022 and [OCC_YEAR] <= 2025),
    #"Changed Type1" = Table.TransformColumnTypes(#"Filtered Rows1",{{"OCC_DATE", type date}, {"REPORT_DATE", type date}, {"HOOD_158", Int64.Type}, {"OCC_YEAR", Int64.Type}, {"OCC_DAY", Int64.Type}, {"OCC_HOUR", Int64.Type}, {"REPORT_YEAR", Int64.Type}})
in
    #"Changed Type1"
```