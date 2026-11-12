# AtliQ Hardware Business Performance Analysis


## 
**AtliQ Hardware Sales & Finance Report** – Monitor sales & Finance performance across markets, customers, products, Fiscal year, Quarter months and divisions to uncover growth opportunities and performance gaps.  

---

##  Purpose
This report transforms raw sales, financial, and target data into a structured, actionable analytical resource, enabling stakeholders to:

-Track overall revenue performance and sales growth

-Analyze profit and loss (P&L) statements, cost of goods sold (COGS), and gross margins

-Compare actual sales against regional and market targets

-Identify top-performing products, customer accounts, and divisions

-Uncover commercial growth opportunities and address performance gaps to make data-driven strategic decisions

---

## Tech Stack
- **Data Modeling & Transformation:** Excel Power Query, Power Pivot  
- **Analytics & Reporting:** DAX, Power BI / Excel  
- **Data Storage:** Fact & Dimension tables (Star schema)  


---

## Data Source
| Table | Description |
|-------|------------|
| `fact_sales_monthly` | Transactional sales data |
| `ns_targets_2021` | Market-level sales targets |
| `dim_customer` | Customer info (Market,platform, channel) |
| `dim_product` | Product hierarchy (division, segment, category) |
| `dim_market` | Market, sub-zone, region hierarchy |
| `dim_date` | Date, month, fiscal year |

---

##  Data Model
The dashboard uses a **Star-schema** for multi-dimensional analysis:  

![Data Model](https://github.com/sithi746/AtliQ-Hardware-Sales-Performance-Report/blob/main/DATA%20MODEL.png)  
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

8.  2021-Target %
=DIVIDE([2021-Target],[target_21], 0)

9. total_cogs
=SUM('fact-sales-monthly'[COGS])

10. gross_margin
=[net_sales]-[total_cogs]  

11. gross_margin%
=DIVIDE([gross_margin], [net_sales], 0)

##  Features 

### Business Problem
- Disconnected data across multiple sources  
- Difficulty tracking sales, Finance, targets, and growth gaps  

### Goal of the Report
The primary goal of the AtliQ Hardwares finance and sales report is to evaluate enterprise performance across global markets, customer accounts, and product lines to identify growth opportunities and optimize profitability.
### Key Objectives:
- Track Revenue Growth: Monitor net sales expansion and YoY trends (FY2019–2021).
- Analyze Profitability: Evaluate P&L statements, COGS, and gross margins across divisions.Assess 
- Market Targets: Measure actual sales against target benchmarks to spot regional variances.Identify 
- Key Drivers: Highlight top customers, high-volume products, and core business divisions (P&A, PC, N&S).
- Guide Decisions: Resolve performance gaps and optimize resource allocation using financial insights.   

### Report Walkthrough
- **Revenue KPI:** Total net sales & YoY growth  
- **Market & Customer Analysis:** Top-performing regions & clients  
- **Product & Division Insights:** Top/bottom products & division report
- **Target vs Actual:** performance gaps
- **Financial & P&L Analysis:** Gross margins, COGS breakdown, and overall profitability trends

 

### Business Impact & Insights
- Revenue Growth: Generated $598.9M in net sales in FY2021, representing 204.48% YoY growth.
- Profitability: Achieved $218.2M in gross margin with a 36.43% gross margin percentage.
- Cost Analysis: Total Cost of Goods Sold (COGS) reached $380.7M, highlighting the importance of cost control alongside revenue growth.
- Margin Performance: Gross margin percentage declined from 37.28% in FY2020 to 36.43% in FY2021, indicating slight margin compression despite strong sales growth.
- Top Markets: India ($161.3M) and USA ($87.8M) led revenue contribution.
- Division Growth: PC (+313.7%) and P&A (+221.5%) recorded the strongest YoY sales growth.
- Target vs. Actual: Sales performance fell short of targets by $54.9M (9.2%) in FY2021.
- Product Performance: AQ Electron 4 3600 Desktop Processor ($19.4M) and AQ Smash 2 ($11.2M) were among the leading products by revenue in the top-growth product analysis.

**Note:** All business impact metrics and insights are based on the default report view (all filters selected). The interactive dashboard enables dynamic analysis of revenue, profitability, gross margins, COGS, market performance and product trends across different dimensions using slicers and filters.

## Business Recommendations
In FY2021, AtliQ Hardwares recorded significant sales growth, supported by strong customer reach, product performance, and digital sales channels. One interesting finding was that AtliQ generated around $598.9 million in sales in FY2021, but its gross margin percentage declined from 41.43% in FY2019 to 36.43% in FY2021. It also missed its sales target by approximately $54.9 million.
This revealed that strong sales growth was not necessarily translating into stronger profitability.
The project helped identify where management could investigate further—whether in underperforming markets, customer performance, or pricing and discount strategies.

*My key takeaway was that data is not just about understanding what happened; it's about helping a business understand why it happened and where it should focus next.*
 If I were presenting this to the management team, my core recommendation would be that AtliQ must shift from volume expansion to margin protection,
 They can achieve this by tightening discount controls, promoting higher-margin products.

