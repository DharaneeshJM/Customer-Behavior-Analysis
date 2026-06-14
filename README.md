# Customer Shopping Behavior Analysis

An end-to-end data analytics project that explores customer shopping behavior using a transactional dataset of 3,900 purchases. The project covers data cleaning and EDA in Python, business analysis using SQL, an interactive Power BI dashboard, a written report, and a presentation summarizing key findings.

## 1. Overview

This project analyzes customer demographics, purchase patterns, product preferences, and subscription behavior to generate actionable business insights. The workflow follows a complete analytics pipeline: load and clean data in Python, run business queries in SQL, visualize results in Power BI, and present findings via a report and presentation deck.

**Key questions explored:**
- How does revenue differ between male and female customers?
- Which customers spend above average even with discounts applied?
- What are the top-rated and best-selling products?
- Do subscribers spend more than non-subscribers?
- How are customers segmented (New, Returning, Loyal)?
- Which age groups and shipping types drive the most revenue?

## 2. Dataset

- **Source file:** `customer_shopping_behavior.csv`
- **Rows:** 3,900
- **Columns:** 18

**Key fields:**
- **Demographics:** Customer ID, Age, Gender, Location
- **Purchase details:** Item Purchased, Category, Purchase Amount (USD), Season, Size, Color
- **Shopping behavior:** Discount Applied, Promo Code Used, Previous Purchases, Frequency of Purchases, Review Rating, Subscription Status, Shipping Type, Payment Method

**Data quality notes:**
- 37 missing values in the `Review Rating` column, imputed using the median rating per product category
- `promo_code_used` found to be redundant with `discount_applied` and dropped during cleaning

## 3. Tools Used

| Tool | Purpose |
|------|---------|
| Python (pandas) | Data loading, cleaning, EDA, feature engineering |
| PostgreSQL | Business query analysis using SQL |
| Power BI | Interactive dashboard and visualization |
| Gamma | Presentation (PPT) creation |
| Word / PDF | Final written report |

## 4. Project Steps

### Step 1: Data Loading & Exploration (Python)
- Loaded the dataset using `pandas`
- Explored structure with `df.info()` and summary statistics with `.describe()`

### Step 2: Data Cleaning (Python)
- Identified and imputed 37 missing values in `Review Rating` using the median rating per category
- Standardized all column names to snake_case
- Checked redundancy between `discount_applied` and `promo_code_used`, and dropped `promo_code_used`

### Step 3: Feature Engineering (Python)
- Created `age_group` by binning customer ages (Young Adult, Adult, Middle-aged, Senior)
- Created `purchase_frequency_days` from the frequency-of-purchase field

### Step 4: Database Integration
- Connected the cleaned Python DataFrame to PostgreSQL
- Loaded the cleaned dataset into a `customer` table for SQL analysis

### Step 5: SQL Analysis (`customer_behavior.sql`)
Ran 10 business queries, including:
1. Total revenue by gender
2. Customers using discounts who still spent above the average purchase amount
3. Top 5 products by average review rating
4. Average purchase amount: Standard vs. Express shipping
5. Subscribers vs. non-subscribers — average spend and total revenue
6. Top 5 products by discount usage rate
7. Customer segmentation (New, Returning, Loyal) by previous purchases
8. Top 3 products per category
9. Repeat buyers (>5 purchases) vs. subscription status
10. Total revenue by age group

### Step 6: Dashboard (Power BI)
Built an interactive **Customer Behavior Dashboard** with:
- Total customers, average purchase amount, and average review rating (KPI cards)
- Subscription status breakdown (donut chart)
- Revenue and sales by category (bar charts)
- Revenue and sales by age group (bar charts)
- Filters/slicers for gender, category, shipping type, and subscription status

### Step 7: Reporting & Presentation
- Compiled findings into a written report (`Customer_Shopping_Behavior_Analysis.pdf`)
- Created a summary presentation deck using **Gamma** (`Customer-Shopping-Behavior-Analysis.pptx`)

