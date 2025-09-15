# 🚀 QUICK START - Complete This Assignment in 6 Hours

## ⚡ **IMMEDIATE ACTION PLAN**

### **Step 1: Get Data (5 minutes)**
1. **Download the actual assignment files:**
   - `Orders.People.xlsx` 
   - `Returns.xlsx`
2. **OR use my sample files for practice:**
   - [sample-orders-people.csv](data/sample-orders-people.csv)
   - [sample-returns.csv](data/sample-returns.csv)

### **Step 2: Power BI Setup (30 minutes)**
1. **Open Power BI Desktop**
2. **Get Data** → Excel/CSV → Load both files
3. **Create Date Table:**
```dax
Date = 
ADDCOLUMNS(
    CALENDAR(DATE(2022,1,1), DATE(2025,12,31)),
    "Year", YEAR([Date]),
    "Month", MONTH([Date]),
    "MonthName", FORMAT([Date], "MMMM"),
    "Quarter", "Q" & QUARTER([Date])
)
```
4. **Mark as Date Table:** Table Tools → Mark as Date Table

### **Step 3: Create Relationships (15 minutes)**
**Model View** → Drag to connect:
- `People[Employee_ID]` ↔ `Orders[Employee_ID]`
- `People[Employee_ID]` ↔ `Returns[Employee_ID]`
- `Orders[Order_ID]` ↔ `Returns[Order_ID]`
- `Date[Date]` ↔ `Orders[Order_Date]`
- `Date[Date]` ↔ `Returns[Return_Date]`

### **Step 4: Copy These DAX Measures (45 minutes)**

```dax
// 1. Return Rate %
Return Rate % = 
DIVIDE(COUNTROWS(Returns), COUNTROWS(Orders), 0) * 100

// 2. YoY Return Rate Change
Return Rate % YoY = 
VAR Current = [Return Rate %]
VAR Previous = CALCULATE([Return Rate %], SAMEPERIODLASTYEAR('Date'[Date]))
RETURN Current - Previous

// 3. Average Return Value
Avg Return Value = AVERAGE(Returns[Return_Value])

// 4. YoY Avg Return Value Change
Avg Return Value YoY = 
VAR Current = [Avg Return Value]
VAR Previous = CALCULATE([Avg Return Value], SAMEPERIODLASTYEAR('Date'[Date]))
RETURN Current - Previous

// 5. Return Count
Return Count = COUNTROWS(Returns)

// 6. Top 5 Employees
Top 5 Employees = 
VAR EmployeeRank = RANKX(ALL(People[Employee_Name]), [Return Count],, DESC)
RETURN IF(EmployeeRank <= 5, [Return Count], BLANK())

// 7. Employee Contribution %
Employee Contribution % = 
DIVIDE([Return Count], CALCULATE([Return Count], ALL(People)), 0) * 100

// 8. Monthly Returns
Monthly Returns = CALCULATE(COUNTROWS(Returns), DATESMTD('Date'[Date]))

// 9. YoY Percentage Changes
Return Rate % YoY Change = 
DIVIDE([Return Rate % YoY], 
       CALCULATE([Return Rate %], SAMEPERIODLASTYEAR('Date'[Date])), 0) * 100

Avg Return Value % YoY = 
DIVIDE([Avg Return Value YoY], 
       CALCULATE([Avg Return Value], SAMEPERIODLASTYEAR('Date'[Date])), 0) * 100
```

### **Step 5: Build Dashboard (2 hours)**

#### **KPI Cards (30 minutes)**
1. **Insert 3 Card visuals**
2. **Configure:**
   - Card 1: `Return Rate %` (add `Return Rate % YoY Change` as tooltip)
   - Card 2: `Avg Return Value` (add `Avg Return Value % YoY` as tooltip)
   - Card 3: `Return Count`

#### **Charts (90 minutes)**
1. **Line Chart** (Monthly Trends):
   - X-axis: `Date[MonthName]`
   - Y-axis: `Monthly Returns`
   - Legend: `Date[Year]`

2. **Bar Chart** (Top 5 Employees):
   - Y-axis: `People[Employee_Name]`
   - X-axis: `Top 5 Employees`

3. **Donut Chart** (Employee Contributions):
   - Legend: `People[Employee_Name]`
   - Values: `Employee Contribution %`

4. **Slicers:**
   - Employee dropdown
   - Region list
   - Date range

### **Step 6: Format Dashboard (30 minutes)**
1. **Apply Theme:** View → Themes → Choose professional theme
2. **Format all visuals:**
   - Consistent colors
   - Clear titles
   - Proper number formatting (%, $, whole numbers)
3. **Test interactivity:** Click slicers, verify cross-filtering

### **Step 7: Record Video (30 minutes)**
**Use this exact script:**
```
"Hello, I'm [Your Name]. This Power BI dashboard analyzes employee 
returns with year-over-year comparisons.

[Show Model View] I've created a star schema with Date, People, Orders, 
and Returns tables connected properly.

[Show Report] Key features include:
- Return rate tracking with YoY indicators
- Top 5 employee rankings that update dynamically  
- Monthly trend analysis with previous year overlay
- Interactive filtering by employee and region

[Click through visuals] The data shows [mention 2-3 specific insights 
from your actual data].

This provides actionable insights for improving performance and 
reducing return rates. Thank you."
```

### **Step 8: Submit (15 minutes)**
1. **Save as:** `PowerBI_Assignment_2025.pbix`
2. **Upload video to YouTube** (unlisted)
3. **Submit via Google Form:** https://forms.gle/wmRgYKVetYrSLxWP9

---

## 🆘 **EMERGENCY MODE (2 Hours Left)**

### **Minimum Viable Solution:**
1. **Import data** (10 min)
2. **Basic relationships** (10 min)
3. **3 core measures:** Return Rate %, Avg Return Value, Return Count (20 min)
4. **Simple YoY:** Use `DATEADD('Date'[Date], -1, YEAR)` (20 min)
5. **3 basic visuals:** Cards + 1 chart (30 min)
6. **Quick video:** 3-minute walkthrough (20 min)
7. **Submit immediately** (10 min)

---

## 💡 **SUCCESS TIPS**

### **Copy-Paste Strategy:**
- Use my DAX formulas exactly as written
- Don't modify unless you understand completely
- Test each measure before moving to next

### **Time Savers:**
- Use sample data first to learn the process
- Focus on functionality over perfect design
- Record video in one take (practice first)

### **Quality Checks:**
- Verify YoY calculations show reasonable changes
- Ensure all visuals respond to slicers
- Check that percentages and currency format correctly

---

## 🎯 **YOU CAN DO THIS!**

**With my guides, you have:**
- ✅ Complete step-by-step instructions
- ✅ All DAX formulas ready to copy
- ✅ Sample data to practice with
- ✅ Video script template
- ✅ Emergency backup plan

**Just follow the steps exactly as written. You've got this! 🚀**