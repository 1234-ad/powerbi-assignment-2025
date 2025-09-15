# Assignment 2025 - Complete Checklist

## 📋 Pre-Submission Checklist

### 🗂️ Data Preparation & Modeling (20% of grade)
- [ ] **Data Import**
  - [ ] Orders.People.xlsx loaded successfully
  - [ ] Returns.xlsx loaded successfully
  - [ ] All tables visible in Fields pane

- [ ] **Data Cleaning**
  - [ ] Date fields properly formatted (Date type)
  - [ ] Employee_ID consistent across tables
  - [ ] No missing critical values
  - [ ] Proper data types assigned

- [ ] **Date Table Creation**
  - [ ] Date table created using DAX CALENDAR function
  - [ ] Additional columns added (Year, Month, Quarter, etc.)
  - [ ] Marked as official Date table
  - [ ] Date range covers all data periods

- [ ] **Relationships**
  - [ ] People ↔ Orders (One-to-Many)
  - [ ] People ↔ Returns (One-to-Many)  
  - [ ] Orders ↔ Returns (One-to-Many)
  - [ ] Date ↔ Orders (One-to-Many)
  - [ ] Date ↔ Returns (One-to-Many)
  - [ ] Star schema design achieved

### 🧮 DAX & Time Intelligence (30% of grade)
- [ ] **Core Measures**
  - [ ] Return Rate % = (Returns / Total Transactions) * 100
  - [ ] Avg Return Value = AVERAGE(Returns[Return_Value])
  - [ ] Return Count = COUNTROWS(Returns)
  - [ ] Total Transactions = COUNTROWS(Orders)

- [ ] **YoY Calculations**
  - [ ] Return Rate % YoY Change using SAMEPERIODLASTYEAR()
  - [ ] Avg Return Value YoY Change
  - [ ] YoY percentage change calculations
  - [ ] Proper error handling for missing previous year data

- [ ] **Advanced Measures**
  - [ ] Top 5 Employees by Return Count (dynamic ranking)
  - [ ] YoY return count difference for Top 5
  - [ ] Monthly Return Trend with YoY overlay
  - [ ] Employee contribution % with YoY comparison
  - [ ] All measures tested and working correctly

### 🎨 Visualization & UI/UX (20% of grade)
- [ ] **KPI Cards**
  - [ ] Return Rate % card with YoY indicator
  - [ ] Avg Return Value card with YoY indicator
  - [ ] Return Count card with YoY indicator
  - [ ] Clear up/down arrows or color coding
  - [ ] Professional formatting

- [ ] **Charts**
  - [ ] Line Chart: Monthly return trends with YoY overlay
  - [ ] Bar/Column Chart: Top 5 employees with YoY comparison
  - [ ] Donut/Pie Chart: Employee contribution % with YoY tooltip
  - [ ] All charts properly labeled and formatted

- [ ] **Filters & Slicers**
  - [ ] Employee filter/slicer
  - [ ] Region filter/slicer  
  - [ ] Date range slicer
  - [ ] All slicers working and affecting visuals

- [ ] **Design Quality**
  - [ ] Consistent color palette applied
  - [ ] Professional theme selected
  - [ ] Clean, uncluttered layout
  - [ ] Proper spacing and alignment
  - [ ] Clear titles and labels
  - [ ] Cross-filtering works properly

### 📊 Insights & Storytelling (20% of grade)
- [ ] **Data Analysis**
  - [ ] Identified key YoY trends in return rates
  - [ ] Analyzed top performing/underperforming employees
  - [ ] Seasonal patterns in returns identified
  - [ ] Regional differences analyzed

- [ ] **Business Insights**
  - [ ] 3-5 key findings documented
  - [ ] YoY changes explained and contextualized
  - [ ] Actionable recommendations prepared
  - [ ] Story flows logically through dashboard

### 🎬 Presentation (10% of grade)
- [ ] **Video Quality**
  - [ ] 5 minutes or less duration
  - [ ] Clear audio quality
  - [ ] Screen recording in good resolution
  - [ ] Professional presentation style

- [ ] **Content Coverage**
  - [ ] Data model explanation (30 seconds)
  - [ ] DAX measures demonstration (2 minutes)
  - [ ] Dashboard walkthrough (1.5 minutes)
  - [ ] Key insights sharing (1 minute)
  - [ ] Smooth transitions between topics

- [ ] **Technical Demo**
  - [ ] Show relationships in model view
  - [ ] Demonstrate YoY calculations working
  - [ ] Navigate through all visuals
  - [ ] Show interactivity and filtering
  - [ ] Highlight UI/UX design choices

## 📤 Submission Requirements
- [ ] **Files Prepared**
  - [ ] PBIX file saved as `PowerBI_Assignment_2025.pbix`
  - [ ] File size under upload limit
  - [ ] All data sources embedded or accessible

- [ ] **Video Uploaded**
  - [ ] YouTube video uploaded (Public or Unlisted)
  - [ ] Video title includes your name/assignment
  - [ ] YouTube link copied and tested

- [ ] **Form Submission**
  - [ ] Google Form accessed: https://forms.gle/wmRgYKVetYrSLxWP9
  - [ ] PBIX file uploaded successfully
  - [ ] YouTube link pasted correctly
  - [ ] Contact information provided
  - [ ] Submitted before deadline: **September 15, 2025**

## ⚠️ Final Quality Checks
- [ ] **Data Accuracy**
  - [ ] YoY calculations verified with sample data
  - [ ] No #ERROR or BLANK() values in visuals
  - [ ] Percentages and currencies formatted correctly
  - [ ] Date filters working across all years

- [ ] **Performance**
  - [ ] Dashboard loads quickly (under 10 seconds)
  - [ ] Interactions are responsive
  - [ ] No unnecessary calculated columns
  - [ ] Efficient DAX measures used

- [ ] **Professional Standards**
  - [ ] No spelling errors in titles/labels
  - [ ] Consistent formatting throughout
  - [ ] Logical visual arrangement
  - [ ] Clear navigation and user experience

## 🎯 Success Criteria Summary
To achieve top marks, ensure:
1. **Technical Excellence:** All DAX measures work correctly with proper YoY logic
2. **Design Quality:** Professional, clean, and user-friendly dashboard
3. **Business Value:** Clear insights that drive decision-making
4. **Presentation Skills:** Confident, clear explanation of work
5. **Completeness:** All requirements met without exceptions

## 📞 Need Help?
- Review the step-by-step guide for detailed instructions
- Check DAX formulas guide for exact syntax
- Test each component before moving to the next
- Practice your presentation multiple times

**Remember:** Quality over complexity. A simple, well-executed dashboard beats an overly complex one with errors!