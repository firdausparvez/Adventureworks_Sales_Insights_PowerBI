# 📄 Project Report: AdventureWorks Sales & Customer Insights

**Project Title:** AdventureWorks Sales & Customer Insights

**Analyst:** Firdaus Parvez

**Tools Used:** Power BI Desktop (Power Query, DAX, Data Modeling)

## I. Executive Summary
The goal of this project was to transform raw sales data into a professional business intelligence solution. The final report enables the management team to track KPIs (Sales, Revenue, Profit, Returns), analyze regional performance, and identify high-value customer segments.

## Dashboard Visuals

<table>
  <tr>
    <th width="25%"><b>Executive Dashboard</b></th>
    <th width="25%"><b>Map</b></th>
    <th width="25%"><b>Product Detail</b></th>
    <th width="25%"><b>Customer Detail</b></th>
  </tr>

  <tr>
    <td><img src="Dashboard_screenshot/Executive_dashboard.png" width="400" alt="Executive Dashboard"></td>
    <td><img src="Dashboard_screenshot/Map.png" width="400" alt="Map Dashboard"></td>
    <td><img src="Dashboard_screenshot/Product_detail.png" width="400" alt="Product Detail"></td>
    <td><img src="Dashboard_screenshot/Customer_detail.png" width="400" alt="Customer Detail"></td>
  </tr>

  <tr valign="top">
    <td>
      High-level overview of company performance, including Total Revenue, Profit, and Return Rates.
    </td>
    <td>
      This visualizes the geographic distribution of sales, highlighting top-performing regions.
    </td>
    <td>
      A breakdown of product performance, helping identify top-selling items and inventory trends.
    </td>
    <td>
      This page enables in-depth analysis of customer demographics, including Income Level and Occupation.
    </td>
  </tr>
</table>

**Key High-Level Metrics:**

* **Total Profit:** ₹10.5 Million (2020-2022).
* **Total Unique Customers:** 17.4K.
* **Average Revenue per Customer:** ₹1,431.
* **Global Return Rate:** 2.2% (Maintained within acceptable limits).

## II. Technical Execution (Methodology)
The project followed a standard Business Intelligence workflow:

**1. Data Extraction & Transformation (ETL)**

* **Data Source:** Connected to raw CSV files (Transactions, Returns, Customers, Products, Territories).
* **Data Cleaning:**
* Promoted headers and validated data types.
* Created a "SKU Type" column to categorize products by text delimitation.
* Standardized data (e.g., replaced "0" with "NA" in Product Style).
* Extracted domain names from customer emails for geographic analysis.



**2. Data Modeling**

* **Schema Design:** Built a Star Schema with a centralized Fact table (Sales) connected to Dimension tables (lookup tables).
* **Snowflake Schema:** Utilized for Product > Subcategory > Category tables to handle granular product hierarchies.
* **Date Hierarchy:** Created a continuous Date table with hierarchies (Year > Month > Week) for time-series drill-downs.

**3. Advanced DAX Calculations**

* **Calculated Columns:** Created logic for Income Level (Low to Very High) and Customer Priority.
* **Measure Creation:**
* *Performance:* Total Profit, Total Revenue, Total Returns.
* *Time Intelligence:* Previous Month Orders, 90-day Rolling Profit (backend measure).
* *Ratios:* Return Rate (Quantity Returned / Quantity Sold).


* **Parameters:** Dynamic field parameters to switch visuals between "Total Customers" and "Revenue per Customer".

## III. Data Analysis & Key Insights
**1. Revenue Trends**

* **Growth:** The Revenue Trending chart indicates a strong upward trajectory over the observed period, contributing to a Total Revenue of $24.9M.
* **Seasonality:** There are visible peaks and troughs in the monthly data, suggesting seasonal buying behavior.

**2. Product Returns Analysis**

* **Overall Rate:** The overall return rate sits at 2.2%, which is within an acceptable range for retail.
* **Problem Areas:** Drill-down analysis on the Product Detail page reveals that specific "Clothing" and "Accessory" items (such as Jerseys and Tires) appear frequently in the returns list, warranting quality checks.

**3. Customer Segmentation**

* **Income Profile:** The largest customer base falls into the "Average" income bracket (11.6K orders), followed closely by "Low" income (10.3K). "High" income customers place significantly fewer orders (2.8K).
* **Occupation Profile:** The top buyers by occupation are Professionals (7.9K orders) and Skilled Manual workers (6.0K orders).

**4. High-Value Customers**

* **Top Performer:** The dashboard identifies Mr. Maurice Shan as the top customer by revenue.
* **Actionable Data:** The "Top 100 Customers" table allows the sales team to instantly identify and export lists of high-value clients for targeted follow-ups.

## IV. Strategic Recommendations
Based on the data insights, the following actions are recommended for AdventureWorks:

**1. Target the "Average Income" Segment**

* **Observation:** The "Customer Detail" visual shows that the "Average" income group places the most orders (11.6K), significantly outperforming the "High" income group.
* **Recommendation:** Shift marketing focus away from luxury/exclusive messaging. Instead, prioritize value-for-money campaigns and bundle deals that appeal to mid-income Professionals, who are your primary buyers.

**2. Address Product Quality in Clothing & Accessories**

* **Observation:** The "Product Detail" page highlights that while the overall return rate is healthy (2.2%), specific items in the Clothing and Accessory categories appear frequently in return lists.
* **Recommendation:** Conduct a quality control audit on these specific subcategories. For clothing, verify if sizing guides are accurate on the website to reduce returns caused by "wrong size" issues.

**3. Launch a VIP Loyalty Program**

* **Observation:** The "Top 100 Customers" table identifies specific high-value individuals like Mr. Maurice Shan who generate disproportionate revenue.
* **Recommendation:** Implement a tiered loyalty program. Use the dashboard to export the "Top 100" list quarterly and offer them exclusive early access to new products to increase their Lifetime Value (LTV).

**4. Optimize Inventory for Peak Seasons**

* **Observation:** The "Revenue Trending" chart on the Executive Dashboard reveals clear seasonality with peaks and troughs.
* **Recommendation:** Use these historical peaks to forecast inventory needs. Ensure high-demand stock (like Tires and Tubes) is over-stocked before the peak months identified on the trend line to prevent stockouts.

