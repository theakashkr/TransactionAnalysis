# PhonePe Pulse - Payment Insights & Analytics Dashboard 🚀

An end-to-end data analytics project featuring interactive **Power BI** dashboards and **SQL Queries** to analyze transaction patterns, customer demographics, usage behaviors, and service-wise performance for PhonePe.

---

## 📸 Dashboard Preview

![PhonePe Power BI Dashboard](Dashboard.jpg)

---

## 📌 Project Overview

This project provides actionable business insights into digital payment performance across various dimensions including user demographics, service categories, day-of-week trends, and month-over-month growth. Designed with modern UI/UX principles, the dashboard allows business stakeholders and recruiters to easily digest key performance indicators (KPIs) and data stories.

### Key Metrics Tracked:
* **Total Transactions:** 101K
* **Total Transaction Value:** ₹528.97M
* **Unique Users:** 108K
* **Success Rate:** 96.15%
* **MoM Growth:** Total Transactions (+8.21%) | Transaction Value (+8.93%)

---

## 🛠️ Key Learnings & Skills Demonstrated

- **Dashboard Layout & Design:** Applied visual hierarchy, clean card structures, and a consistent PhonePe purple color scheme.
- **KPI Card & Tooltip Design:** Created custom KPI cards and interactive tooltips to summarize key metrics efficiently.
- **Data Modeling & DAX:** Developed DAX measures for Month-over-Month (MoM%) growth tracking and time-intelligence analyses.
- **Service-Wise Transaction Analysis:** Evaluated transaction volume across *Loans, Money Transfer, Insurance, and Recharge & Bills*.
- **Customer & Age Segmentation:** Analyzed revenue and usage contributions across demographics (*Millennial, Gen X, Gen Z, Boomers*).
- **Weekday vs. Weekend Analysis:** Segmented digital transaction distribution to understand peak user activity days.
- **SQL Data Analysis:** Wrote robust SQL queries for data extraction, transformation, aggregation, and validation.
- **Business Storytelling:** Turned raw transactional data into recruiter-ready insights and executive summaries.

---

## 💡 Key Business Insights

1. **Age Segment Breakdown:**
   - **Millennials** contribute the highest volume and value (~37.77% / ₹199.78M), closely followed by **Gen X** (~36.73% / ₹194.28M).
   - **Gen Z** makes up ~21.07% of transactions, representing a major growth opportunity.

2. **Weekday vs. Weekend Usage:**
   - **71.49%** (₹378.16M) of total transaction value occurs on **Weekdays**, showing strong reliance on PhonePe for daily essential commerce and peer-to-peer transfers.
   - **28.51%** (₹150.82M) occurs on **Weekends**.

3. **Service Category Breakdown:**
   - **Loans** and **Money Transfer** dominate transaction value compared to Insurance and Recharge/Bills.

4. **MoM Growth Momentum:**
   - Consistent upward momentum in transaction counts (+8.21%) and total value (+8.93%) reflects strong month-over-month user retention and adoption.

---

## 📁 Repository Structure

```text
├── Dashboard.jpg           # High-resolution screenshot of the Power BI report
├── PhonePe_Dashboard.pbix  # Power BI Desktop report file
├── queries.sql             # SQL queries used for data extraction and analysis
└── README.md               # Documentation
```

---

## 🔍 Key SQL Queries

<details>
<summary>Click to view sample SQL queries</summary>

```sql
-- 1. Total Transactions and Revenue Summary
SELECT 
    COUNT(transaction_id) AS Total_Transactions,
    SUM(transaction_amount) AS Total_Value,
    COUNT(DISTINCT user_id) AS Unique_Users,
    ROUND((SUM(CASE WHEN status = 'Success' THEN 1 ELSE 0 END) * 100.0 / COUNT(*)), 2) AS Success_Rate
FROM phonepe_transactions;

-- 2. Age Segment Revenue Contribution
SELECT 
    age_group,
    SUM(transaction_amount) AS Total_Amount,
    ROUND((SUM(transaction_amount) * 100.0 / (SELECT SUM(transaction_amount) FROM phonepe_transactions)), 2) AS Value_Percentage
FROM phonepe_transactions
GROUP BY age_group
ORDER BY Total_Amount DESC;

-- 3. Weekday vs Weekend Usage
SELECT 
    CASE 
        WHEN DAYOFWEEK(transaction_date) IN (1, 7) THEN 'Weekend'
        ELSE 'Weekday'
    END AS Day_Type,
    COUNT(transaction_id) AS Transaction_Count,
    SUM(transaction_amount) AS Total_Value
FROM phonepe_transactions
GROUP BY Day_Type;
```

</details>

---

## 🛠️ Tools & Technologies Used

* **Power BI Desktop** (Data visualization, DAX, Custom Tooltips)
* **SQL** (Data Extraction, Aggregations, Window Functions)
* **Excel / CSV** (Data Cleaning & Preparation)

---

## 🤝 Let's Connect!

If you find this project insightful or have feedback, feel free to reach out or connect on LinkedIn!

* **GitHub:** [@your-username](https://github.com/your-username)
* **LinkedIn:** [Your Name](https://linkedin.com/in/your-profile)
* **Email:** your.email@example.com