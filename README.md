# Intelligent Supply Chain Optimisation & Volatility Tracking for UK Supermarkets

## Project Overview

This project was designed to build an end-to-end supply chain analytics solution using Python, MySQL, and Power BI. The objective was to automate data cleaning, detect inventory anomalies, analyse supplier performance, identify operational risks, and create an interactive dashboard for business decision-making.

---

# Technology Stack

* Python (pandas, SQLAlchemy)
* MySQL
* Power BI
* DAX
* Power Query

---

# Phase 1 – Python Data Engineering & ETL

## 1. Data Ingestion

The raw supermarket supply chain CSV dataset was imported into Python using pandas.

Key activities:

* Loaded CSV file into pandas dataframe
* Standardised date formats
* Converted stock and sales fields into numeric datatypes
* Performed initial data validation

### Example Columns

* Date
* Region
* Store_ID
* Category
* Opening_Stock
* Deliveries
* Daily_Sales
* Closing_Stock
* Supplier_Status
* Lead_Time_Days

---

## 2. Intelligent Anomaly Detection

A rule-based anomaly detection system was implemented to identify mathematically impossible inventory scenarios.

### Validation Rule

Rows were flagged if:

Daily_Sales > Opening_Stock + Deliveries

These records were isolated into a separate quarantined dataset to maintain data quality.

### Outcome

* Invalid inventory records removed
* Clean operational dataset created
* Improved analytical reliability

---

## 3. Stock Status Recalculation

The original Stock_Status column was considered unreliable.

A new rule-based logic engine recalculated inventory status:

| Condition           | Status   |
| ------------------- | -------- |
| Closing_Stock < 50  | Critical |
| Closing_Stock < 150 | Warning  |
| Else                | Healthy  |

### Outcome

* Removed incorrect manual/system labels
* Standardised inventory classification
* Improved operational monitoring

---

## 4. Supplier Reliability Scoring

A custom Python function was developed to calculate supplier performance.

### Logic Used

* Base Score = 100
* On-Time = +10
* Delayed = -30
* Cancelled = -60
* Lead time penalty = -2 points per day

### Output

A new calculated field:

Supplier_Reliability_Score

### Business Value

* Identified unreliable suppliers
* Supported procurement analysis
* Improved operational risk visibility

---

## 5. Demand Volatility Profiling

Coefficient of Variation (CV) analysis was used to measure category-level demand instability.

### Formula

CV = (Standard Deviation / Mean) × 100

### Output

Category_Volatility_Index

### Business Value

* Identified unstable product categories
* Improved inventory planning insights
* Highlighted demand fluctuation trends

---

## 6. Data Export

The cleaned and enriched dataset was exported as:

* cleaned_supply_chain_data.csv
* quarantined_data.csv

---

# Phase 2 – MySQL Database & Advanced SQL Analytics

## 1. Database Loading

The final cleaned dataset was loaded into MySQL using SQLAlchemy.

### Database

supply_chain_db

### Table

uk_supermarket_supply

---

## 2. Advanced SQL Business Queries

### Query 1 – Chronic Under-Delivery Detector

Identified store and category combinations where deliveries covered less than 50% of sales and supplier failures exceeded 20%.

### Business Insight

Detected operationally vulnerable inventory locations.

---

### Query 2 – Perfect Storm Vulnerability Finder

Detected stores experiencing high sales on the same day suppliers cancelled deliveries.

### Business Insight

Identified high-risk stockout scenarios.

---

### Query 3 – Supplier Impact Stress Test

Compared average closing stock levels between on-time and delayed supplier deliveries.

### Business Insight

Measured operational dependency on supplier punctuality.

---

### Query 4 – False Alarm Audit

Checked whether stores incorrectly reported critical stock despite having healthy inventory levels.

### Business Insight

Validated inventory classification accuracy.

---

# Phase 3 – Power BI Dashboard & Business Intelligence

## 1. Star Schema Data Model

A proper star schema model was created.

### Fact Table

Fact_Inventory

### Dimension Tables

* Dim_Date
* Dim_Store

### Relationships

* One-to-Many relationships established
* Single-direction filtering implemented

---

## 2. KPI Dashboard

Executive KPI cards were created for:

* Total Sales
* Total Deliveries
* Average Closing Stock
* Supplier Reliability
* Critical Stock Count
* Supplier Failure Rate

---

## 3. Interactive Visualisations

Dashboard visuals included:

* Stock trend line chart
* Supplier reliability analysis
* Regional store distribution
* Category sales contribution
* Matrix heatmap
* Dynamic smart narrative

---

## 4. Smart Narrative System

A dynamic DAX-based narrative measure was developed to automatically generate business insights.

### Example Output

“Currently, all regions have an average closing stock of 185 units with a supplier failure rate of 30.3%.”

---

## 5. What-If Parameter Simulation

A lead-time reduction simulation model was created.

### Functionality

Users can simulate supplier lead-time improvements and estimate potential reductions in lost sales.

### Business Value

* Scenario analysis
* Operational forecasting
* Decision support analytics

---

# Key Skills Demonstrated

## Data Engineering

* ETL pipeline development
* Data cleaning
* Feature engineering
* Data validation

## SQL Analytics

* Conditional aggregation
* Correlated subqueries
* HAVING clause analysis
* Business intelligence querying

## Power BI

* Star schema modeling
* DAX measures
* Power Query transformations
* Interactive dashboard design
* KPI reporting
* Scenario simulation

## Business Intelligence

* Supply chain risk analysis
* Inventory optimisation
* Supplier performance tracking
* Demand volatility analysis
* Executive reporting

---

# Project Outcome

This project successfully delivered a complete end-to-end supply chain analytics platform capable of:

* Detecting inventory anomalies
* Monitoring supplier reliability
* Tracking demand volatility
* Supporting operational decision-making
* Delivering interactive executive dashboards
* Simulating supply chain optimisation scenarios

The solution demonstrates practical capabilities in data engineering, SQL analytics, and business intelligence development suitable for modern Data Analyst, BI Analyst, and Supply Chain Analyst roles.

---

# Tools Used

| Tool        | Purpose                   |
| ----------- | ------------------------- |
| Python      | ETL & feature engineering |
| pandas      | Data transformation       |
| SQLAlchemy  | Database connection       |
| MySQL       | Data storage & analytics  |
| Power BI    | Dashboard development     |
| DAX         | KPI calculations          |
| Power Query | Data modeling             |

---

# Final Deliverables

* Python ETL pipeline
* Cleaned analytical dataset
* Quarantined anomaly dataset
* MySQL analytical database
* Advanced SQL business queries
* Interactive Power BI dashboard
* Smart narrative reporting
* What-if simulation analysis
