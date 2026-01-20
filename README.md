<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Zepto E-commerce SQL Data Analyst Portfolio Project</title>
    <style>
        body {
            font-family: Arial, Helvetica, sans-serif;
            line-height: 1.6;
            margin: 40px;
            color: #333;
        }
        h1, h2, h3 {
            color: #1f2937;
        }
        code {
            background-color: #f3f4f6;
            padding: 2px 6px;
            border-radius: 4px;
        }
        pre {
            background-color: #f3f4f6;
            padding: 15px;
            border-radius: 6px;
            overflow-x: auto;
        }
        ul {
            margin-left: 20px;
        }
        hr {
            margin: 40px 0;
        }
    </style>
</head>
<body>

<h1>🛒 Zepto E-commerce SQL Data Analyst Portfolio Project</h1>

<p>
This is a complete, real-world <strong>SQL Data Analyst portfolio project</strong> based on an
e-commerce inventory dataset scraped from <strong>Zepto</strong>, one of India’s fastest-growing
quick-commerce startups.
</p>

<p>
The project simulates end-to-end data analyst workflows, from raw data setup to
business-focused insights using SQL.
</p>

<hr>

<h2>🎯 Who This Project Is For</h2>
<ul>
    <li>📊 Data Analyst aspirants building strong portfolio projects</li>
    <li>📚 Anyone learning SQL through hands-on, real-world datasets</li>
    <li>💼 Candidates preparing for interviews in retail, e-commerce, or product analytics</li>
</ul>

<hr>

<h2>📌 Project Objective</h2>
<p>
The goal of this project is to simulate how data analysts in e-commerce or retail companies
use SQL to:
</p>
<ul>
    <li>Set up and manage a messy, real-world inventory database</li>
    <li>Perform Exploratory Data Analysis (EDA)</li>
    <li>Clean and standardize inconsistent data</li>
    <li>Answer business-driven questions related to pricing, inventory, discounts, and revenue</li>
</ul>

<hr>

<h2>📁 Dataset Overview</h2>
<p>
The dataset was sourced from Kaggle and originally scraped from Zepto’s official product listings.
It closely resembles real-world e-commerce catalog data.
</p>

<p>
Each row represents a unique <strong>SKU (Stock Keeping Unit)</strong>.
Duplicate product names exist because the same product may appear in different package sizes,
weights, discounts, or categories.
</p>

<hr>

<h2>🧾 Dataset Columns</h2>
<ul>
    <li><strong>sku_id</strong> – Unique identifier for each product entry (synthetic primary key)</li>
    <li><strong>name</strong> – Product name as shown in the app</li>
    <li><strong>category</strong> – Product category (Fruits, Snacks, Beverages, etc.)</li>
    <li><strong>mrp</strong> – Maximum Retail Price (converted from paise to ₹)</li>
    <li><strong>discountPercent</strong> – Discount applied on MRP</li>
    <li><strong>discountedSellingPrice</strong> – Final selling price after discount (₹)</li>
    <li><strong>availableQuantity</strong> – Units available in inventory</li>
    <li><strong>weightInGms</strong> – Product weight in grams</li>
    <li><strong>outOfStock</strong> – Boolean flag indicating stock availability</li>
    <li><strong>quantity</strong> – Number of units per package (mixed with grams for loose produce)</li>
</ul>

<hr>

<h2>🔧 Project Workflow</h2>

<h3>1️⃣ Database &amp; Table Creation</h3>
<pre>
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
</pre>

<h3>2️⃣ Data Import</h3>
<pre>
\copy zepto(
    category, name, mrp, discountPercent, availableQuantity,
    discountedSellingPrice, weightInGms, outOfStock, quantity
)
FROM 'data/zepto_v2.csv'
WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');
</pre>

<p>
<strong>Note:</strong> UTF-8 encoding issues were resolved by saving the CSV file
in <em>CSV UTF-8</em> format.
</p>

<h3>3️⃣ 🔍 Exploratory Data Analysis (EDA)</h3>
<ul>
    <li>Counted total records in the dataset</li>
    <li>Viewed sample records to understand structure</li>
    <li>Checked for null values across all columns</li>
    <li>Identified distinct product categories</li>
    <li>Compared in-stock vs out-of-stock products</li>
    <li>Detected duplicate product names representing multiple SKUs</li>
</ul>

<h3>4️⃣ 🧹 Data Cleaning</h3>
<ul>
    <li>Removed records where MRP or discounted price was zero</li>
    <li>Converted pricing values from paise to rupees</li>
</ul>

<h3>5️⃣ 📊 Business Insights Using SQL</h3>
<ul>
    <li>Top 10 best-value products based on discount percentage</li>
    <li>High-MRP products that are currently out of stock</li>
    <li>Estimated potential revenue by product category</li>
    <li>Expensive products (MRP &gt; ₹500) with minimal discounts</li>
    <li>Top 5 categories with the highest average discounts</li>
    <li>Price-per-gram analysis for value-for-money products</li>
    <li>Weight-based product segmentation (Low, Medium, Bulk)</li>
    <li>Total inventory weight per category</li>
</ul>

<hr>

<h2>🛠️ How to Use This Project</h2>
<ol>
    <li>Clone the repository</li>
    <li>Open <code>zepto_SQL_data_analysis.sql</code></li>
    <li>Create a PostgreSQL database</li>
    <li>Run the SQL file</li>
    <li>Import the dataset (ensure UTF-8 encoding)</li>
</ol>

<hr>

<h2>📜 License</h2>
<p>
This project is licensed under the <strong>MIT License</strong>.
You are free to use, modify, and include it in your portfolio.
</p>

</body>
</html>
