# Plant-Co.-Global-Performance


##   Table of Contents

- [Project brief](#Projectbrief)
- [Objective](#Objective)
- [Data Architecture](#DataArchitecture)
- [Key Questions to Answer](#KeyQuestionstoanswer)
- [Data source](#Datasource)
- [Tools](#Tools)
- [Dashboard](#Dashboard)
- [Stages](#Stages)
- [Data processing & Transformation](#DAX-Implementation)
- [Insights & Findings](#Insights)
- [Recommendations](#Recommendations)



# Project brief 
Plant Co. Global Performance Analytics Dashboard - This is a multi-dimensional analysis of Sales, Quantity, and Gross Profit performance.



# Objective
This Power BI project provides a 360-degree view of Plant Co.’s 2023 performance. The dashboard is designed for senior management to monitor healthy growth by analyzing the intersection of sales volume, revenue, and profit margins. By integrating Time Intelligence and Account Segmentation, the report identifies specific areas of underperformance where volume may be increasing but profitability is lagging.


# Data Architecture 


# Questions


# Tools

| --- | --- | 
| Power BI , DAX, Power Query | 


# Dashboard


# Stages


# Processing & Transformation
Data Modeling: Created a star schema to ensure optimized performance and accurate filtering across multiple dimensions (Time, Product, Geography).

DAX Calculations: Developed complex DAX measures for Time Intelligence, including:

YTD Sales = TOTALYTD(SUM(Sales[Amount]), 'Date'[Date])

PYTD Sales = CALCULATE([YTD Sales], SAMEPERIODLASTYEAR('Date'[Date]))

GP% = DIVIDE([Total Gross Profit], [Total Sales])

# Insights , Findings

- Year-to-Date (YTD) vs. Prior Year (PYTD) Analysis
Performance Tracking: A primary KPI section tracks total YTD Sales ($13.00M) against PYTD ($13.51M), highlighting a negative variance of $512K.

Waterfall Analysis: The "Sales YTD vs PYTD by Month" waterfall chart provides a clear narrative of seasonal fluctuations, showing significant monthly dips in February and November.

2. Account Profitability Segmentation
Scatter Plot Analysis: I used a scatter plot to segment accounts by Gross Profit % vs. Sales. This allows stakeholders to identify high-volume, low-margin "risk" accounts versus high-margin "premium" accounts.

Dynamic Filtering: The implementation of x-axis and y-axis sliders allows for real-time segmentation of the customer base.

3. Product & Regional Performance
Product Categorization: Stacked bar charts break down performance by product type (Indoor, Landscape, Outdoor) and Product Size (Small, Medium, Large).

Geospatial Mapping: A global map visualization tracks YTD sales by country, providing a spatial understanding of the company's market footprint across North America, Europe, and Asia.

# Recommendations
