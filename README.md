# Power BI Banking Analytics Dashboard

A Power BI analytics dashboard built using a **Star Schema** to analyze customer insights and banking transaction performance.

The project demonstrates data modeling, DAX measures, interactive filtering, time-based analysis, and business-focused dashboard design.

---

## 📊 Dashboard Overview

The Power BI report contains two main analytical pages:

### 1. Customer Insights

This page focuses on customer-level analysis and helps understand customer characteristics and interest-rate patterns.

**Key KPIs:**
- Total Customers
- Average Annual Income
- Accounts per Customer
- Average Interest Rate

**Visual analysis includes:**
- Average Interest Rate by Customer Segment
- Average Interest Rate by Occupation
- Average Interest Rate by Age Band
- Region and City filters
- Year selection from 2022 to 2026

### 2. Executive Overview

This page provides a high-level view of banking transaction performance.

**Key KPIs:**
- Average Transaction Amount
- Total Transaction Amount
- Total Transaction Count
- Success Rate

**Visual analysis includes:**
- Success Rate by Quarter
- Success Rate by Transaction Channel
- Success Rate by Region
- Year-wise analysis
- Region and City filters

---

## 🏗️ Data Model

The report follows a **Star Schema** architecture.

### Fact Table

**`fact_trans`**

Contains transactional/business-event data used for quantitative analysis.

Typical analytical fields include:
- Transaction amount
- Transaction count
- Transaction status
- Transaction date
- Customer/account references
- Branch references
- Transaction channel

### Dimension Tables

**`dim_customers`**
- Customer information
- Customer segment
- Occupation
- Age/age band
- Annual income
- Region/city attributes

**`dim_accounts`**
- Account-related attributes
- Account information connected to customers

**`dim_branch`**
- Branch information
- Region
- City and related branch attributes

**`dim_date`**
- Date
- Year
- Quarter
- Month
- Other calendar attributes used for time-based analysis

### Model Structure

```text
                 dim_customers
                       |
                       |
dim_date ------ fact_trans ------ dim_accounts
                       |
                       |
                  dim_branch
```

The fact table is used for measurable business events, while dimension tables provide descriptive context for slicing and analyzing those events.

---

## 📐 Key Measures

The dashboard uses DAX measures for KPI calculations and visual analysis.

Examples include:

```DAX
Total Transaction Amount =
SUM(fact_trans[trans_amt])
```

```DAX
Average Transaction Amount =
AVERAGE(fact_trans[trans_amt])
```

```DAX
Total Transaction Count =
COUNTROWS(fact_trans)
```

```DAX
Success Rate =
DIVIDE(
    CALCULATE(
        COUNTROWS(fact_trans),
        fact_trans[status] = "Success"
    ),
    COUNTROWS(fact_trans)
) * 100
```

Customer-focused measures include metrics such as:

```text
Total Customers
Average Annual Income
Accounts per Customer
Average Interest Rate
```

> Measure names and column names may differ depending on the final Power BI model.

---

## 🎛️ Interactive Features

The report provides interactive controls for business analysis.

### Filters

- Region
- City

### Year Selection

The dashboard allows users to switch between:

- 2022
- 2023
- 2024
- 2025
- 2026

This allows users to analyze customer and transaction performance across different years.

---

## 📈 Business Questions Answered

The dashboard can be used to explore questions such as:

### Customer Analysis

- How many customers are present?
- What is the average annual income of customers?
- How many accounts are held per customer?
- How does the average interest rate vary by customer segment?
- Does interest rate vary across occupations?
- How does interest rate compare across age bands?

### Transaction Analysis

- What is the total transaction amount?
- What is the average transaction amount?
- How many transactions occurred?
- What is the overall transaction success rate?
- How does success rate change by quarter?
- Which transaction channels have different success rates?
- How does transaction success rate vary by region?

---

## 🛠️ Tools & Technologies

- **Power BI Desktop**
- **DAX**
- **Power Query**
- **Data Modeling**
- **Star Schema**
- **SQL / Relational Data Concepts**

---

## 🔄 Data Modeling Approach

The project follows a dimensional modeling approach:

```text
Raw / Source Data
       ↓
Data Cleaning & Transformation
       ↓
Dimension Tables + Fact Table
       ↓
Star Schema
       ↓
DAX Measures
       ↓
Interactive Power BI Dashboard
       ↓
Business Insights
```

The star schema helps separate transactional data from descriptive attributes and makes the model easier to analyze and maintain.

---

## 📷 Dashboard Preview

### Customer Insights

![Customer Insights](images/customer-insights.png)

### Executive Overview

![Executive Overview](images/executive-overview.png)

> Place the two dashboard screenshots inside an `images` folder in the GitHub repository using the filenames shown above.

---

## 📁 Suggested Repository Structure

```text
powerbi-banking-dashboard/
│
├── README.md
│
├── PowerBI/
│   └── Banking_Analytics_Dashboard.pbix
│
├── images/
│   ├── customer-insights.png
│   └── executive-overview.png
│
├── data/
│   └── README.md
│
└── docs/
    └── data-model.png
```

If the source data is confidential or too large, do not upload it to GitHub. Instead, document the expected table structure and provide a small sample dataset where appropriate.

---

## 🎯 Project Objectives

The main objectives of this project are to:

1. Build a dimensional data model using a Star Schema.
2. Separate transactional and descriptive data using fact and dimension tables.
3. Create reusable DAX measures for business KPIs.
4. Build interactive Power BI dashboards.
5. Analyze customer behavior and banking transaction performance.
6. Provide business-friendly visual insights through KPIs, charts, filters, and time-based analysis.

---

## 🚀 How to Use

1. Clone or download this repository.
2. Open the `.pbix` file using **Power BI Desktop**.
3. If required, update the data source connections.
4. Refresh the dataset.
5. Navigate between the **Customer Insights** and **Executive Overview** pages.
6. Use the Region, City, and Year filters to explore the data.

---

## 💡 Key Power BI Concepts Demonstrated

- Star Schema
- Fact and Dimension Tables
- Relationships
- Data Modeling
- DAX Measures
- KPI Cards
- Time Intelligence
- Slicers
- Interactive Filtering
- Aggregations
- Customer Segmentation
- Transaction Analysis
- Dashboard Design

---

## 👨‍💻 Author

**Manoj B P**

Power BI | SQL | Python | Data Analytics | Data Engineering

---

## 📌 Disclaimer

This dashboard is created for learning, portfolio, and analytical demonstration purposes. The displayed values and business entities may represent sample or simulated data.
