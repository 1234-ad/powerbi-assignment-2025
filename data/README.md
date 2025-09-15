# Data Directory

## Required Datasets
Place the following Excel files in this directory:

### 1. Orders.People.xlsx
- Contains employee information and order data
- Key fields: Employee ID, Name, Region, Order details
- Used for: Employee performance analysis

### 2. Returns.xlsx  
- Contains return transaction data
- Key fields: Return ID, Employee ID, Return Date, Return Value, Reason
- Used for: Returns analysis and YoY comparisons

## Data Structure Expected

### People Table
```
Employee_ID | Employee_Name | Region | Department | Hire_Date
```

### Orders Table
```
Order_ID | Employee_ID | Order_Date | Customer_ID | Product_ID | Sales_Amount
```

### Returns Table
```
Return_ID | Order_ID | Employee_ID | Return_Date | Return_Value | Return_Reason
```

## Data Quality Checks
- Ensure date fields are properly formatted
- Check for missing Employee_IDs
- Validate return amounts are positive
- Verify date ranges for YoY analysis (need at least 2 years of data)