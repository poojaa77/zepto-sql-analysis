# 🛒 Zepto E-Commerce Inventory Analysis

A comprehensive SQL data analysis project using real-world inventory data from Zepto, one of India's fastest-growing quick-commerce platforms. This project demonstrates end-to-end data analytics workflow from database setup to deriving actionable business insights.

## 📋 Table of Contents
- [Project Overview](#project-overview)
- [Dataset Information](#dataset-information)
- [Technologies Used](#technologies-used)
- [Database Schema](#database-schema)
- [Key Features](#key-features)
- [Analysis Performed](#analysis-performed)
- [Business Insights](#business-insights)
- [SQL Queries](#sql-queries)
- [Installation & Setup](#installation--setup)
- [Usage](#usage)
- [Key Learnings](#key-learnings)
- [Future Enhancements](#future-enhancements)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Project Overview

This project simulates real-world data analyst workflows in the e-commerce and retail industry. Using a dataset scraped from Zepto's product listings, I performed comprehensive data analysis to uncover insights about pricing strategies, inventory management, product availability, and revenue optimization.

**Project Goals:**
- Set up and structure a real-world e-commerce inventory database
- Perform thorough Exploratory Data Analysis (EDA)
- Clean and transform messy data for accurate analysis
- Write business-driven SQL queries to extract actionable insights
- Support data-driven decision-making for inventory and pricing optimization

## 📊 Dataset Information

**Source:** Kaggle - Zepto Inventory Dataset  
**Dataset Type:** E-commerce Product Inventory  
**Format:** CSV

The dataset contains product information including:
- SKU (Stock Keeping Unit) identifiers
- Product categories and names
- Pricing information (MRP and discounted prices)
- Discount percentages
- Available quantities and stock status
- Product weight specifications

Each row represents a unique SKU, with products potentially appearing multiple times due to variations in weight, packaging, or discount schemes.

## 🛠 Technologies Used

- **Database:** PostgreSQL
- **Tools:** pgAdmin 4
- **Language:** SQL
- **Data Format:** CSV

## 🗄️ Database Schema

```sql
CREATE TABLE zepto (
    sku_id SERIAL PRIMARY KEY,
    category VARCHAR(120),
    name VARCHAR(150) NOT NULL,
    mrp NUMERIC(8,2),
    discountPercent NUMERIC(5,2),
    availableQuantity INTEGER,
    discountedSellingPrice NUMERIC(8,2),
    weightInGms INTEGER,
    outOfStock BOOLEAN,
    quantity INTEGER
);
```

## ✨ Key Features

- **Data Import & Setup:** Loaded CSV data into PostgreSQL database
- **Data Cleaning:** Handled null values, removed invalid entries, converted pricing units
- **Exploratory Analysis:** Investigated product distribution, pricing patterns, and stock availability
- **Business Analytics:** Derived insights on revenue, discounts, inventory optimization
- **Query Optimization:** Wrote efficient SQL queries for large-scale data analysis

## 🔍 Analysis Performed

### 1. Data Exploration
- Total record count and data structure analysis
- Sample data inspection
- Category-wise product distribution
- Pricing range analysis

### 2. Data Cleaning
- Identified and removed records with zero MRP or selling price
- Converted pricing from paise to rupees for consistency
- Handled missing values and data inconsistencies
- Validated stock availability flags

### 3. Business Analysis
- **Discount Analysis:** Identified top 10 best-value products by discount percentage
- **Inventory Management:** Found high-MRP items currently out of stock
- **Revenue Estimation:** Calculated potential revenue by product category
- **Pricing Strategy:** Filtered expensive products (MRP > ₹500) with minimal discounts
- **Category Performance:** Analyzed average discounts and pricing by category
- **Stock Optimization:** Identified low-stock high-demand products

## 💡 Business Insights

Key findings from the analysis:

1. **Pricing Patterns:** Identified categories with highest and lowest discount rates
2. **Stock Issues:** Discovered premium products frequently going out of stock
3. **Revenue Opportunities:** Estimated potential revenue loss from stockouts
4. **Discount Strategy:** Found products with suboptimal discount-to-MRP ratios
5. **Category Performance:** Ranked categories by revenue potential and turnover

## 📝 SQL Queries

The project includes comprehensive SQL queries covering:

- **Aggregation Functions:** COUNT, SUM, AVG, MIN, MAX
- **Filtering:** WHERE, HAVING clauses for business rules
- **Sorting:** ORDER BY for ranking and prioritization
- **Data Transformation:** CASE statements, type conversions
- **Grouping:** GROUP BY for category-wise analysis
- **Joins:** (If applicable) Combining related data
- **Subqueries:** Nested queries for complex analysis

All queries are documented in `zepto_analysis.sql` with comments explaining the business logic.

## 🚀 Installation & Setup

### Prerequisites
- PostgreSQL installed on your system
- pgAdmin 4 (or any PostgreSQL client)
- Basic knowledge of SQL

### Steps

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/zepto-sql-analysis.git
cd zepto-sql-analysis
```

2. **Create Database**
```sql
CREATE DATABASE zepto_db;
```

3. **Create Table**
Run the schema creation script from `zepto_analysis.sql`

4. **Import Data**
- Open pgAdmin
- Right-click on the `zepto` table → Import/Export
- Select your CSV file
- Configure import settings (delimiter: comma, header: yes)
- Execute import

5. **Run Analysis Queries**
Execute the queries in `zepto_analysis.sql` sequentially

## 💻 Usage

```sql
-- Example: Find top 10 most discounted products
SELECT 
    name,
    category,
    mrp,
    discountPercent,
    discountedSellingPrice
FROM zepto
WHERE discountPercent IS NOT NULL
ORDER BY discountPercent DESC
LIMIT 10;

-- Example: Calculate revenue by category
SELECT 
    category,
    SUM(discountedSellingPrice * availableQuantity) AS potential_revenue,
    COUNT(*) AS product_count
FROM zepto
WHERE outOfStock = FALSE
GROUP BY category
ORDER BY potential_revenue DESC;
```

## 📚 Key Learnings

- Real-world data is messy and requires extensive cleaning
- Business context is crucial for meaningful data analysis
- Proper database design impacts query performance
- SQL is powerful for deriving actionable business insights
- Data validation is essential before analysis

## 🔮 Future Enhancements

- [ ] Add time-series analysis for stock trends
- [ ] Implement customer segmentation analysis
- [ ] Create automated data pipeline for daily updates
- [ ] Build Power BI/Tableau dashboards for visualization
- [ ] Add predictive analytics for demand forecasting
- [ ] Integrate Python for advanced statistical analysis

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📧 Contact

Name - poojagajjar777@gmail.com 
Project Link: [https://github.com/poojaa77/zepto-sql-analysis]

## 🙏 Acknowledgments

- Dataset sourced from Kaggle
- Inspired by real-world e-commerce analytics workflows
- Thanks to the Zepto team for making data publicly available

---

⭐ If you found this project helpful, please consider giving it a star!

**#DataAnalytics #SQL #PostgreSQL #ECommerce #DataScience #BusinessIntelligence**
