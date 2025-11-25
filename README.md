# Vendor-Performance-Analysis-Dashboard

📊 Project Overview

A comprehensive data analytics solution designed to optimize vendor performance and inventory management in wholesale retail. This project combines SQL, Python, and Power BI to transform millions of transaction records into actionable business insights, addressing critical supply chain risks and inventory inefficiencies.

🎯 Business Problem

The wholesale retail company faced critical operational challenges:

$2.71 Million locked in unsold inventory, restricting cash flow
65.7% purchase dependency on just 10 vendors, creating severe supply chain risk
Lack of visibility into vendor performance and inventory efficiency
No data-driven framework for procurement decisions

Objective: Build an end-to-end analytics solution to identify underperforming vendors, reduce inventory costs, diversify supply chain, and provide actionable recommendations to improve profitability by 15-20% annually.

👨‍💼 My Role

As an analyst, I managed the complete analytics lifecycle:

Data Engineering: Designed and implemented SQL database architecture
ETL Pipeline: Built automated data ingestion and cleaning workflows
Statistical Analysis: Conducted exploratory data analysis and hypothesis testing
Business Intelligence: Developed interactive Power BI dashboards
Strategic Consulting: Delivered data-driven recommendations to stakeholders


📁 Dataset Description

Source: 5 CSV files containing wholesale transaction data
Time Period: One year of operations
Raw Volume: Millions of vendor transaction records
Processed Dataset: 10,692 aggregated records
Data Components:

Purchases: Vendor transactions, quantities, unit prices
Sales: Product movement and revenue data
Inventory: Stock levels and turnover metrics
Invoices: Freight costs and payment details
Vendor Information: Supplier details and performance metrics


🛠️ Tools & Technologies

SQL 

Database design and table creation
Complex multi-table joins with optimization
Common Table Expressions (CTEs) for query performance
Data aggregation and transformation

Python

Pandas: Data manipulation and cleaning
Matplotlib & Seaborn: Statistical visualizations
SciPy: Hypothesis testing and statistical analysis
Logging Module: ETL pipeline monitoring

Power BI

DAX: Calculated measures and KPIs
Visualizations: Interactive charts and matrices
Features: Slicers, filters, drill-through capabilities
Design: Executive-ready dashboards with branding


🔄 Development Process

1. Data Engineering Phase
Challenge: Initial SQL join on millions of rows caused memory failures and 10+ minute execution times.
Solution Implemented:
sql-- Optimization Strategy: Pre-aggregation with CTEs
WITH purchase_summary AS (
    SELECT 
        vendor_id,
        product_id,
        SUM(quantity) as total_purchased,
        AVG(unit_price) as avg_purchase_price
    FROM purchases
    GROUP BY vendor_id, product_id
),
sales_summary AS (
    SELECT 
        product_id,
        SUM(quantity) as total_sold,
        AVG(unit_price) as avg_sales_price
    FROM sales
    GROUP BY product_id
)
-- Final join on aggregated data
Result: Reduced dataset from millions to 10,692 records, improving execution speed by 80%
2. Data Quality Management
Built systematic Python cleaning pipeline:
pythonimport pandas as pd
import logging

# Configure logging
logging.basicConfig(level=logging.INFO)

def clean_and_validate(df, table_name):
    """Standardized cleaning function"""
    logging.info(f"Cleaning {table_name}...")
    
    # Handle missing values
    # Standardize formats
    # Validate data types
    # Remove duplicates
    
    logging.info(f"{table_name} cleaned: {len(df)} records")
    return df
Issues Addressed:

Inconsistent date formats across sources
Missing vendor information
Duplicate transaction records
Unit price anomalies

3. Feature Engineering
Created calculated business metrics:

Profit Margin: (Sales Price - Purchase Price) / Sales Price * 100
Stock Turnover Ratio: Sales Quantity / Average Inventory
Vendor Dependency Index: Vendor Purchases / Total Purchases * 100
Inventory Holding Cost: Unsold Quantity * Unit Cost * Holding Rate

4. Exploratory Data Analysis
Conducted comprehensive analysis using Python:

Distribution analysis of purchase volumes
Correlation analysis between freight costs and order sizes
Time-series analysis of inventory trends
Vendor performance segmentation

5. Hypothesis Testing
Hypothesis: Low-performing vendors have higher profit margins
pythonfrom scipy import stats

high_performers = vendor_data[vendor_data['performance'] == 'high']['margin']
low_performers = vendor_data[vendor_data['performance'] == 'low']['margin']

t_stat, p_value = stats.ttest_ind(high_performers, low_performers)
Result: Statistically significant (p < 0.05) - confirmed low performers focus on premium products rather than volume
6. Dashboard Development
Built comprehensive Power BI dashboard with:

Executive KPI cards
Vendor performance matrix
Inventory aging analysis
Purchase vs. sales trends
Dynamic filtering by vendor, category, time period


💡 Key Insights & Findings

Supply Chain Risk

65.7% vendor concentration: Top 10 vendors account for majority of purchases
Single-source dependencies identified for 23 critical product categories
Supply chain vulnerability to vendor disruptions

Inventory Inefficiency

$2.71M locked capital in unsold inventory
Average inventory turnover: 4.2x (industry benchmark: 6-8x)
198 slow-moving SKUs identified with <2 sales per quarter

Cost Optimization Opportunities

72% cost reduction potential through bulk purchasing strategies
Freight optimization: Small orders incur 3x higher per-unit shipping costs
Volume discounts underutilized with 45% of vendors

Product Performance

198 high-margin brands with low sales velocity need marketing push
Premium products from low-volume vendors show 35% higher margins
Fast-moving items concentrated in 15% of product catalog

Statistical Validation

Hypothesis confirmed: Low-performing vendors have significantly higher margins (p = 0.003)
Indicates strategic focus on premium products vs. volume sales
Suggests need for differentiated vendor management strategies


📈 Business Impact & Recommendations

Immediate Actions (0-3 Months)
1. Inventory Optimization
Impact: Free up $1.3M in working capital (48% of unsold inventory)

Implement clearance strategy for 198 slow-moving brands
Reduce safety stock levels for low-turnover items
Establish inventory ceiling policies by category

2. Bulk Purchasing Program
Impact: 72% cost reduction on qualifying orders

Negotiate volume agreements with top 20 vendors
Consolidate orders to meet bulk thresholds
Implement quarterly purchase planning

3. Vendor Diversification
Impact: Reduce supply chain risk from 65.7% to <40% concentration

Identify 5-7 alternative vendors per category
Establish backup supplier agreements
Create vendor performance scorecards

Medium-Term Strategy (3-12 Months)
4. Marketing Campaign
Target: 198 high-margin/low-sales brands

Expected revenue increase: $400K annually
Focus on premium product positioning
Cross-sell with fast-moving items

5. Vendor Performance Management
Implementation: Real-time dashboard monitoring

Monthly vendor scorecards (delivery, quality, pricing)
Performance-based negotiation leverage
Automated alerts for underperformance

Long-Term Vision (12+ Months)
6. Predictive Analytics

Demand forecasting models
Automated reorder point optimization
Dynamic pricing recommendations


