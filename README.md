# 📊 Telecom Customer Churn Analysis & Prediction

This project demonstrates a complete **ETL + Dashboard + Machine Learning** workflow using:
- **MySQL** for data extraction, cleaning, and preprocessing
- **Power BI** for interactive dashboards
- **Python (scikit-learn)** for predictive modeling using Random Forest

---

## 📁 Dataset Overview - Customer_Data.csv

- **Source**: Kaggle  
- **Rows**: 6,419  
- **Columns**: 32  
- **Target Variable**: `Customer_Status`  
  - Values: `Stayed`, `Churned`, `Joined`

---

## 🎯 Project Goals

1. **Analyze customer data** at multiple levels:
   - 🧑 **Demographics** (age, gender, marital status)
   - 🌍 **Geographics** (state, region)
   - 💳 **Payment & Account Info** (monthly charge, refund, revenue)
   - 📶 **Services** (phone, internet, streaming, device protection)

2. **Profile churned customers** to identify patterns and opportunities for **targeted marketing campaigns**.

3. **Build predictive models** to identify potential churners ahead of time and prevent customer loss.

---

## 📈 Metrics Tracked

- 👥 **Total Customers**
- 📉 **Total Churned Customers**
- 📊 **Churn Rate (%)**
- 🆕 **New Joiners**

---

## 🛠 Tools & Technologies Used

| Tool            | Purpose |
|-----------------|---------|
| **MySQL**       | Data exploration, null handling, ETL, and view creation |
| **Power BI**    | Dashboards for business summary and prediction |
| **Python (Jupyter)** | Machine Learning model training & prediction |
| **scikit-learn**| Random Forest classification model |
| **Power Query** | Data transformations in Power BI |
| **DAX**         | KPIs and custom measures |

---

## ⚙️ Workflow Overview

### 1. Data Exploration & Cleaning (MySQL)
- Checked distinct values and nulls
- Replaced nulls using `ISNULL()`
- Inserted cleaned data into `prod_Churn` table

### 2. View Creation for Power BI
```sql
CREATE VIEW vw_ChurnData AS
SELECT * FROM prod_Churn WHERE Customer_Status IN ('Churned', 'Stayed');

CREATE VIEW vw_JoinData AS
SELECT * FROM prod_Churn WHERE Customer_Status = 'Joined';
```

### 3. Power BI Churn Summary Dashboard
- Total customers, churned customers, churn rate, and new joiners
- Churn by gender, age group, payment method, tenure, contract type, and state
- Churn by services used

### 4. Machine Learning Model (Python - Random Forest)
- Preprocessed 20+ categorical features using LabelEncoder
- Dropped unused columns like `Customer_ID`, `Churn_Reason`
- Random Forest achieved **~86% accuracy**
- Saved predictions and merged with customer data

### 5. Power BI Prediction Dashboard
- Visualized predicted churners by state, gender, age, contract, etc.
- Showed list of at-risk customers with revenue insights

---

## 📊 Model Performance

| Metric      | Value  |
|-------------|--------|
| **Accuracy**| 86.0%  |
| **Model**   | Random Forest Classifier |

---

## 🔍 Top Predictive Features

- Monthly_Charge
- Contract
- Tenure_in_Months
- Internet_Type
- Payment_Method

---

## 🧾 SQL Output Snapshots

### Gender Distribution
- Female: 63.07%
- Male: 36.92%

### Contract Type
- Month-to-Month: 51.2% (most churn-prone)
- Two Year: 26.7% (most stable)

### Revenue by Customer Status
| Status   | Customers | Revenue % |
|----------|-----------|-----------|
| Stayed   | 4275      | 82.2%     |
| Churned  | 1732      | 17.5%     |
| Joined   | 411       | 0.25%     |

### Customer Distribution by State (Top 5)
| State          | Customers | Percentage |
|----------------|-----------|------------|
| Uttar Pradesh  | 629       | 9.81%      |
| Tamil Nadu     | 600       | 9.36%      |
| Maharashtra    | 504       | 7.85%      |
| Karnataka      | 473       | 7.37%      |
| Haryana        | 398       | 6.20%      |


---

## 📂 Project Structure

```
├── sql/
│   └── SQL Queries.docx
├── notebooks/
│   └── churn_modeling.ipynb
├── powerbi/
│   └── churn_analysis.pbix
├── docs/
│   └── Power Query Transformations.docx
├── screenshots/
│   ├── churn_summary_dashboard.png
│   └── churn_prediction_dashboard.png
├── data/
│   ├── Predictions.csv
|   └── Prediction_Data.xlmx
└──  README.md
```

---

## ✅ How to Run

1. Execute SQL scripts in `/sql` to load & clean data and create views.
2. Open Power BI `churn_analysis.pbix` files and link them to your SQL views.
3. Run `churn_modeling.ipynb` to train model and save predictions.
4. Reload predictions into Power BI for visualization.

---

## 🚀 Future Enhancements

- Deploy model using Flask or Streamlit
- Automate Power BI refresh using Power BI Gateway
- Add SHAP plots for model explainability
- Set up churn alerts via email

---

**Last Updated**: August 07, 2025
