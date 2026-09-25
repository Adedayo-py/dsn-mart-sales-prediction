# dsn-mart-sales-prediction
# 🛒 DSN Mart Sales Prediction

A machine learning project developed for the **DSN AI Bootcamp 2026 – Machine Learning Track**.

The goal of this project is to predict product sales for **DSN Mart**, using information about products, prices, stores, and store characteristics.


## 📌 Project Overview

Retail businesses need accurate sales predictions to support decisions around inventory, pricing, and store operations.

In this project, I built and evaluated several machine learning models to predict the `total_sales` of products across DSN Mart stores.

The workflow covers:

- Data exploration and understanding
- Data cleaning and preprocessing
- Feature engineering
- Model experimentation
- Model evaluation using RMSE
- Kaggle submission and leaderboard evaluation
- Final model selection


## 📊 Dataset

The dataset contains information about products and stores.

### Training set

- **6,818 rows**
- Target variable: `total_sales`

### Test set

- **1,705 rows**
- Used to generate the final Kaggle predictions

### Key Features

Some of the important variables include:

| Feature | Description |
|---|---|
| `product_code` | Unique product identifier |
| `product_weight_kg` | Product weight |
| `fat_content` | Product fat-content category |
| `product_category` | Product category |
| `product_price` | Product price |
| `shelf_visibility` | Product visibility on the shelf |
| `store_code` | Store identifier |
| `store_size` | Store size category |
| `store_location_tier` | Store location category |
| `store_format` | Store format |
| `store_age_years` | Age of the store |
| `total_sales` | Target variable |


## 🔎 Exploratory Data Analysis

The data was explored to understand:

- Product and store distributions
- Missing values
- Numerical feature ranges
- Categorical variables
- Product frequency across stores
- Store-level patterns
- Relationships between price and sales

The dataset contains **1,555 unique products** across **10 stores**.

Most products appear across multiple stores, making product and store information particularly useful for modelling.

---

## 🛠️ Feature Engineering

Several features were tested during experimentation, including:

- Price per kilogram
- Price × shelf visibility
- Weight × shelf visibility
- Product frequency
- Store frequency
- Product-level price statistics
- Store-level price statistics
- Log-transformed product price
- Price relative to store average

Not every engineered feature improved performance, so features were evaluated experimentally rather than automatically included in the final model.


## 🤖 Models Tested

Several approaches were evaluated using validation RMSE.

### Baseline

A simple mean-sales baseline was established before training more advanced models.

### Random Forest

A Random Forest regression model was tested as a tree-based baseline.

### LightGBM

LightGBM was evaluated both independently and as part of blending experiments.

### CatBoost

CatBoost performed strongly on the dataset because it can work directly with categorical variables such as product and store identifiers.

The final modelling experiments focused primarily on CatBoost.


## 🧪 Model Experimentation

Different CatBoost configurations and feature sets were tested, including:

- Tree depth
- Learning rate
- L2 regularization
- Random seeds
- Feature selection
- Additional price features
- Model blending
- Five-fold cross-validation

A compact feature set performed strongly during local validation:

```text
product_code
product_price
store_code
store_format
product_category
store_age_years
