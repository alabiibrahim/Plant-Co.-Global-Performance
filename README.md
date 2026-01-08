# Plant-Co.-Global-Performance


##   Table of Contents

- [Project brief](#Projectbrief)
- [Data Architecture](#DataArchitecture)
- [Key Questions to Answer](#KeyQuestionstoanswer)
- [Data source](#Datasource)
- [Tools](#Tools)
- [Dashboard & Charts](#Dashboard)
- [Stages](#Stages)
- [Data processing & Transformation](#DAX-Implementation)
- [Insights & Findings](#Insights)
- [Recommendations](#Recommendations)
- [challenges and solution](#chalengesandsolution)



# Project brief 

This project features a 3 page, interactive Power BI dashboard designed for Plant Co. to monitor global performance across three key business pillars: Sales, Quantity, and Gross Profit.

The dashboard provides a detailed breakdown experience, allowing stakeholders to identify not just what happened in 2023, but why it happened by comparing Year-to-Date (YTD) performance against the Previous Year (PYTD).


# Data Architecture 
A snaphot of the data modeing star schema

# Questions


## Tools

| Tools | Purpose | 
| --- | --- | 
| Power BI | DAX, Power Query | 


# Chart types and Why? 

- Card Visuals - Shows the KPIs metrics (YTD, PYTD and GP%), and also the dynamic report title.

- Scatter Charts - Shows accouint segmentation by GP % vs Sales. This allows stakeholders to identify high-volume, low-margin "risk" accounts versus high-margin "premium" accounts.

- Waterfall charts - Shows the "YTD vs PYTD" comparison by Month, to provide a clear narrative of seasonal fluctuations.

- Map - Shows the global YTD Sales, Quantity and GP %  by country, providing a spatial understanding of the company's market footprint.

- Stacked Bar chart - Helps show the break down performance by product type (Indoor, Landscape, Outdoor).

- Column chart - Display the breakdown performance by Product Size (Small, Medium, Large)

# Dashboard


# Stages 
- Load data to Power Query, Standardize data-types and remove duplicates.
- Create a 'calendar' table and toggle button to view across 3 pillars of business. (Quantity, Sales and Gross Profit).
- Data modeling. Create DAX measures. 


# Processing & Transformation
Data Modeling: Created a star schema to ensure optimized performance and accurate filtering across multiple dimensions (Time, Product, Geography).

DAX Calculations: Developed complex DAX measures for Time Intelligence, including:

YTD Sales = TOTALYTD(SUM(Sales[Amount]), 'Calendar'[Date])

PYTD Sales = CALCULATE([YTD Sales], SAMEPERIODLASTYEAR('Calendar'[Date]))

GP% = DIVIDE([Total Gross Profit], [Total Sales])

# Insights , Findings

- Total YTD Sales ($13M) against PYTD ($13.51M), highlighting a negative variance of $512K.

Sales Performance ($13.00M YTD)
Goal: Monitor top-line revenue health.

Key Finding: Despite a strong Q2, a significant dip in November (-$0.23M) contributed to a total YTD deficit of $512K compared to the prior year.

2. Global Quantity Performance (555.66K Units YTD)
Goal: Track inventory movement and market demand.

Key Finding: While Sales and Gross Profit are down, Quantity is actually UP by 17K units. This indicates that the company is moving more products but at lower price points or higher costs, a critical insight for the pricing strategy team.

3. Gross Profit Performance ($5.15M YTD)
Goal: Analyze bottom-line efficiency.

Key Finding: The Gross Profit margin remains stable at 39.62%, though total profit is down $265K YTD, driven largely by the "Large" and "Medium" product segments.

# Recommendations

Pricing Analysis: Since unit volume (Quantity) is up but Revenue is down, the company should investigate if aggressive discounting or a shift toward "Small" lower-priced products is eroding the top line.

Product Strategy: The "Large" product size category shows significant YTD vs PYTD variance; a targeted campaign for large-scale landscape products could recover the $512K sales gap.

Regional Focus: High-density sales clusters in Europe suggest a strong market fit; expanding successful European marketing tactics to underperforming regions could stabilize Q4 results.
