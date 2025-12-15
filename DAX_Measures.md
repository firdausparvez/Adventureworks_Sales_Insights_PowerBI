# AdventureWorks DAX Measures 

This document contains the DAX (Data Analysis Expressions) formulas used in the AdventureWorks Sales & Customer Insights project. They are categorized by their function.

## 1. Key Performance Indicators (KPIs)

### Total Revenue
Calculates total revenue by multiplying order quantities with related product prices.
```dax
SUMX(
    'Sales Data',
    'Sales Data'[OrderQuantity] * RELATED('Product Lookup'[ProductPrice])
)
```
### Total Cost
Multiplies order quantity by product cost to determine total expenses.
```
SUMX(
    'Sales Data',
    'Sales Data'[OrderQuantity] * RELATED('Product Lookup'[ProductCost])
)
```
### Total Profit
Revenue minus Cost.
```
[Total Revenue] - [Total Cost]
```
### Total Orders
Counts unique orders placed.
```
DISTINCTCOUNT('Sales Data'[OrderNumber])
```
### Total Returns
Counts the number of returned items.
```
COUNT('Returns Data'[ReturnQuantity])
```
### Return Rate
Percentage of items sold that were returned.
```
DIVIDE(
    [Quantity Returned],
    [Quantity Sold],
    "No Sales"
)
```
Average Revenue per Customer
```
DIVIDE([Total Revenue], [Total Customer])
```
## 2. Time Intelligence (MoM & YoY)
### Previous Month Orders
Calculates orders from the previous month for comparison.
```
CALCULATE(
    [Total Order],
    DATEADD('Calendar Lookup'[Date], -1, MONTH)
)
```
### Previous Month Profit
```
CALCULATE(
    [Total Profit],
    DATEADD('Calendar Lookup'[Date], -1, MONTH)
)
```
### Order Target (10% Growth)
Sets a target of 10% increase over the previous month.
```
[Previous Month Orders] * 1.1
```
### YTD Revenue (Year-to-Date)
```
CALCULATE(
    [Total Revenue],
    DATESYTD('Calendar Lookup'[Date])
)
```
## 3. Rolling Averages
### 90-Day Rolling Profit
Calculates profit over the last 90 days to smooth out volatility.
```
CALCULATE(
    [Total Profit],
    DATESINPERIOD(
        'Calendar Lookup'[Date],
        MAX('Calendar Lookup'[Date]),
        -90,
        DAY
    )
)
```
### 10-Day Rolling Revenue
```
CALCULATE(
    [Total Revenue],
    DATESINPERIOD(
        'Calendar Lookup'[Date],
        MAX('Calendar Lookup'[Date]),
        -10,
        DAY
    )
)
```
## 4. Product Specific Analysis
### Bike Sales
Calculates sales specifically for the "Bikes" category.
```
CALCULATE(
    [Quantity Sold],
    'Product Categories Lookup'[CategoryName] = "Bikes"
)
```
### Bike Return Rate
Specific return rate for bikes.
```
CALCULATE(
    [Return Rate],
    'Product Categories Lookup'[CategoryName] = "Bikes"
)
```
### % of All Returns
Calculates the proportion of a specific product's returns against all returns.
```
DIVIDE(
    [Total Returns],
    [All Returns]
)
```
## 5. Customer & Scenario Logic
### Total Customer
Counts unique customers.
```
DISTINCTCOUNT('Sales Data'[CustomerKey])
```
### Full Name (Customer Details)
Returns the customer name if one is selected, otherwise shows "Multiple Customers".
```
IF(
    HASONEVALUE('Customer Lookup'[CustomerKey]),
    MAX('Customer Lookup'[Full Name]),
    "Multiple Customers"
)
```
### Adjusted Price (Scenario parameter)
Used for "What-If" analysis on pricing.
```
[Average Retail Price] * (1 + 'Price Adjustment (%)'[Price Adjustment (%) Value])
```
