# BCG-Churn-Analysis

This repository contains a complete customer **churn analysis** workflow, from exploratory data analysis through feature engineering and predictive modelling. The goal is to uncover the key drivers of churn and build robust classifiers to help the business retain high‑risk customers.

## 🎯 Objective

> **Can we predict which customers are most likely to churn?**  
> And — equally important — **which features** (usage, price changes, engagement) **drive** that risk?

---

## 🛠️ Tools & Technologies

- **Python 3.8+**  
- **Pandas**, **NumPy** for data handling  
- **Matplotlib**, **Seaborn** for visualization  
- **Scikit‑learn**, **XGBoost** for modelling  
- **Jupyter Notebook** for interactive analysis  

---

## 🔍 Methodology

### 1. Exploratory Data Analysis (notebooks/EDA.ipynb)
- **Import & inspect** raw data: shape, dtypes, missing values  
- **Descriptive statistics**: summary tables, distributions  
- **Visualize**:
  - Churn rate by segment  
  - Sales channel breakdown  
  - Consumption and forecast trends  
  - Contract types, margins, subscribed power, and other categorical variables  

### 2. Feature Engineering (notebooks/Feature Engineering.ipynb)
- **Merge** customer and price datasets  
- **Price‑difference features**:
  - Δ off‑peak prices (December vs. January)  
  - Mean/max price changes by period & month  
- **Temporal features**:
  - `tenure` (months since activation)  
  - Conversion of dates → numeric month indicators  
- **Categorical encoding**:
  - One‑hot for `channel_sales`, `origin_up`, dropping low‑variance dummies  
- **Boolean & numeric transformations**:
  - `has_gas` flag  
  - Scaling and log‑transforming skewed variables  
- **Correlation analysis** to identify and drop multicollinear features  

### 3. Predictive Modelling
- **Train/test split** with stratification on churn label  
- **Baseline**: Logistic Regression  
- **Ensembles**: Random Forest, XGBoost  
- **Evaluation**:  
  - **Accuracy**, **ROC‑AUC**, **F1 score**  
  - **Cross‑validation** for robust metrics

---

## 📈 Key Findings

### 🔑 Top Predictive Features
| Feature                            | Description                                  |
|------------------------------------|----------------------------------------------|
| `forecast_cons_rolling_mean`       | Recent consumption trend                     |
| `SPC_up_to_1m`                     | Subscribed power change in last month        |
| `price_difference_peak_valley`     | Volatility in pricing                        |
| `num_inbound_calls`                | Customer service interactions                |
| `contract_type_monthly`            | Contract renewal frequency                   |

### 🏆 Model Performance

| Model                | Accuracy | ROC‑AUC | F1 Score |
|----------------------|---------:|--------:|---------:|
| Logistic Regression  |     0.76 |    0.83 |     0.71 |
| Random Forest        |     0.81 |    0.88 |     0.78 |
| **XGBoost**          | **0.83** | **0.91** | **0.81** |

> **XGBoost** achieved the highest ROC‑AUC (0.91) and F1 (0.81), demonstrating strong discrimination between churners and non‑churners.

---

## 📊 Visual Insights

- **EDA**: Distribution plots of churn by channel, consumption, forecast  
- **Correlation heatmap** guiding feature pruning  
- **Feature importance bar chart** from XGBoost  




- **EDA**: Distribution plots of churn by channel, consumption, forecast  
- **Correlation heatmap** guiding feature pruning  
- **Feature importance bar chart** from XGBoost
  ![image](https://github.com/user-attachments/assets/fe7a2c54-fcd3-45df-8604-b6834307181b)
  From this chart, we can observe the following points:
  - Our price sensitivity features are scattered around, but are not the main driver for customer churn
  This observation is important because this relates back to our original hypothesis:

    > Is churn driven by the customers' price sensitivity?

Based on the output of the feature importances, it is **not** a main driver, but it is a weak contributor. However, to arrive at a conclusive result, more experimentation is needed.



---
