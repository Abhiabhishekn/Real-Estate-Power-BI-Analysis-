Power BI Project Documentation

Project Portfolio Analytics Dashboard
Prepared by: Abhishek Naithani
THIS DOCUMENT OUTLINES THE DATA PREPARATION, MODELING APPROACH, AND DASHBOARD DESIGN FOR THE

PROJECT PORTFOLIO ANALYTICS SOLUTION

1. Objective
The objective of this project was to build an interactive Power BI solution that allows stakeholders to:
• Monitor overall project performance
• Analyze financial metrics such as Budget, Actuals, and Forecast
• Understand how the project portfolio is structured
• Identify risk areas using slippage and variance
• Explore project-level data without writing SQL queries

The focus was to create a clear and structured dashboard experience for both technical and non-
technical users.

2. Data Preparation and Transformation
2.1 Source Data
The dataset contained:
• Project-level details (Project ID, Name, Status, Division, Business Line, etc.)
• Financial data across multiple years (CAPEX, OPEX, Forecast, Slippage)
2.2 Data Cleaning (Power Query)
The raw data was not in a reporting-friendly format, so the following steps were performed:
Unpivoting Financial Columns
The dataset originally had multiple columns such as:
• 2026 Actual CAPEX
• 2026 Forecast OPEX
• 2027 Total Forecast
• 2028 Net Forecast

These were unpivoted into a structured format:
• Metric → Stores original column name
• Amount → Stores the value
This made the dataset flexible for analysis and visualization.
Creating Derived Columns
To improve usability, the following columns were created:
• Year
Extracted from the metric name (2026, 2027, 2028)
• Type
Categorized into:
o Actual
o Forecast
• Category
Standardized into:
o CAPEX
o OPEX
o Total
o Slippage

This step was important to ensure consistency across all dashboards.
Handling Data Quality
• Null values were retained where appropriate (as they represent real scenarios)
• Data types were corrected (Currency, Percentage, Date)
• Column names were standardized for clarity
• There were no duplicates found in the dataset based on Project ID

3. Data Model
The model was designed using a star schema approach:
• Projects (Dimension Table)
Contains unique project-level information

• Financials (Fact Table)
Contains financial metrics such as Amount, Category, Year, and Type

Relationship
• Relationship created on Project ID
• Cardinality: One-to-Many (Project → Financial)
• Cross-filter direction: Single
This structure ensures:
• clean filtering
• better performance
• scalable design

4. Dashboard Overview
The solution consists of four dashboards and one detail explorer page, each focusing on a specific
business area.
4.1 Dashboard 1: Project Portfolio Performance Overview
Purpose
To provide a high-level summary of overall performance.
Key Visuals
• KPI cards (Total Actual, Total Budget, Total Forecast)
• Actual vs Forecast by Year
• CAPEX vs OPEX distribution
• Slippage by Division
Intent
This dashboard is designed for leadership to quickly understand:
• overall financial performance
• spending structure
• areas that may require attention

4.2 Dashboard 2: Financial Analysis & Spend Breakdown
Purpose
To provide a deeper view into financial data.
Key Visuals
• CAPEX vs OPEX by Year
• Forecast trend over time
• Spending by Business Line
• Project-level financial table (With Conditional Filtering & Actions)
Intent
This dashboard helps in:
• understanding cost distribution
• identifying key spending areas
• analyzing financial trends across years
4.3 Dashboard 3: Project Portfolio & Operational Overview
Purpose
To analyze the operational side of the portfolio.
Key Visuals
• Project Status Distribution
• Project Pipeline by Year
• Funding Status Distribution
• Project-level table (With Conditional Filtering & Actions)
Intent
This dashboard provides visibility into:
• project lifecycle stages
• pipeline growth over time
• funding allocation

4.4 Dashboard 4: Risk & Slippage Analysis
Purpose
To highlight risk areas and performance gaps.
Key Visuals
• Slippage by Division (%)
• Top Projects by Slippage (%)
• Top Projects by Variance ($)
Intent
This dashboard allows stakeholders to:
• identify high-risk divisions
• focus on projects with the highest delays
• understand deviations between budget and forecast
4.5 Project Data Explorer
Purpose
To provide a self-service interface for detailed data exploration.
Features
• Fully filterable table
• Slicers for:
o Business Line
o Year
o Division
o Project Name
o Category
o Project Status

Intent
This page allows users to:
• explore project-level records
• validate dashboard insights
• work with the data without requiring SQL

5. Interactivity and Design Approach
• Slicers were synchronized across dashboards to maintain consistency
• Visuals were kept simple and focused for better readability
• Top N filtering was used to highlight key projects
• Layouts were kept consistent across all pages
The overall design focuses on clarity, usability, and structured storytelling.

6. Conclusion
This Power BI solution provides a complete view of the project portfolio by combining:
• Executive-level insights
• Financial analysis
• Operational visibility
• Risk identification
• Detailed data exploration
The dashboards are designed to support support data-driven decision making while remaining easy to use for all
stakeholders.