## 5. Dashboard Preview

The Power BI dashboard provides at-a-glance KPIs and breakdowns by category, age group, and subscription status, with interactive filters for gender, shipping type, and category.

## 6. Key Results & Insights

- **Revenue by Gender:** Male customers generated significantly higher total revenue (~$157,890) compared to female customers (~$75,191)
- **Top-Rated Products:** Gloves, Sandals, Boots, Hat, and Skirt have the highest average review ratings (3.78–3.86)
- **Shipping:** Express shipping customers spend slightly more on average ($60.48) than Standard shipping customers ($58.46)
- **Subscriptions:** Non-subscribers (2,847 customers) generate far more total revenue (~$170,436) than subscribers (1,053 customers, ~$62,645), though average spend per customer is similar
- **Discount-Driven Products:** Hat, Sneakers, Coat, Sweater, and Pants have the highest share of discounted purchases (47–50%)
- **Customer Segments:** Most customers (3,116) fall into the "Loyal" segment, with 701 "Returning" and only 83 "New"
- **Top Products by Category:** Jewelry, Sunglasses, and Belt lead Accessories; Blouse, Pants, and Shirt lead Clothing; Sandals, Shoes, and Sneakers lead Footwear; Jacket and Coat lead Outerwear
- **Repeat Buyers:** Customers with more than 5 previous purchases are mostly non-subscribers (2,518 vs. 958)
- **Revenue by Age Group:** Young Adults contribute the most revenue (~$62,143), followed by Middle-aged, Adult, and Senior groups (all fairly close, ~$55,000–$59,000)

## 7. Business Recommendations

- **Boost Subscriptions** – Promote exclusive benefits to convert non-subscribers, who currently drive most revenue
- **Customer Loyalty Programs** – Reward repeat buyers to strengthen the already-large "Loyal" segment
- **Review Discount Policy** – Balance discount-driven sales with margin control for heavily discounted products
- **Product Positioning** – Highlight top-rated and best-selling products in marketing campaigns
- **Targeted Marketing** – Focus on high-revenue age groups (Young Adults) and express-shipping customers

## 8. How to Run This Project

1. **Set up environment**
   ```bash
   pip install pandas sqlalchemy psycopg2-binary
   ```

2. **Load and clean the data (Python)**
   - Open the analysis notebook/script
   - Load `customer_shopping_behavior.csv` using `pandas`
   - Run the cleaning and feature engineering steps (missing value imputation, snake_case columns, age_group creation, etc.)

3. **Load data into PostgreSQL**
   - Create a database and a `customer` table
   - Use the cleaned DataFrame's `.to_sql()` method (via SQLAlchemy) to load the data

4. **Run SQL queries**
   - Open `customer_behavior.sql` in PostgreSQL (pgAdmin, DBeaver, or psql)
   - Execute each query (Q1–Q10) to reproduce the business analysis results

5. **Build/refresh the Power BI dashboard**
   - Connect Power BI to the PostgreSQL database (or the cleaned CSV)
   - Recreate or refresh the visuals: KPI cards, category/age group charts, subscription donut chart, and slicers

6. **View the report and presentation**
   - `Customer_Shopping_Behavior_Analysis.pdf` — full written report
   - `Customer-Shopping-Behavior-Analysis.pptx` — summary presentation (built with Gamma)

## 9. Project Files

| File | Description |
|------|-------------|
| `customer_shopping_behavior.csv` | Raw dataset (3,900 rows, 18 columns) |
| `customer_behavior.sql` | SQL queries for business analysis |
| `Customer_Shopping_Behavior_Analysis.pdf` | Full written report with EDA and SQL results |
| `Customer-Shopping-Behavior-Analysis.pptx` | Presentation summary |
| Power BI dashboard file (.pbix) | Interactive dashboard |

---
*This project demonstrates an end-to-end data analytics workflow: Python for data preparation, SQL for business analysis, Power BI for visualization, and Gamma for presentation — built as a portfolio project to showcase practical data analysis skills.*
