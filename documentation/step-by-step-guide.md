# Complete Step-by-Step Implementation Guide

## Phase 1: Data Preparation (30 minutes)

### Step 1: Import Data
1. Open Power BI Desktop
2. Get Data → Excel → Select Orders.People.xlsx
3. Get Data → Excel → Select Returns.xlsx
4. Load both tables

### Step 2: Create Date Table
```dax
Date = 
ADDCOLUMNS(
    CALENDAR(DATE(2020,1,1), DATE(2025,12,31)),
    "Year", YEAR([Date]),
    "Month", MONTH([Date]),
    "MonthName", FORMAT([Date], "MMMM"),
    "Quarter", QUARTER([Date])
)
```

### Step 3: Mark Date Table
- Model view → Right-click Date table → Mark as date table

## Phase 2: Data Modeling (20 minutes)

### Relationships to Create:
1. People[Employee_ID] → Returns[Employee_ID] (Many-to-One)
2. Date[Date] → Returns[Return_Date] (One-to-Many)
3. Date[Date] → Orders[Order_Date] (One-to-Many)

### Validation:
- Check relationship cardinality
- Ensure cross-filter direction is correct
- Test with sample visuals

## Phase 3: DAX Measures (45 minutes)

### Create New Measure Table:
1. Home → Enter Data → Create empty table named "Measures"
2. Add all measures from dax-formulas-guide.md

### Testing Each Measure:
- Create simple table visual
- Add measure to verify calculation
- Check YoY comparisons work correctly

## Phase 4: Dashboard Design (60 minutes)

### Layout Structure:
```
[KPI Cards Row]     [Filters Panel]
[Return Rate] [Avg Value] [Count]

[Charts Section]
[Line Chart - Monthly Trends]
[Bar Chart - Top 5 Employees]
[Donut Chart - Employee Contribution]
```

### Visual Specifications:
1. **KPI Cards**: Show current value + YoY change %
2. **Line Chart**: X-axis = Month, Y-axis = Returns, Add YoY line
3. **Bar Chart**: Top 5 employees with YoY comparison
4. **Donut Chart**: Employee contribution with tooltips
5. **Slicers**: Employee, Region, Date range

### Color Scheme:
- Primary: #1f77b4 (Blue)
- Secondary: #ff7f0e (Orange) 
- Success: #2ca02c (Green)
- Warning: #d62728 (Red)

## Phase 5: Video Recording (30 minutes)

### Recording Script:
1. **Introduction** (30s): "Welcome to my Power BI dashboard..."
2. **Overview** (60s): Show main KPIs and YoY changes
3. **Deep Dive** (120s): Interact with filters, explain trends
4. **Insights** (90s): Highlight key findings
5. **Conclusion** (30s): Summarize and thank

### Recording Tips:
- Use OBS Studio or PowerPoint recording
- 1080p resolution minimum
- Clear audio (use headset mic)
- Upload to YouTube as unlisted

## Phase 6: Submission (15 minutes)

### Final Checklist:
- [ ] PBIX file saved and tested
- [ ] Video uploaded to YouTube
- [ ] Links ready for Google Form
- [ ] Submit before deadline (Sep 15, 2025)

## Estimated Total Time: 3.5 hours