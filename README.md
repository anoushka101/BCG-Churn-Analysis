## 📊 Objective

To predict **customer churn** in the electricity retail market by:
- Identifying behavioral and pricing patterns that indicate churn.
- Engineering features from transactional, temporal, and pricing data.
- Training a model that can distinguish churners from non-churners.

---

## 🛠️ Tools & Technologies

- **Python** (Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn)
- **Jupyter Notebook**
- **Feature Engineering**
- **Random Forest Classification**

---

## 🔍 Methodology

### 1. 🧪 Exploratory Data Analysis
- Loaded and merged `client_data.csv` and `price_data.csv`.
- Explored data distributions, missing values, and pricing trends.
- Used summary statistics and plots to understand consumption and churn behavior.

### 2. 🧱 Feature Engineering
- Created features such as:
  - Off-peak price differences (December vs. January).
  - Client net margins and forecasted consumption.
  - Tenure, activity history, and price variability.
- One-hot encoded categorical variables and imputed missing values.

### 3. 🤖 Modeling (Random Forest Classifier)
- Trained a Random Forest model to classify churn (`churn = 1`) vs non-churn (`churn = 0`).
- Evaluated using **confusion matrix**, **precision**, **recall**, and **accuracy**.

#### 📌 Model Performance:

| Metric           | Value        |
|------------------|--------------|
| True Positives   | 18           |
| False Positives  | 4            |
| True Negatives   | 3282         |
| False Negatives  | 348          |
| **Accuracy**     | 0.9036       |
| **Precision**    | 0.8182       |
| **Recall**       | 0.0492       |

> ⚠️ Despite high accuracy, the model struggles to detect churners — recall is very low. Precision is decent, indicating that positive predictions are usually correct, but rare.

---

## 📊 Visualizations

### Churn Percentage
![image](https://github.com/user-attachments/assets/20393340-3093-4001-8593-8812b82fd5c9)

About 10% of customers have churned. 

### 🔹 Feature Importance Chart (Random Forest)

![image](https://github.com/user-attachments/assets/ff0a98b6-d48d-4da0-818c-61820c93ede9)


Key insights:
- **Net margin** and **12-month consumption** are top churn predictors.
- **Power subscription margins** and **forecasted consumption** also rank high.
- **Time-based features** like tenure, months active, and renewal periods are influential.
- **Price sensitivity features** appear, but are not the dominant factors.
  
> These findings suggest that churn is **not primarily driven by price sensitivity**, but by a blend of contract margins, consumption behavior, and customer tenure.

---

## 📈 Key Findings

- The classifier performs well in identifying **non-churners**, with only 4 false positives.
- It performs **poorly on churners**, with 348 false negatives — a recall of just 4.9%.
- This imbalance reveals a serious challenge in predicting rare churn events.
- Feature importance confirms that **pricing factors alone are not enough** — behavioral and contractual metrics are more predictive.

> To improve recall, future work could explore:
> - Balancing the dataset (e.g., SMOTE)
> - Cost-sensitive learning
> - Ensemble methods focused on recall optimization


