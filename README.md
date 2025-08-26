# 🏠 London House Price Regression Project

## 📌 Project Overview
This project focuses on predicting **London house prices** using regression models. Housing prices in London are both a key economic indicator and a subject of public interest. By building accurate predictive models, this project aims to provide valuable insights for buyers, sellers, and policymakers.  

Two models were implemented:
- **Linear Regression** (baseline)
- **XGBoost** (advanced ensemble model)  

Results showed that **XGBoost significantly outperformed Linear Regression**, achieving high accuracy and explaining over 90% of the variance in property prices.

---

## 📊 Data Source
The dataset was obtained from Kaggle: [London House Price Data](https://www.kaggle.com/datasets/abdelhamed1/london-house-price-data/data).  

- **Format:** Parquet  
- **Size:** ~418,000 property records  
- **Features include:**
  - Full address, postcode, latitude & longitude  
  - Property characteristics (bedrooms, bathrooms, living rooms, floor area)  
  - Property type & tenure (freehold, leasehold, etc.)  
  - Energy ratings  
  - Historical estimates of rental & sale values  
  - Transaction history (price changes over time)  

🎯 **Target variable:** `saleEstimate_currentPrice` (current estimated market value of each property).

---

## 🔄 Workflow

### 1. Data Cleaning
- Removed non-essential columns (e.g., full addresses, redundant estimates).  
- Removed **5,409 duplicates**.  
- Handled missing values:
  - Dropped features with <5% missing values.  
  - Median imputation for features with 5–20% missing values.  
  - Assigned `"Unknown"` for features with >20% missing values (e.g., energy ratings).  
- Outlier treatment via **percentile capping (0.5th–99.5th)** and **log transformations**.  
- Engineered features:
  - **Bedroom-to-bathroom ratio**  
  - **Time-based features** (year, month, day of week)  

➡️ Final dataset: **400,893 entries × 14 features**

### 2. Exploratory Data Analysis (EDA)
- Identified **multicollinearity** (correlations >0.9) and dropped redundant columns.  
- Distribution analysis showed **right-skewed variables** (floor area, sale price).  
- Boxplots revealed extreme outliers in **floor area and sale price**.  

### 3. Preprocessing
- Standardized numerical features with **StandardScaler**.  
- Encoded categorical variables (`tenure`, `property type`, `energy rating`) using **One-Hot Encoding**.  
- Log-transformed target variable to reduce skewness.  

### 4. Modeling
- **Linear Regression** (baseline model).  
- **XGBoost** with 100 estimators, learning rate 0.1, max depth 6.  

### 5. Evaluation
- Metrics: **MAE, RMSE, R², Adjusted R²**.  

---

## 📈 Results
| Model              | MAE   | RMSE  | R²   |
|--------------------|-------|-------|------|
| Linear Regression  | 0.266 | 0.354 | 0.694 |
| XGBoost            | 0.144 | 0.199 | 0.903 |

✅ **XGBoost achieved an Adjusted R² of 0.903**, showing it captured complex, non-linear relationships effectively.  

---

## 📝 Conclusion
- Thorough **data cleaning and preprocessing** were essential for reliable modeling.  
- **Linear Regression** served as a useful benchmark but had limited predictive power.  
- **XGBoost outperformed significantly**, demonstrating the value of advanced machine learning methods in real estate price prediction.  
- The project highlights that accurate housing price prediction requires both **robust preprocessing** and **powerful models** capable of handling complex feature interactions.  

---

