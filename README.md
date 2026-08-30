## Procurement Performance and Insights

### Project overview 

This procurement analysis examines purchasing activity to provide a clear view of spending, supplier performance, delivery efficiency, quality, compliance, and cost savings.
Drawing on procurement data from Keggle, the project breaks down purchase orders, suppliers, item categories, quantities, pricing, delivery dates, defective units, and compliance status. The data preparation and querying were handled using SQL, and the findings were brought to life through an interactive Power BI dashboard designed for ongoing performance monitoring.
Ultimately, the analysis uncovers spending patterns across different suppliers and categories, tracks delivery reliability, audits compliance, measures defect rates, and calculates total procurement savings.


### Project Objectives 

 - Examining procurement activity across various suppliers and item categories
 - Calculating total procurement spend and tracking spending distribution by category
 - Evaluating supplier delivery performance and uncovering trends over time
 - Assessing overall procurement compliance
 - Identifying specific suppliers and categories driving high defective units and defect rates
 - Measuring procurement savings across different suppliers and categories
 - Delivering actionable insights to optimize both purchasing strategy and supplier manage


### Tools

 - PostgreSQL 
      - Used for data ingestion, data cleaning, transformation, calculated fields, and procurement analysis.

 - Power BI 
       - Used for data visualization, KPI development, dashboard design, and interactive analysis.



### Data Workflow 

 - Source
      - The raw procurement data originates from Kaggle, capturing a complete operational record of purchasing activity. This repository documents every transaction from purchase orders and supplier metrics to product categories, pricing structures, delivery timelines, defect counts, and regulatory compliance markers.

 - Ingestion 
       - The procurement dataset was imported into PostgreSQL to establish a structured foundation for data preparation, transformation, and analysis. Once the SQL-based preparation and analysis were finalized, the processed data was connected to Power BI for dashboard development and visual storytelling.
 
 - Cleaning
        - The dataset underwent a thorough review to identify data quality issues and ensure procurement records were fully prepared for analysis. Key fields required for procurement calculations and performance metrics were systematically checked for missing values and structural 

 - Transformation
       - SQL was used to create calculated fields required for the analysis, including Estimated Total Cost, Actual Total Cost, Saving per Unit, Total Saving, Good Units, and Delivery Days, which made it possible to analyze procurement spending, savings, product quality, and delivery performance.

 - Analysis
      - The SQL analysis focused on purchase volume, procurement spending, supplier performance, category spending, delivery performance, compliance, defective units, defective rates, procurement savings, and delivery trends, with queries used to aggregate and compare procurement data across suppliers, categories, dates, and performance measures.

 - Output
     - The final output was an interactive Power BI Procurement Analysis Dashboard containing KPI cards and visualizations covering procurement spending, supplier performance, delivery, quality, compliance, and savings, while the repository can also contain the SQL script used for the data preparation and analysis, allowing the analytical process to be reviewed separately from the dashboard.


### Key Metrics
 - Total Purchase Orders (777)
      - Indicates the total number of procurement orders analyzed.
 
 - Total Procurement Spend (₦45M)
       - Reflects the total procurement expenditure across the analyzed purchase orders.
 
 - Average Delivery Time (10.8 days)
       - Shows the average time taken for procurement orders to be delivered.
 
 - Compliance Rate (82.4%)
       - Captures the share of purchase orders recorded as compliant.
 
 - Defective Rate (5.6%)
        - Measures the overall share of defective units within the purchased quantity.
 
 - Total Savings (₦4M)
         - Signifies the total procurement savings achieved through negotiated pricing.
 
 - Total Quantity Purchased (851K units)
          - Indicates the total quantity procured across the purchase orders.


