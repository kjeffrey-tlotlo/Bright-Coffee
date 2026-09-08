##📌 Project Overview
Bright Coffee Shop provided a raw transactional dataset covering three store locations. This project walks through the full analytics workflow — from planning and architecture, through data processing and cleaning, to visualization and CEO-ready recommendations.

##Business questions answered:**

•	Which products generate the most revenue?
•	What time of day does the store perform best?
•	What are the sales trends across products and time intervals?
•	What actions can improve overall sales performance?

🗂️ ##Repository Structure

├── 01-planning/
│   └── data-flow-architecture-diagram.pdf   # Miro plan: source → ETL → storage → analysis
├── 02-data-processing/
│   ├── bright_coffee_shop_sales.csv         # Raw data converted to CSV
│   └── transformations.sql                  # SQL used in Databricks for cleaning & transforms
├── 03-analysis/
│   └── Bright_Coffee_Data_Inspection.xlsx   # Processed dataset, pivot tables & charts
├── 04-presentation/
│   └── Bright_Coffee_Shop_Analysis_CEO_Deck.pptx   # Final presentation to the CEO
└── README.md

🧰 ##Tools Used
##Stage                               ##Tool(s)
Planning & Architecture	              Miro
Data Processing / ETL	Databricks,     SQL
Data Analysis & Visualization	        Microsoft Excel (Pivot Tables & Charts), Databricks, Data Studio,Power BI
Presentation & Reporting	            PowerPoint

🔄 ##Data Flow & Architecture
	Source: Raw transactional sales data (Excel) from 3 store locations.
	ETL Pipeline (Databricks):
	Converted the source Excel file to CSV.
	Loaded the CSV into Databricks.
	Cleaned unit_price values that used comma decimal separators (e.g., '3,1' → 3.1).
	Computed total_amount = unit_price * transaction_qty.
	Created a transaction_time_bucket column, grouping each transaction into a time-of-day bucket (Morning, Afternoon, Evening, Night, Closing Hours).
	Used SQL to aggregate by product type, category, store location, and time bucket.
	Storage: Processed tables stored/queried in Databricks.
	Analysis & Presentation: Exported the processed table to Excel for pivot tables and charts, then summarized findings in a PowerPoint deck for the CEO.

📊 Dataset

| Column | Description |
|---|---|
| `transaction_id` | Unique transaction identifier |
| `transaction_date` / `transaction_time` | Date and time of sale |
| `store_id` / `store_location` | Store identifier and location (Hell's Kitchen, Astoria, Lower Manhattan) |
| `product_id` / `product_category` / `product_type` / `product_detail` | Product hierarchy (9 categories, 29 product types) |
| `transaction_qty` | Units sold in the transaction |
| `unit_price` | Price per unit |
| `total_amount` | Calculated: `unit_price × transaction_qty` |
| `time_bucket` | Engineered field: time-of-day segment |
| `day_type` | Day of the week |
| `month_name` | Month of transaction |
| `sales_value_category` | Engineered field: relative sales value bucket |

🔑## Key Insights

**Total Revenue**: $698,812 across 149,116 units sold, with an average order value of R1.44.
**Top revenue-driving products**: Barista Espresso (R91.4K), Brewed Chai Tea (R77.1K), Hot Chocolate (R72.4K), and Gourmet Brewed Coffee (R70.0K) lead the lineup.
**Time of day:** Mornings drive the most sales (32.8%), followed by Afternoon (24.8%) and Night (20.1%). Evening (17.9%) and Closing Hours (4.5%) are the weakest windows.
**Weekly trend:** Sales build steadily through the week, peaking on Saturday (~R698.8K cumulative) after a Monday low (~R101.7K), suggesting a strong weekend effect.
**Monthly trend:** June (23.7%) and May (22.5%) were the strongest months; February (11%) and January (11.6%) were the softest.
**Store performance:** All three locations perform similarly — Hell's Kitchen leads slightly in both transaction volume (50,735) and revenue (R236.5K), followed by Astoria (R232.2K) and Lower Manhattan (R230.1K).

💡 Recommendations

1.	Boost slow time slots — Launch marketing campaigns (discounts, loyalty pushes) targeting Evening and Closing Hours, the weakest sales windows.
2.	Double down on best-sellers — Ensure consistent stock of Barista Espresso, Brewed Chai Tea, and Hot Chocolate, the top revenue drivers.
3.	Promote underperforming products — Bundle or discount lower-selling items to lift their visibility and sales.
4.	Smooth out weekly demand — Consider early-week promotions (Monday–Wednesday) to balance the strong weekend skew.
5.	Replicate Hell's Kitchen's edge — Investigate what drives its slightly higher performance and apply learnings to Astoria and Lower Manhattan.





The dataset (Bright Coffee Shop Sales) contains 149,116 transactions with the following fields:
