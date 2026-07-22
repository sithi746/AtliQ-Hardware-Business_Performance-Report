# AtliQ Hardware Sales Analysis 

---

## 
**AtliQ Hardware Sales Report** – Monitor sales performance across markets, customers, products, and divisions to uncover growth opportunities and performance gaps.  

---

##  Purpose
This dashboard transforms raw sales and target data into a **structured, actionable analytics tool**, enabling stakeholders to:  
- Track overall revenue performance  
- Compare actuals vs targets  
- Identify top-performing products and customers  
- Make data-driven strategic decisions  

---

## Tech Stack
- **Data Modeling & Transformation:** Excel Power Query, Power Pivot  
- **Analytics & Reporting:** DAX, Power BI / Excel  
- **Data Storage:** Fact & Dimension tables (Snowflake schema)  


---

## Data Source
| Table | Description |
|-------|------------|
| `fact_sales_monthly` | Transactional sales data |
| `ns_targets_2021` | Market-level sales targets |
| `dim_customer` | Customer info (platform, channel) |
| `dim_product` | Product hierarchy (division, segment, category) |
| `dim_market` | Market, sub-zone, region hierarchy |
| `dim_date` | Date, month, fiscal year |

---

##  Data Model
The dashboard uses a **Snowflake-schema** for multi-dimensional analysis:  

![Data Model](https://github.com/sithi746/AtliQ-Hardware-Sales-Performance-Report/blob/main/Data-model.png)  
*Fact tables link to normalized dimensions for efficient querying and comparisons.*  

---
##  Measures Created
1. net_sales
=SUM(fact_sales_monthly[net_sales_amount])

2. net_sales_19
=CALCULATE([net_sales], dim_date[fy]="2019")

3. net_sales_20
=CALCULATE([net_sales], dim_date[fy]="2020")

4. net_sales_21
=CALCULATE([net_sales], dim_date[fy]="2021")

5. target_21
=SUM(ns_targets_2021[ns_target])

6. 2021-Target
=[net_sales_21]-[target_21]

7. 21_vs_20
=DIVIDE([net_sales_21]-[net_sales_20], [net_sales_20], 0)

8. %
=DIVIDE([2021-Target],[target_21], 0)

##  Features 

### Business Problem
- Disconnected data across multiple sources  
- Difficulty tracking sales, targets, and growth gaps  

### Goal of the Report
- Consolidate data for actionable insights  
- Track performance vs targets across markets, customers, and products  

### Report Walkthrough
- **Revenue KPI:** Total net sales & YoY growth  
- **Market & Customer Analysis:** Top-performing regions & clients  
- **Product & Division Insights:** Top/bottom products & division report
- **Target vs Actual:** performance gaps  

 

### Business Impact & Insights
- **Revenue:** $598.9M, 21 vs 20 growth 304.5%
- **Top Markets:** India $161.3M, USA $87.8M  
- **Top Customer yoy growth:** Nova 2664.9%
- **High-Growth Divisions:** PC +313.7%, P&A +221.5%  
- **Top Products:** AQ mx nb, AQ Smash 2  
- Recommendations: improve forecasting, scale high-performing products, rationalize underperformers, invest strategically in top divisions


## Conclusion
In 2021, AtliQ Hardware achieved remarkable growth, fueled by expanding customer reach, successful new products, and strong digital sales channels. While the company demonstrates excellent market scalability, closing performance gaps and optimizing product and regional results will be essential to maintain sustainable long-term growth.