### Data Cleaning and Transformation

 - Before building the analytical calculations, the procurement dataset was reviewed in SQL to assess its structure, completeness, and consistency, and to prepare it for analysis in Power BI.

 - Dataset overview
       - The dataset contains 777 purchase orders with the following fields: Product ID, Supplier, Order Date, Delivery Date, Item Category, Order Status, Quantity, Unit Price, Negotiated Price, Defective Units, and Compliance.

 - Completeness checks

      - Delivery Date: only 690 of 777 records had a delivery date populated. Since Delivery Days depends on both Order Date and Delivery Date, incomplete records can’t produce a valid delivery-duration value.
      - Defective Units: 641 records had values recorded, which was verified before running any quality calculations (defective units, defective rate).
      - Other fields were also checked for missing values as part of the broader review.

 - Duplicate check
      - Records were checked for duplicates to prevent repeated entries from inflating purchase volumes, spend, defective units, or savings figures.

 - Consistency review
       - Supplier names, item categories, order/delivery dates, quantities, unit prices, negotiated prices, defective units, and compliance status were reviewed for consistency, ensuring the fields could be grouped and aggregated reliably.

 - Date validation
       - A check for cases where Delivery Date preceded Order Date found one inconsistent record. It was flagged and retained as-is rather than modified, preserving the original data while documenting the issue.
  

 - Calculated Fields

      - After completing the data quality checks, calculated fields were created to support the procurement analysis.

 - Estimated Total Cost
      - Calculated as Quantity × Unit Price. This represents the estimated procurement cost based on the original unit price.

 - Actual Total Cost
       - Calculated as Quantity × Negotiated Price. This represents the procurement cost based on the negotiated price.

 - Saving per Unit
        - Calculated as the difference between the original unit price and the negotiated price. This measures the saving achieved per unit through negotiated pricing.

 - Total Saving
        - Calculated as the difference between the estimated total cost and the actual total cost. This measures the total procurement saving achieved through negotiated pricing.

 - Good Units
       - Calculated as Quantity − Defective Units. This represents the quantity remaining after defective units are deducted.

 - Delivery Days
       - Calculated as Delivery Date − Order Date. This measures the number of days taken to fulfil each procurement order.

 - Aggregation
       - The cleaned and calculated dataset was grouped by Supplier, Item Category, Compliance Status, and Year, and summarized across Delivery Performance, Defective Units, Defective Rate, Procurement Spend, and Savings — preparing it for supplier, category, and time-based comparisons in the Power BI dashboard.


### Recommendations
 - Review suppliers with high defective unit
       - Delta Logistics recorded the highest number of defective units at 20K. The procurement team could review the supplier’s quality performance and investigate the factors contributing to the high defect volume.
 
 - Investigate Raw Materials quality
       - Raw Materials recorded the highest defective rate at 6.4%. The business could investigate the quality issues associated with this category and assess whether supplier or product-level factors may be contributing to the higher rate.
 
 - Monitor supplier delivery performance 
       - Gema CO recorded the shortest average delivery time at 10.19 days, while Better Suppliers recorded the longest at 11.27 days. Delivery performance could be monitored regularly to identify suppliers with consistently longer delivery times.
  
 - Review procurement negotiation practices
       - MRO generated the highest category savings at ₦902K, while Beta Suppliers recorded the highest supplier savings at ₦890K. The procurement team could review the pricing and negotiation practices associated with these savings and identify opportunities to apply effective approaches more broadly.
 
 - Investigate the 2024 delivery trend
       - Average delivery time declined from 10.8 days in 2023 to 3.0 days in 2024. The underlying records should be reviewed to understand what caused this change before treating it as a confirmed improvement in supplier performance.


### Assumptions
 - Delivery Days represents the difference between Delivery Date and Order Date.
 
 - Estimated Total Cost is based on Quantity multiplied by Unit Price.
 
 - Actual Total Cost is based on Quantity multiplied by Negotiated Price.
 
 - Total Saving represents the difference between estimated and actual procurement cost.
  
 - Defective Rate is based on defective units relative to total quantity purchased.
 
 - Compliance is based on the Yes/No compliance status recorded in the dataset.
 
 - The 851K total quantity represents the quantity procured rather than products sold.


### Limitations
 - The analysis is based on the available procurement records from the dataset.
 
 - The analysis identifies procurement patterns but does not establish the underlying causes of those patterns.
 
 - The reason for the substantial reduction in average delivery time in 2024 was not established in the current analysis.
  
 - Defective unit counts and defective rates measure different aspects of quality performance and should be interpreted together.
 
 - Compliance results are based on the compliance status recorded in the dataset and do not independently verify the underlying procurement requirements.
 
 - The analysis does not establish causation between supplier performance and the observed procurement outcomes.
