# DAX Measures — Indian Railways Analytics

## Overview

This document describes the DAX measures used in the Indian Railways — Fare, Availability & Network Intelligence Power BI project.

The measures support fare analysis, journey distance analysis, train counting, route analysis, and average charge calculations.

## 1. Train & Route Analysis

| Measure | Description |
|---|---|
| Active Train Count | Counts trains considered active under the report's filter logic. |
| Unique Route Count | Counts distinct routes in the selected data context. |

## 2. Fare Analysis

| Measure | Description |
|---|---|
| Average Fare per KM | Analyzes fare relative to journey distance. |
| Fare Average | Calculates the average fare under the current filter context. |
| Highest Fare | Identifies the highest fare in the selected data. |
| Lowest Fare | Identifies the lowest fare in the selected data. |
| Overall Fare per KM | Evaluates overall fare relative to journey distance. |
| Total Fare Value | Aggregates total fare values. |

## 3. Base Fare & Additional Charges

| Measure | Description |
|---|---|
| Base Fare Average | Calculates the average base fare. |
| Additional Charges Average | Calculates the average of additional charges, according to the measure definition. |
| Catering Charge Average | Calculates the average catering charge. |
| Dynamic Fare Average | Calculates the average dynamic fare component. |
| Other Charge Average | Calculates the average other-charge component. |
| Reservation Charge Average | Calculates the average reservation charge. |
| Service Tax Average | Calculates the average service tax component. |
| Superfast Charge Average | Calculates the average superfast charge. |

## 4. Journey Analysis

| Measure | Description |
|---|---|
| Distance Average | Calculates average journey distance. |
| Distance Total | Aggregates distance values according to the measure definition. |

## Additional Fields

The following names also appear in the report's field list. Their classification as measures, columns, or calculated columns must be confirmed in Power BI:

- Base Fare
- Catering Charge
- Distance (km)
- Dynamic Fare
- Other Charge
- Reservation Charge
- Service Tax
- Superfast Charge
- Total Fare

## Data Model

The primary fact table is `FactFare`. Other fields include travel class, train number, station names, route, fare date, timestamp, distance, and duration.

## Validation Notes

- Measure descriptions are based on their names and intended analytical use.
- Exact DAX expressions should be copied from the final Power BI report.
- Aggregation methods, filter logic, blank handling, and relationships should be validated against the actual formulas.
- This document should be updated whenever measures change.

## Tools Used

- Power BI Desktop
- DAX
- Power Query
- Data Modeling
- Data Visualization
