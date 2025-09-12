# DAX Formulas Guide

## Required Measures with Examples

### 1. Return Rate %
```dax
Return Rate % = 
DIVIDE(
    COUNTROWS(Returns),
    COUNTROWS(Orders),
    0
) * 100
```

### 2. YoY Return Rate Change
```dax
YoY Return Rate Change = 
VAR CurrentReturnRate = [Return Rate %]
VAR PreviousReturnRate = 
    CALCULATE(
        [Return Rate %],
        SAMEPERIODLASTYEAR('Date'[Date])
    )
RETURN
    CurrentReturnRate - PreviousReturnRate
```

### 3. Average Return Value
```dax
Avg Return Value = 
AVERAGE(Returns[Return_Amount])
```

### 4. YoY Avg Return Value Change
```dax
YoY Avg Return Value Change = 
VAR CurrentAvg = [Avg Return Value]
VAR PreviousAvg = 
    CALCULATE(
        [Avg Return Value],
        SAMEPERIODLASTYEAR('Date'[Date])
    )
RETURN
    CurrentAvg - PreviousAvg
```

### 5. Top 5 Employees by Returns
```dax
Top 5 Employee Returns = 
VAR CurrentEmployee = SELECTEDVALUE(People[Employee_Name])
VAR EmployeeRank = 
    RANKX(
        ALL(People[Employee_Name]),
        [Total Returns],
        ,
        DESC
    )
RETURN
    IF(EmployeeRank <= 5, [Total Returns], BLANK())
```

### 6. Monthly Return Trend
```dax
Monthly Returns = 
CALCULATE(
    COUNTROWS(Returns),
    DATESMTD('Date'[Date])
)
```

### 7. Employee Contribution %
```dax
Employee Contribution % = 
DIVIDE(
    [Total Returns],
    CALCULATE([Total Returns], ALL(People[Employee_Name])),
    0
) * 100
```

## Time Intelligence Functions Used:
- `SAMEPERIODLASTYEAR()` - Compare with same period last year
- `DATEADD()` - Add/subtract time periods
- `PARALLELPERIOD()` - Alternative for period comparison
- `DATESMTD()` - Month-to-date calculations