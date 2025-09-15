# Complete DAX Formulas Guide

## 📊 Core Measures

### 1. Return Rate Calculations
```dax
// Base measure: Return Rate %
Return Rate % = 
DIVIDE(
    COUNTROWS(Returns),
    COUNTROWS(Orders),
    0
) * 100

// YoY Return Rate Change
Return Rate % YoY = 
VAR CurrentReturnRate = [Return Rate %]
VAR PreviousReturnRate = 
    CALCULATE(
        [Return Rate %],
        SAMEPERIODLASTYEAR('Date'[Date])
    )
RETURN
    CurrentReturnRate - PreviousReturnRate

// YoY Return Rate % Change
Return Rate % YoY Change = 
DIVIDE(
    [Return Rate % YoY],
    CALCULATE([Return Rate %], SAMEPERIODLASTYEAR('Date'[Date])),
    0
) * 100
```

### 2. Average Return Value Calculations
```dax
// Base measure: Average Return Value
Avg Return Value = 
AVERAGE(Returns[Return_Value])

// YoY Average Return Value Change
Avg Return Value YoY = 
VAR CurrentAvg = [Avg Return Value]
VAR PreviousAvg = 
    CALCULATE(
        [Avg Return Value],
        SAMEPERIODLASTYEAR('Date'[Date])
    )
RETURN
    CurrentAvg - PreviousAvg

// YoY Average Return Value % Change
Avg Return Value % YoY = 
DIVIDE(
    [Avg Return Value YoY],
    CALCULATE([Avg Return Value], SAMEPERIODLASTYEAR('Date'[Date])),
    0
) * 100
```

### 3. Top 5 Employees (Dynamic)
```dax
// Return Count per Employee
Return Count = 
COUNTROWS(Returns)

// Top 5 Employees Measure
Top 5 Employees = 
VAR CurrentEmployee = SELECTEDVALUE(People[Employee_Name])
VAR EmployeeRank = 
    RANKX(
        ALL(People[Employee_Name]),
        [Return Count],
        ,
        DESC
    )
RETURN
    IF(EmployeeRank <= 5, [Return Count], BLANK())

// YoY Return Count Difference for Top 5
Top 5 YoY Difference = 
VAR CurrentCount = [Top 5 Employees]
VAR PreviousCount = 
    CALCULATE(
        [Return Count],
        SAMEPERIODLASTYEAR('Date'[Date])
    )
RETURN
    IF(NOT ISBLANK(CurrentCount), CurrentCount - PreviousCount, BLANK())
```

### 4. Monthly Return Trend
```dax
// Monthly Return Count
Monthly Returns = 
CALCULATE(
    COUNTROWS(Returns),
    DATESMTD('Date'[Date])
)

// Previous Year Same Month
Monthly Returns PY = 
CALCULATE(
    [Monthly Returns],
    SAMEPERIODLASTYEAR('Date'[Date])
)

// Monthly YoY Growth %
Monthly YoY Growth % = 
DIVIDE(
    [Monthly Returns] - [Monthly Returns PY],
    [Monthly Returns PY],
    0
) * 100
```

### 5. Employee Contribution Analysis
```dax
// Employee Contribution %
Employee Contribution % = 
DIVIDE(
    [Return Count],
    CALCULATE([Return Count], ALL(People[Employee_Name])),
    0
) * 100

// Previous Year Employee Contribution %
Employee Contribution % PY = 
CALCULATE(
    [Employee Contribution %],
    SAMEPERIODLASTYEAR('Date'[Date])
)

// YoY Contribution Change
Employee Contribution YoY = 
[Employee Contribution %] - [Employee Contribution % PY]
```

## 🗓️ Date Table Creation
```dax
// Create Date Table
Date = 
VAR MinDate = DATE(2022, 1, 1)  // Adjust based on your data
VAR MaxDate = DATE(2025, 12, 31)
RETURN
    ADDCOLUMNS(
        CALENDAR(MinDate, MaxDate),
        "Year", YEAR([Date]),
        "Month", MONTH([Date]),
        "MonthName", FORMAT([Date], "MMMM"),
        "Quarter", "Q" & QUARTER([Date]),
        "WeekDay", WEEKDAY([Date]),
        "WeekDayName", FORMAT([Date], "DDDD"),
        "IsWeekend", WEEKDAY([Date]) IN {1, 7}
    )
```

## 🎯 KPI Formatting Measures
```dax
// KPI Arrow Direction
Return Rate Arrow = 
IF(
    [Return Rate % YoY] > 0,
    "↗️ " & FORMAT([Return Rate % YoY Change], "+0.0%"),
    "↘️ " & FORMAT([Return Rate % YoY Change], "0.0%")
)

// Color Coding for KPIs
Return Rate Color = 
IF(
    [Return Rate % YoY] < 0,
    "Green",  // Lower return rate is good
    "Red"     // Higher return rate is bad
)
```

## 💡 Pro Tips
1. **Always use DIVIDE()** instead of "/" to handle division by zero
2. **Test with SAMEPERIODLASTYEAR()** first, then try DATEADD() if needed
3. **Use VAR statements** for complex calculations to improve readability
4. **Format measures** appropriately (%, currency, whole numbers)
5. **Add error handling** with ISBLANK() and ISERROR() functions