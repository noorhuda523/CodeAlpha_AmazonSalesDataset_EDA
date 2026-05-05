# 🛒 Revenue Leakage & Cancellation Risk Analysis · Amazon E-Commerce Sales EDA

> **Funnel Analysis · Revenue Segmentation · Cancellation Risk Scoring · Discount Impact Assessment**
>
> `Python` `Pandas` `Matplotlib` `Seaborn` `Statistical Analysis` `EDA` `Hypothesis Testing` `IQR Outlier Detection`

---

## 📋 Executive Summary

| | |
|---|---|
| **Business Problem** | Thousands of Amazon transactions flow through multiple countries, product categories, and payment channels — but without structured analysis, revenue leaks, cancellation risks, and ineffective discount strategies stay invisible. |
| **Solution** | End-to-end EDA across 13 structured sections: data quality audit → revenue distribution → category segmentation → geographic analysis → fulfilment risk → discount effectiveness → correlation analysis → hypothesis testing → anomaly detection. |
| **Key Impact** | Identified that Cash on Delivery carries the highest cancellation risk, discounts show near-zero correlation with order value uplift, and revenue is heavily concentrated in the top product categories and countries. |
| **Next Steps** | Build a cancellation probability model by payment method and country; A/B test category-specific discount tiers; develop a customer lifetime value segmentation. |

---

## 📌 Business Problem

E-commerce businesses generate enormous transaction data but often lack visibility into **what drives — or erodes — revenue**.

This project answers five core business questions directly relevant to operations and strategy:

- Which product **categories generate the most revenue** — and which underperform despite high order volume?
- Do **discounts actually lift order value**, or do they simply cut margin without increasing basket size?
- Which **countries and regions** drive the most order activity — and is there geographic concentration risk?
- What does the **order status breakdown** reveal about fulfilment quality and cancellation exposure?
- Which **payment methods carry the highest cancellation rates** — and what is the operational cost?

---

## 🗂️ Project Structure

```
📦 amazon-sales-eda
 ┣ 📓 eda-on-amazon-sales-dataset.ipynb   ← Main analysis notebook (13 sections)
 ┣ 📄 README.md                           ← This file
 ┣ 📁 images/                             ← Chart exports from notebook
 ┗ 📊 dataset/Amazon.csv                  ← Source: Kaggle (rohiteng/amazon-sales-dataset)
```

---

## 🔍 Methodology

| Step | What Was Done |
|---|---|
| **1. Data Quality Audit** | Checked missing values, duplicates, negative quantities, data type corrections |
| **2. Feature Engineering** | Parsed OrderDate → extracted Year, Month, MonthName for time-series analysis |
| **3. Univariate Analysis** | Distribution of order values, quantities, and unit prices |
| **4. Bivariate Analysis** | Category vs revenue, discount vs order value, payment method vs cancellation rate |
| **5. Geographic Segmentation** | Orders and revenue broken down by country (top 10) |
| **6. Correlation Analysis** | Full Pearson correlation matrix across all numeric financial variables |
| **7. Hypothesis Testing** | 5 business hypotheses stated, tested, and interpreted against data |
| **8. Anomaly Detection** | Zero-tax high-value orders identified; IQR-based price outlier detection |

> No machine learning was applied. All business questions were answerable through statistical analysis and visualisation — keeping the analysis transparent, interpretable, and focused on real decisions.

---

## 🛠️ Skills & Technical Stack

| Category | Details |
|---|---|
| **Language** | Python 3 |
| **Core Libraries** | Pandas, NumPy, Matplotlib, Seaborn |
| **Analysis Techniques** | EDA, Revenue Segmentation, Group Aggregation, Distribution Analysis |
| **Statistical Methods** | Pearson Correlation, Descriptive Statistics, IQR Outlier Detection, Hypothesis Testing |
| **Data Cleaning** | Type casting, datetime parsing, null/duplicate detection, feature engineering |
| **Visualisation** | Histograms with KDE, Horizontal Bar Charts, Regression Scatter Plots, Heatmaps, Pie Charts |
| **Environment** | Kaggle Notebooks |

---

## 📊 Analysis & Visuals

### 1. Revenue Distribution & Annual Trend

Understanding how revenue is distributed across orders and how it has changed year over year.

![Revenue Distribution](files.zip/revenue_dist.png)

> A right-skewed distribution confirms that a small number of high-value orders drive a disproportionate share of total revenue — a common e-commerce pattern with significant implications for customer retention strategy.

---

### 2. Category Performance — Orders vs Revenue

