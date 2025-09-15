# Sample Data Structure Guide

## 📊 Expected Data Format

### Orders.People.xlsx Structure

#### People Sheet
```csv
Employee_ID,Employee_Name,Region,Department,Hire_Date,Manager_ID
EMP001,John Smith,North,Sales,2022-01-15,MGR001
EMP002,Sarah Johnson,South,Sales,2022-03-20,MGR001
EMP003,Mike Davis,East,Sales,2021-11-10,MGR002
EMP004,Lisa Wilson,West,Sales,2023-02-05,MGR002
EMP005,David Brown,North,Support,2022-06-12,MGR003
```

#### Orders Sheet
```csv
Order_ID,Employee_ID,Order_Date,Customer_ID,Product_ID,Sales_Amount,Quantity
ORD001,EMP001,2023-01-15,CUST001,PROD001,1500.00,3
ORD002,EMP002,2023-01-16,CUST002,PROD002,2300.00,1
ORD003,EMP001,2023-01-18,CUST003,PROD001,1500.00,3
ORD004,EMP003,2023-01-20,CUST004,PROD003,850.00,2
ORD005,EMP004,2023-01-22,CUST005,PROD002,2300.00,1
```

### Returns.xlsx Structure

#### Returns Sheet
```csv
Return_ID,Order_ID,Employee_ID,Return_Date,Return_Value,Return_Reason,Product_ID
RET001,ORD001,EMP001,2023-01-25,500.00,Defective,PROD001
RET002,ORD002,EMP002,2023-01-28,2300.00,Wrong Size,PROD002
RET003,ORD004,EMP003,2023-02-01,425.00,Customer Changed Mind,PROD003
RET004,ORD001,EMP001,2023-02-03,1000.00,Damaged in Transit,PROD001
RET005,ORD005,EMP004,2023-02-05,2300.00,Not as Described,PROD002
```

## 🔍 Data Quality Requirements

### Critical Fields for Analysis
1. **Employee_ID**: Must be consistent across all tables
2. **Dates**: Must be in proper date format (not text)
3. **Return_Value**: Must be numeric (positive values)
4. **Order amounts**: Must be numeric for calculations

### Data Validation Checklist
- [ ] **No missing Employee_IDs** in any table
- [ ] **Date ranges** cover at least 2 years for YoY analysis
- [ ] **Return values** are positive numbers
- [ ] **Employee names** are consistent (no typos)
- [ ] **Regions** use standard naming (North, South, East, West)

## 📈 Sample YoY Data Pattern

### 2023 Data (Current Year)
```
Month       | Returns | Return_Value | Employees_Active
January     | 15      | $12,500      | 25
February    | 18      | $15,200      | 25
March       | 12      | $9,800       | 26
April       | 20      | $18,500      | 26
May         | 16      | $13,200      | 27
June        | 14      | $11,800      | 27
```

### 2022 Data (Previous Year)
```
Month       | Returns | Return_Value | Employees_Active
January     | 12      | $10,200      | 22
February    | 15      | $12,800      | 22
March       | 10      | $8,500       | 23
April       | 17      | $15,200      | 23
May         | 13      | $11,000      | 24
June        | 11      | $9,200       | 24
```

### Expected YoY Calculations
```
January 2023 vs 2022:
- Return Count: +3 (+25%)
- Return Value: +$2,300 (+22.5%)
- Return Rate: Depends on total orders
```

## 🎯 Key Relationships

### Primary Relationships
```
People (Dimension)
├── Employee_ID (Primary Key)
└── Connected to:
    ├── Orders[Employee_ID] (Foreign Key)
    └── Returns[Employee_ID] (Foreign Key)

Orders (Fact Table)
├── Order_ID (Primary Key)
├── Employee_ID (Foreign Key → People)
├── Order_Date (Foreign Key → Date)
└── Connected to:
    └── Returns[Order_ID] (Foreign Key)

Returns (Fact Table)
├── Return_ID (Primary Key)
├── Order_ID (Foreign Key → Orders)
├── Employee_ID (Foreign Key → People)
└── Return_Date (Foreign Key → Date)

Date (Dimension)
├── Date (Primary Key)
└── Connected to:
    ├── Orders[Order_Date] (Foreign Key)
    └── Returns[Return_Date] (Foreign Key)
```

## 📋 Data Preparation Steps

### 1. Excel File Preparation
Before importing to Power BI:
- Remove any merged cells
- Ensure headers are in row 1
- Remove empty rows/columns
- Format date columns consistently
- Save as .xlsx format

### 2. Power BI Import Settings
```
Data Type Mapping:
- Employee_ID: Text
- Employee_Name: Text
- Order_Date: Date
- Return_Date: Date
- Sales_Amount: Decimal Number
- Return_Value: Decimal Number
- Quantity: Whole Number
```

### 3. Data Transformation (Power Query)
```m
// Remove empty rows
= Table.SelectRows(Source, each not List.IsEmpty(List.RemoveMatchingItems(Record.FieldValues(_), {"", null})))

// Standardize date format
= Table.TransformColumnTypes(#"Removed Empty Rows",{{"Order_Date", type date}, {"Return_Date", type date}})

// Clean employee names
= Table.TransformColumns(#"Changed Type", {{"Employee_Name", Text.Proper}})
```

## 🔧 Testing Your Data

### Quick Validation Queries
```dax
// Check for missing relationships
Missing_Employee_Returns = 
CALCULATE(
    COUNTROWS(Returns),
    ISBLANK(RELATED(People[Employee_Name]))
)

// Verify date ranges
Min_Date = MIN(Orders[Order_Date])
Max_Date = MAX(Returns[Return_Date])

// Check data completeness
Total_Employees = DISTINCTCOUNT(People[Employee_ID])
Employees_With_Orders = DISTINCTCOUNT(Orders[Employee_ID])
Employees_With_Returns = DISTINCTCOUNT(Returns[Employee_ID])
```

## 💡 Pro Tips

### Data Quality Best Practices
1. **Always backup** original Excel files
2. **Document any changes** made during import
3. **Test relationships** before building measures
4. **Validate calculations** with known results
5. **Keep data transformation simple**

### Common Data Issues
- **Date formats**: US vs European date formats
- **Text encoding**: Special characters in names
- **Number formats**: Currency symbols, thousands separators
- **Missing values**: Handle nulls appropriately
- **Duplicate records**: Check for data entry errors

Remember: **Clean data is the foundation of accurate analysis!**