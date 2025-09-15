# Troubleshooting Guide

## 🚨 Common Issues & Solutions

### Data Loading Problems

#### Issue: "File not found" or "Access denied"
**Solution:**
- Ensure Excel files are not open in another application
- Check file permissions and location
- Try copying files to a local folder first

#### Issue: "Data type errors" during import
**Solution:**
```
1. Open Power Query Editor
2. Select problematic column
3. Transform → Data Type → Choose correct type
4. For dates: ensure format is MM/DD/YYYY or DD/MM/YYYY
5. For numbers: remove text characters, handle nulls
```

### Relationship Issues

#### Issue: "Relationships not working" or "Cross-filtering broken"
**Solution:**
- Check cardinality: Should be One-to-Many from dimension to fact
- Verify column data types match exactly
- Ensure no duplicate values in "One" side of relationship
- Set cross-filter direction to "Both" if needed

#### Issue: "Circular dependency detected"
**Solution:**
- Review relationship chain: Date → Orders → Returns → People
- Remove any direct relationships that create loops
- Use inactive relationships if multiple date fields exist

### DAX Calculation Errors

#### Issue: "SAMEPERIODLASTYEAR() returns blank"
**Solution:**
```dax
// Check if Date table is marked as Date table
// Verify date column is continuous (no gaps)
// Ensure previous year data exists

// Alternative approach:
Previous Year = 
CALCULATE(
    [Your Measure],
    DATEADD('Date'[Date], -1, YEAR)
)
```

#### Issue: "Division by zero errors"
**Solution:**
```dax
// Always use DIVIDE() function
Safe Percentage = 
DIVIDE(
    [Numerator],
    [Denominator],
    0  // Default value if denominator is zero
)
```

#### Issue: "Top N ranking not working"
**Solution:**
```dax
// Ensure RANKX uses ALL() to remove filters
Top N Measure = 
VAR CurrentRank = 
    RANKX(
        ALL(Table[Column]),  // Remove filters
        [Measure],
        ,
        DESC
    )
RETURN
    IF(CurrentRank <= 5, [Measure], BLANK())
```

### Visualization Problems

#### Issue: "Charts showing wrong data"
**Solution:**
- Check field assignments in visualization pane
- Verify measure calculations with simple test data
- Clear all filters and test again
- Check if relationships are active

#### Issue: "YoY indicators not showing"
**Solution:**
```dax
// Create conditional formatting measure
YoY Arrow = 
VAR YoYChange = [Your YoY Measure]
RETURN
    IF(
        ISBLANK(YoYChange), "",
        IF(YoYChange > 0, "↗️", "↘️")
    )
```

#### Issue: "Slicers not filtering visuals"
**Solution:**
- Check visual interactions: Format → Edit interactions
- Ensure slicer field has proper relationships
- Verify slicer is set to "Filter" not "Highlight"

### Performance Issues

#### Issue: "Dashboard loading slowly"
**Solution:**
- Reduce number of visuals per page (max 6-8)
- Use measures instead of calculated columns
- Optimize DAX: avoid nested CALCULATE functions
- Import only necessary columns

#### Issue: "Memory errors during refresh"
**Solution:**
- Close other applications
- Reduce data volume (filter to recent years only)
- Use DirectQuery for large datasets
- Optimize data model relationships

## 🔧 Quick Fixes

### Date Table Issues
```dax
// If automatic date table causes problems, create custom:
Date = 
ADDCOLUMNS(
    CALENDAR(DATE(2022,1,1), DATE(2025,12,31)),
    "Year", YEAR([Date]),
    "Month", MONTH([Date]),
    "MonthName", FORMAT([Date], "MMMM"),
    "Quarter", QUARTER([Date])
)
```

### Missing Data Handling
```dax
// Handle missing previous year data
YoY Safe = 
VAR Current = [Current Measure]
VAR Previous = CALCULATE([Current Measure], SAMEPERIODLASTYEAR('Date'[Date]))
RETURN
    IF(
        ISBLANK(Previous),
        "No Prior Data",
        Current - Previous
    )
```

### Formatting Issues
```dax
// Format percentages properly
Formatted Percentage = 
FORMAT([Percentage Measure], "0.0%")

// Format currency
Formatted Currency = 
FORMAT([Currency Measure], "$#,##0")
```

## 📞 Getting Help

### Before Asking for Help:
1. **Check error messages** carefully
2. **Test with simple data** first
3. **Verify relationships** in model view
4. **Clear all filters** and test again
5. **Check DAX syntax** for typos

### Useful Resources:
- **Power BI Community:** community.powerbi.com
- **DAX Guide:** dax.guide
- **Microsoft Docs:** docs.microsoft.com/power-bi
- **YouTube Tutorials:** Search "Power BI [your issue]"

### Emergency Checklist (Day Before Deadline):
- [ ] Save backup copy of PBIX file
- [ ] Test all measures with known data
- [ ] Verify video recording setup
- [ ] Check Google Form submission process
- [ ] Have alternative submission method ready

## 🎯 Last-Minute Tips

### If Running Out of Time:
1. **Focus on core requirements** first
2. **Simple working solution** beats complex broken one
3. **Test YoY calculations** with obvious data
4. **Keep dashboard clean** and professional
5. **Practice presentation** at least once

### Quality Over Quantity:
- Better to have 3 perfect visuals than 6 broken ones
- Focus on accurate YoY calculations
- Ensure basic interactivity works
- Professional appearance matters

Remember: **A working, simple solution is better than a complex, broken one!**