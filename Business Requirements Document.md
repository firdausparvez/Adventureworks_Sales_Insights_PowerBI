# 📄 Business Requirements Document

**Project Title:** AdventureWorks Sales & Customer Insights  
**Role:** Business Intelligence Analyst  
**Client:** AdventureWorks – Global Manufacturing Company  

---

## I. Business Objective

- **Goal:** Design and deliver a centralized Power BI analytics solution .
- **Purpose:** Enable business users to monitor sales performance, analyze product/customer trends, track returns, and evaluate regional performance .
- **Outcome:** Transform raw transactional CSV data into a structured data model with interactive dashboards for decision-making .

---

## II. Business Scope

- **Analysis Areas:**
  - Products, categories, and subcategories .
  - Customers and customer segments .
  - Sales territories and regions .
  - Time-based performance (Year, Month, Week, Date) .

- **Lifecycle:** Data ingestion → Transformation → Modeling → DAX calculations → Visualization .

---

## III. Data Sources

- **Source Type:** Raw CSV files provided as part of the project assignment .
- **File List:**
  - Sales Transactions & Returns Data .
  - Product Master Data, Category Lookup, & Subcategory Lookup .
  - Customer Information .
  - Sales Territory Data .
- **Platform:** All preparation and modeling performed internally within Power BI Desktop .

---

## IV. Data Preparation Requirements

The following steps are implemented using Power Query:

- **Product Data:**
  - Integrate Product Category and Subcategory lookup tables .
  - Extract "SKU Type" by parsing text before the dash in Product SKU .
  - Replace invalid Product Style values ("0") with "NA" .

- **Customer Data:**
  - Extract Domain Name from email addresses and clean text .
  - Derive "Birth Year" from Birth Date .

- **Customer Logic:**
  - **Priority:** "Priority" if parent & income > $100k; otherwise "Standard" .
  - **Income Level:** "Very High" (≥$150k), "High" (≥$100k), "Average" (≥$50k), "Low" (<$50k) .
  - **Education Category:** Group "Partial High School" with "High School", "Partial College" with "Undergrad", etc., using SWITCH logic .

- **Calendar Data:**
  - Generate a dedicated Calendar table (computed) .
  - Add derived date fields: Month Name, Month Number, Start of Year, Year .

- **Data Quality:**
  - Ensure clean column headers and consistent data types .
  - Restore tables to original state after statistical validation where required .

---

## V. Data Modeling Requirements

A relational data model designed for efficiency:

- **Schema Type:** Star Schema connecting Sales, Returns, Customer, Product, and Territory tables .

- **Advanced Modeling:**
  - **Snowflake Schema:** Applied specifically to Product, Subcategory, and Category tables .
  - **Filter Flow:** Single-direction filters (except where specific bi-directional testing was required) .
  - **Hierarchy:** Date Hierarchy (Start of Year → Start of Month → Start of Week → Date) for drill-downs .

---

## VI. Analytical & DAX Requirements

Business metrics developed using Data Analysis Expressions (DAX):

- **Core KPIs:**
  - Total Sales, Total Revenue, Total Profit, Total Customers .
  - Quantity Sold, Quantity Returned, Return Rate .

- **Specific Product Logic:**
  - **Bike Analysis:** Specific measures for "Bike Returns", "Bike Sales", and "Bike Return Rate" .
  - **All Returns:** Measure calculating returns regardless of filter context to determine "% of All Returns" .

- **Time Intelligence:**
  - Previous Month Orders & Previous Month Profit .
  - 90-day Rolling Profit .
  - **Targets:** 10% increase scenarios for Orders and Profit .

- **Advanced Logic:**
  - **Field Parameters:** "Customer Metric Selection" parameter to toggle between Total Customers and Revenue per Customer on visuals .

---

## VII. Reporting & Visualization Requirements

Designed for business and leadership consumption:

- **Executive Dashboard:**
  - High-level KPI cards and trending lines .

- **Customer Detail Report:**
  - **KPI Cards:** Unique Customers and Revenue per Customer .
  - **Line Chart:** Weekly trending with zoom sliders, drill-down capabilities (Year/Month/Week), and dynamic metric selection .
  - **Donut Charts:** Orders by Income Level and Occupation .
  - **Top 100 Customer Table:** List of top customers with data bars and color scale conditional formatting .
  - **Top Customer Callouts:** Text cards specifically highlighting the Name, Orders, and Revenue of the #1 top customer .

- **Interactive Elements:**
  - **Slicers:** Year slicer to filter the entire page .
  - **Bookmarks:** "Customer Insight" (saved view) and "Clear All Filters" (reset view) linked to action buttons .

---

## VIII. Success Criteria

The project is successful if it delivers:

- Accurate and validated KPI calculations .
- Clean, intuitive, and interactive dashboards .
- Clear insights into sales, returns, and customer behavior .
- A scalable data model suitable for future enhancements .
