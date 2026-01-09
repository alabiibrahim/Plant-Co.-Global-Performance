# Plant Co. Global Performance

![GIF](Images/PlanGIF.gif)

##   Table of Contents

- [Project brief](#Projectbrief)
- [Data Architecture](#DataArchitecture)
- [Questions](#Questions)
- [Data source](#Datasource)
- [Tools](#Tools)
- [Dashboards](#Dashboard)
- [Chart types and why](#ChartTypesandWhy?)
- [Stages](#Stages)
- [Data Transformation](#Transformation)
- [Findings](#Findings)
- [Recommendations](#Recommendations)
- [challenges&solution](#Chalenges&Solution)



## Project brief 

This project features a 3 page, interactive Power BI dashboard designed for Plant Co. to monitor global performance across three key business pillars: Sales, Quantity, and Gross Profit.

The dashboard provides a detailed breakdown experience, allowing stakeholders to identify not just what happened in 2023, but why it happened by comparing Year-to-Date (YTD) performance against the Previous Year (PYTD).


## Data Architecture 

![DataModeling](Images/Data%20Modeling.PNG)

This project is built on a Star Schema architecture, optimized for analytical performance, scalable reporting, and reliable DAX calculations in Power BI.

- Fact Table: contains transactional sales data acting as a central table connecting all business dimensions with key metrics (Quantity, Sales, COGs). 

- Plant_Products Table: This here contains the product attributes and hierarchy to help in analysis with product size, type, group e.t.c

- Accounts Table: Contains customer and account information includes geographic and location for regional a nalysis.

- Calendar Table: Created to help in time intelligence analysis. It helps in calculating YTD, PYTD and SAMEPERIODLASTYEAR.

- Measures Table: This is not connected to other table but used for all DAX measures to help in reusability, readability.

- Slic_Values: This is also diconnected from other tables. It helps in calculating dynamic slicers measures and a conditional measures.Also, this slicers is not connected intentionally as to be flexible.


### Benefit of data modeling

- Improves query performance and report responsiveness

- Simplifies DAX logic by enforcing a single-direction filter flow

- Ensures accurate time-intelligence calculations

- Follows industry best practices for Power BI and enterprise BI solutions.


## Questions


## Data Source

![Data](https://github.com/alabiibrahim/Plant-Co.-Global-Performance/blob/main/Datasets/Plant%20co.DTS.xls)

## Tools

| Tools | Purpose | 
| --- | --- | 
| Power BI | DAX, Power Query | 


## Stages 
- Load data to Power Query, Standardize data-types and remove duplicates.
- Create a 'calendar' table and toggle button to view across 3 pillars of business. (Quantity, Sales and Gross Profit).
- Data modeling. Create DAX measures. 


## Chart types and Why? 

- Card Visuals - Shows the KPIs metrics (YTD, PYTD and GP%), and also the dynamic report title.

- Scatter Charts - Shows accouint segmentation by GP % vs Sales. This allows stakeholders to identify high-volume, low-margin "risk" accounts versus high-margin "premium" accounts.

- Waterfall charts - Shows the "YTD vs PYTD" comparison by Month, to provide a clear narrative of seasonal fluctuations.

- Map - Shows the global YTD Sales, Quantity and GP %  by country, providing a spatial understanding of the company's market footprint.

- Stacked Bar chart - Helps show the break down performance by product type (Indoor, Landscape, Outdoor).

- Column chart - Display the breakdown performance by Product Size (Small, Medium, Large)


## Dashboard

![Dashboard](Images/Plant1.PNG)

![Dashboard](Images/Plant2.PNG)

![Dashboard](Images/Plant3.PNG)


## Data Transformation

Here are the DAX formulas used in this project:

- Sales = SUM('Fact'Sales_USD)
        - This measure total all sales values from the Fact table.  

- Qty = SUM('Fact'Quantity)
        - This measure total all quantity from the Fact table.

- COGs = SUM('Fact'COGS_USD)
        - This measure total the Cost of Good sold from the Fact table  

- GrossProfit = COGs - Sales
        - This measure subtract the COGs from Sales to get the Gross Profit.

- YTD Sales = TOTALYTD('Measures'[Sales], 'Calendar'[Date]) 
        - This measure calculate the sales value from the start of the year to the end. 

- PYTD Sales = CALCULATE([YTDSales], SAMEPERIODLASTYEAR('Calendar'[Date]))
      - This measure calculate the YoY comparison. Just as seen in the waterfall chart.

GP% = DIVIDE([GrossProfit], [Sales])

// Calculate Sales for the same period last year
Sales PYTD = CALCULATE([Sales YTD], SAMEPERIODLASTYEAR('Calendar'[Date]))

// Calculate Quantity for the same period last year
Quantity PYTD = CALCULATE([Qty YTD], SAMEPERIODLASTYEAR('Calendar'[Date]))


## Findings

- Sales ($13.00M YTD). Quantity (555.66K Units YTD). Gross Profit ($5.15M YTD).

- Despite a strong Q2, a significant dip in November (-$0.23M) contributed to a total YTD deficit of $512K compared to the prior year.

- While Sales and Gross Profit are down, Quantity is actually UP by 17K units. This indicates that the company is moving more products but at lower price points or higher costs, a critical insight for the pricing strategy team.

- The Gross Profit margin remains stable at 39.62%, though total profit is down $265K YTD, driven largely by the "Large" and "Medium" product segments.


## Recommendations

- Since Quantity is up but Revenue is down, the company should investigate if aggressive discounting or a shift toward "Small" lower-priced products is eroding the top line.

- The "Large" product size category shows significant YTD vs PYTD variance; a targeted campaign for large-scale landscape products could recover the $512K sales gap.

- High-density sales clusters in Europe suggest a strong market fit; expanding successful European marketing tactics to underperforming regions could stabilize Q4 results.


## Challenges & Solution 

1. The stakeholders needed to see Sales, Quantity, and Gross Profit performance, but putting all three on one page created a cluttered and "noisy" dashboard that was hard to read.

    - How I solved it: I created a "Slicer Table" for easy toggling between 3 key pillars of business using DAX. This allowed the user to switch the entire context of the page with one click, maintaining a clean and simple report while providing three times the analytical depth.

2. Standard YTD functions can sometimes fail if the fiscal calendar is non-standard or if there are gaps in the data, leading to misleading variance figures.

    - How I solved it: I created a Date Table and utilized SAMEPERIODLASTYEAR combined with TOTALYTD logic to ensure the waterfall charts accurately show comparisons for the $512K sales variance.

3. With hundreds of accounts, a standard bar chart was insufficient for identifying profitability outliers.

    - How I solved it: I used a Scatter Plot with a Profitability Quadrant. By adding a constant line at the 20K sales mark and a GP% axis, I created an instant visual diagnostic tool to separate "High-Volume/Low-Margin" accounts from "Premium" partners.

