# California Housing Price Prediction

## 📌 Project Overview

This project was completed as **Task 3** of my **Machine Learning Internship at Arch Technologies**.

The objective of this project is to build and evaluate machine learning regression models for predicting **median house values in California** using demographic, geographic, and housing-related features.

The project covers the complete machine learning workflow, including:

* Data loading and exploration
* Data quality analysis
* Missing-value handling
* Feature engineering
* Exploratory Data Analysis (EDA)
* Data preprocessing
* Model training
* Model comparison
* Model evaluation
* Cross-validation
* Overfitting analysis
* Feature importance analysis
* Model saving

---

## 📊 Dataset

**Dataset:** California Housing Prices

**Source:** Kaggle – California Housing Prices

Dataset characteristics:

* **Rows:** 20,640
* **Original columns:** 10
* **Target variable:** `median_house_value`
* **Missing values:** 207 in `total_bedrooms`
* **Duplicate rows:** 0

### Main Features

* `longitude`
* `latitude`
* `housing_median_age`
* `total_rooms`
* `total_bedrooms`
* `population`
* `households`
* `median_income`
* `ocean_proximity`

---

## ⚙️ Feature Engineering

Three additional features were created to provide more meaningful information to the models:

* `rooms_per_household`
* `bedrooms_per_room`
* `population_per_household`

These features were calculated from the original housing and population variables.

---

## 🧹 Data Preprocessing

The following preprocessing steps were applied:

### Numerical Features

* Median-value imputation
* StandardScaler normalization

### Categorical Features

* Most-frequent imputation
* One-hot encoding
* Unknown categories handled using `handle_unknown="ignore"`

A `ColumnTransformer` and separate preprocessing pipelines were used to keep the workflow organized and reproducible.

---

## 🤖 Machine Learning Models

Four regression algorithms were trained and compared:

1. Linear Regression
2. Random Forest Regressor
3. Extra Trees Regressor
4. Gradient Boosting Regressor

### Model Performance

| Model             |        MAE |       RMSE |     R² |
| ----------------- | ---------: | ---------: | -----: |
| Linear Regression | $49,645.49 | $69,127.04 | 0.6353 |
| Random Forest     | $31,586.19 | $48,875.77 | 0.8177 |
| Extra Trees       | $32,689.50 | $49,921.76 | 0.8098 |
| Gradient Boosting | $31,157.86 | $48,322.68 | 0.8218 |

The Gradient Boosting model achieved an **R² score of 0.8218** on the test set.

> R² is used as a regression evaluation metric and should not be interpreted as classification accuracy.

---

## 🏆 Final Model

The selected Gradient Boosting Regressor used the following configuration:

```python
GradientBoostingRegressor(
    n_estimators=300,
    learning_rate=0.05,
    max_depth=5,
    min_samples_split=2,
    min_samples_leaf=2,
    loss="huber",
    random_state=42
)
```

### Final Test Results

* **MAE:** $31,157.86
* **RMSE:** $48,322.68
* **R²:** 0.8218

The model explains approximately **82.18% of the variance** in the test-set target values.

---

## 🔄 Cross-Validation

Five-fold cross-validation was performed to evaluate model consistency.

* Mean R²: **0.8275**
* Standard deviation: **0.0040**

Cross-validation R² scores:

```text
0.8310
0.8240
0.8230
0.8333
0.8261
```

---

## 📈 Overfitting Analysis

The final model produced:

* Training R²: **0.8757**
* Testing R²: **0.8218**
* Train-Test Gap: **0.0539**

This comparison was used to assess the model's generalization behavior.

---

## 🔍 Feature Importance

The most influential features in the final model included:

| Feature                  | Importance |
| ------------------------ | ---------: |
| median_income            |     0.5432 |
| ocean_proximity_INLAND   |     0.1742 |
| population_per_household |     0.0936 |
| longitude                |     0.0640 |
| latitude                 |     0.0593 |

---

## 📊 Visualizations

The notebook contains visualizations for:

* Target variable distribution
* Feature correlation
* Geographic distribution of housing data
* Model performance comparison
* Actual vs. predicted values
* Residual/error analysis
* Feature importance

---

## 💾 Saved Model

The trained model was saved as:

```text
california_housing_price_model.pkl
```

The model can be loaded later using `joblib`.

---

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-learn
* Joblib
* Google Colab
* Kaggle Dataset

---

## 📁 Project Files

```text
Task-3-California-Housing-Price-Prediction/
│
├── California_Housing_Price_Prediction.ipynb
├── california_housing_price_model.pkl
└── README.md
```

---

## 🎯 Learning Outcomes

Through this project, I practiced:

* Regression problem formulation
* Data preprocessing
* Feature engineering
* Exploratory data analysis
* Multiple regression algorithms
* Model comparison
* Cross-validation
* Error analysis
* Feature importance interpretation
* Model serialization

---

## 👩‍💻 Internship

**Machine Learning Internship — Arch Technologies**

**Task:** California Housing Price Prediction

**Month:** Month 2

**Author:** Syeda Abeera Haya
