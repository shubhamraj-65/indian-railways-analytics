# Indian Railways Analytics — DAX Measures

This document describes the DAX measures used in the Indian Railways Power BI dashboard to analyze train fares, distance, additional charges, and route coverage.

## 1. Fare & Revenue Analysis

### Total Fare Value
```dax
Total Fare Value = SUM(FactFare[Total Fare])
```
Calculates the total value of fares in the current filter context.

### Fare Average
```dax
Fare Average = AVERAGE(FactFare[Total Fare])
```
Calculates the average total fare.

### Highest Fare
```dax
Highest Fare = MAX(FactFare[Total Fare])
```
Returns the highest total fare in the filtered data.

### Lowest Fare
```dax
Lowest Fare = MIN(FactFare[Total Fare])
```
Returns the lowest total fare.

### Base Fare Average
```dax
Base Fare Average = AVERAGE(FactFare[Base Fare])
```
Calculates the average base fare before additional charges.

### Additional Charges Average
```dax
Additional Charges Average = [Fare Average] - [Base Fare Average]
```
Estimates the difference between average total fare and average base fare.

### Fare Markup %
```dax
Fare Markup % =
DIVIDE(
    [Fare Average] - [Base Fare Average],
    [Base Fare Average]
)
```
Measures the percentage difference between average total fare and average base fare. Format this measure as a percentage.

## 2. Distance & Fare Efficiency

### Distance Total
```dax
Distance Total = SUM(FactFare[Distance (km)])
```
Calculates the sum of recorded distances in the current filter context.

### Distance Average
```dax
Distance Average = AVERAGE(FactFare[Distance (km)])
```
Calculates the average recorded distance.

### Average Fare per KM
```dax
Average Fare per KM =
DIVIDE(
    [Fare Average],
    [Distance Average]
)
```
Divides average fare by average distance.

### Overall Fare per KM
```dax
Overall Fare per KM =
DIVIDE(
    [Total Fare Value],
    [Distance Total]
)
```
Divides total fare value by total recorded distance. This is a ratio of totals, not necessarily the average fare per kilometre for an individual journey.

## 3. Additional Charge Analysis

### Reservation Charge Average
```dax
Reservation Charge Average =
AVERAGE(FactFare[Reservation Charge])
```

### Superfast Charge Average
```dax
Superfast Charge Average =
AVERAGE(FactFare[Superfast Charge])
```

### Service Tax Average
```dax
Service Tax Average =
AVERAGE(FactFare[Service Tax])
```

### Dynamic Fare Average
```dax
Dynamic Fare Average =
AVERAGE(FactFare[Dynamic Fare])
```

### Catering Charge Average
```dax
Catering Charge Average =
AVERAGE(FactFare[Catering Charge])
```

### Other Charge Average
```dax
Other Charge Average =
AVERAGE(FactFare[Other Charge])
```

These measures calculate average values for their respective fare components under the current report filters.

## 4. Train & Route Coverage

### Active Train Count
```dax
Active Train Count =
DISTINCTCOUNT(FactFare[Train Number])
```
Counts distinct train numbers represented in the filtered fare data. It does not independently confirm that a train is currently operating.

### Unique Route Count
```dax
Unique Route Count =
COUNTROWS(
    SUMMARIZE(
        FactFare,
        FactFare[From Station],
        FactFare[To Station]
    )
)
```
Counts distinct origin–destination combinations in the current filter context.

## Notes
- Measures are stored in the `FactFare` table.
- Results respond to the report's filter context, such as train, class, route, or distance, where those filters apply.
- `DIVIDE()` helps handle division by zero safely.
- Average fare-component measures depend on the source data and how missing values are represented.
- All formulas above are based on the measures defined in the Power BI report.