Comparing which categories attract the most orders versus which generate the most revenue.

![Category Analysis](files.zip/category.png)

> A category leading in order count does not necessarily lead in revenue. High-price categories can dominate revenue with fewer transactions — margin strategy matters more than volume strategy.

---

### 3. Geographic Analysis — Top 10 Countries

Which countries drive the most orders and revenue — and whether concentration risk exists.

![Geographic Analysis](files.zip/geography.png)

> Heavy concentration in a few countries creates revenue risk. If the top 2–3 markets slow down, there is limited buffer from other regions.

---

### 4. Order Status & Fulfilment Quality

Breaking down Delivered vs Cancelled vs Returned orders and their revenue impact.

![Order Status](files.zip/order_status.png)

> Every cancelled or returned order is a direct operational cost — lost revenue plus logistics overhead. The combined loss rate is a key KPI for fulfilment health.

---

### 5. Payment Method — Usage & Cancellation Risk

Which payment methods are most popular, and which carry the highest cancellation rates.

![Payment Method](files.zip/payment.png)

> Cash on Delivery allows customers to reject orders at the door with no upfront cost — making it structurally riskier than prepaid methods.

---

### 6. Discount Impact Analysis

Testing whether discounts actually increase order value and quantity ordered.

![Discount Impact](files.zip/discount.png)

![Discount by Category](files.zip/discount_cat.png)

> Near-zero correlation between discount level and total order value means blanket discounts are margin transfers — not growth drivers.

---

### 7. Correlation Heatmap

Identifying which numeric variables move together across the dataset.

![Correlation Heatmap](files.zip/correlation.png)

> UnitPrice is the strongest driver of TotalAmount. Pricing strategy has more leverage than discount depth or quantity incentives.

---

## 📈 Key Results & Recommendations

| # | Finding | Business Implication |
|---|---|---|
| 1 | Revenue is right-skewed | A small % of high-value orders drive most revenue |
| 2 | Electronics leads revenue; order volume leader differs | High-price categories beat high-volume on revenue |
| 3 | Geographic concentration in top countries | Over-reliance on few markets = concentration risk |
| 4 | Cancellation + return rate is measurable | Every % point of loss rate = calculable operational cost |
| 5 | Cash on Delivery = highest cancellation rate | COD is a structural risk to fulfilment efficiency |
| 6 | Discount correlation with order value ≈ 0 | Blanket discounts transfer margin without lifting basket size |
| 7 | UnitPrice is the dominant TotalAmount driver | Pricing strategy > discount strategy for revenue impact |

**1. Restructure discount strategy** — Switch from blanket promotions to targeted, category-specific discounts. Current discounts are margin giveaways with near-zero uplift on order value.

**2. Reduce Cash on Delivery exposure** — Introduce prepayment incentives or limit COD in high-cancellation markets. Even a small shift to prepaid reduces fulfilment loss.

**3. Protect high-value orders** — The right tail of the revenue distribution is disproportionately important. Identify what drives these orders and replicate the conditions.

**4. Address geographic concentration** — Targeted expansion into underpenetrated markets reduces single-region revenue risk.

---

## ⚠️ Next Steps & Limitations

**Given more time, I would:**
- Build a cancellation probability model segmented by payment method, category, and country
- Create an RFM segmentation (Recency, Frequency, Monetary) for customer lifetime value analysis
- Run a simulated A/B test on discount tiers to estimate true revenue impact
- Build an interactive Power BI dashboard for business stakeholders

**Limitations of this dataset:**
- No customer demographics — age, income, or loyalty segmentation is not possible
- No marketing data — cannot isolate the ROI of discount campaigns
- Correlation does not imply causation — all relationships are observational
- No cost of goods data — full margin analysis is not possible

---

## 📁 Dataset

**Source:** [Amazon Sales Dataset — Kaggle](https://www.kaggle.com/datasets/rohiteng/amazon-sales-dataset)  
**Credit:** rohiteng | **Usage:** Educational and portfolio purposes only

---

## 👤 Author

**Noor ul Huda** — Data Analyst

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/noor-ul-huda-92b040358)
[![GitHub](https://img.shields.io/badge/GitHub-noorhuda523-black?style=flat&logo=github)](https://github.com/noorhuda523)
[![Kaggle](https://img.shields.io/badge/Kaggle-View_Notebook-20BEFF?style=flat&logo=kaggle)](https://www.kaggle.com/noorulhud)

---

> 💡 **Found this useful?** Star the repo and connect on LinkedIn.


