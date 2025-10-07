# 📘 Project: Customer Churn Analysis (Excel Dashboard)

## 🎯 Objective
To analyze telecom customer data and identify key drivers behind customer churn.  
The goal is to help the business reduce churn and improve retention strategies through data-driven insights.

---

## 🧮 Dataset Overview

| Feature | Description |
|----------|--------------|
| `customerID` | Unique ID per customer |
| `gender`, `SeniorCitizen`, `Partner`, `Dependents` | Demographic details |
| `tenure`, `Contract`, `PaymentMethod`, `PaperlessBilling` | Service & contract details |
| `InternetService`, `TechSupport`, `OnlineSecurity` | Service type & usage |
| `MonthlyCharges`, `TotalCharges` | Revenue-related metrics |
| `Churn` | Whether customer left (Yes/No) |
| `Average Monthly Revenue`, `Customer Lifetime Value (CLV)` | *New calculated fields* added for advanced analysis |

---

## 🧹 Data Cleaning & Preparation

1. Removed **11 records** with tenure = 0 (customers not yet activated).  
2. Standardized Yes/No values into descriptive terms (e.g., “Have Partner”, “No Partner”).  
3. Added calculated columns:  
   - `Average Monthly Revenue = TotalCharges / tenure`  
   - `Customer Lifetime Value (CLV) = MonthlyCharges * tenure`  
   - `Subscription Time` = tenure converted into categories (<1 year, 1–3 years, >3 years).  
4. Ensured all numeric fields (TotalCharges, MonthlyCharges) were clean and consistent.  

---

## 📊 Key Performance Indicators (KPIs)

| KPI | Excel Formula | Description |
|------|---------------|-------------|
| **Total Customers** | `=COUNTA(tblCustomers[customerID])` | Total active + churned customers |
| **Churned Customers** | `=COUNTIF(tblCustomers[Churn],"Yes")` | Number of customers who left |
| **Active Customers** | `=COUNTIF(tblCustomers[Churn],"No")` | Current active customers |
| **Churn Rate** | `=COUNTIF(tblCustomers[Churn],"Yes") / COUNTA(tblCustomers[customerID])` | % of customers who churned |
| **Monthly Recurring Revenue (MRR)** | `=SUMIFS(tblCustomers[MonthlyCharges], tblCustomers[Churn], "No")` | Monthly revenue from active customers |
| **Annual Recurring Revenue (ARR)** | `=SUMIFS(tblCustomers[MonthlyCharges], tblCustomers[Churn], "No") * 12` | Annual projection of recurring revenue |
| **Average Monthly Revenue (ARPU)** | `=AVERAGE(tblCustomers[MonthlyCharges])` | Mean monthly spend per user |
| **Customer Lifetime Value (CLV)** | `=tblCustomers[MonthlyCharges] * tblCustomers[tenure]` | Lifetime worth of a customer |
| **Average Tenure (Months)** | `=AVERAGE(tblCustomers[tenure])` | Average duration of customer relationship |
| **Revenue Lost to Churn** | `=SUMIFS(tblCustomers[MonthlyCharges], tblCustomers[Churn], "Yes")` | Monthly revenue lost from churned customers |


## 📈 Dashboard Highlights 
- **Charts:**
  - Churn % by Contract Type  
  - Churn % by Internet Service  
  - Tenure vs Churn (line chart)  
  - Revenue vs Churn (bar chart)  
- **KPIs:** Dynamic cards for Churn Rate, ARR, Total Customers, Active Customers  

---

## 🧠 Key Insights

1. **Month-to-Month contracts** have the **highest churn rate (~43%)**, while two-year contracts show strong retention.  
2. Customers **without Tech Support or Online Security** are more likely to churn.  
3. **Electronic check** payment method users show higher churn — likely due to higher manual effort.  
4. **Senior Citizens** show slightly higher churn than younger customers.  
5. **ARR ≈ $2.8M** from active users; losing 5% more customers could reduce ARR by approximately **$140K annually**.

## 💡 Recommendations

- Offer discounts or loyalty programs for *month-to-month* users to switch to long-term contracts.  
- Promote **Tech Support & Security bundles** to increase retention.  
- Simplify or incentivize **auto-pay** options to reduce churn via payment method friction.  
- Create targeted retention campaigns for high-value customers (based on CLV).  

---

## 🧰 Tools Used

- **Microsoft Excel** – Data cleaning, Pivot Tables, and Dashboard visualization 
  
