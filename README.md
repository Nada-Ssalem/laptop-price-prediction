# 💻 Laptop Price Prediction

A machine learning project that analyzes laptop specifications to predict laptop prices in euros using Linear Regression.

---

## 📋 Project Overview

This project uses a dataset of **1,303 laptops** to explore the relationship between laptop features (such as CPU, RAM, screen size, and weight) and their prices. The goal is to build a regression model capable of predicting laptop prices.

---

## 📁 Dataset

**Dataset Link:**
https://www.kaggle.com/datasets/muhammetvarl/laptop-price/data


**Shape:** 1303 rows × 13 columns

| Column             | Type    | Description                          |
|--------------------|---------|--------------------------------------|
| `laptop_ID`        | int     | Unique identifier for each laptop    |
| `Company`          | string  | Manufacturer (e.g., Apple, HP, Dell) |
| `Product`          | string  | Model name                           |
| `TypeName`         | string  | Laptop category (Notebook, Gaming…)  |
| `Inches`           | float   | Screen size in inches                |
| `ScreenResolution` | string  | Display resolution                   |
| `Cpu`              | string  | CPU model and speed                  |
| `Ram`              | string  | RAM size (e.g., 8GB)                 |
| `Memory`           | string  | Storage type and size                |
| `Gpu`              | string  | GPU model                            |
| `OpSys`            | string  | Operating system                     |
| `Weight`           | string  | Weight in kg                         |
| `Price_euros`      | float   | **Target variable** — price in euros |

**Price Statistics:**
- Min: €174 | Max: €6,099 | Mean: €1,123.69

---

## 🔧 Libraries Used

```python
numpy
pandas
matplotlib
seaborn
scikit-learn
```

---

## 🧪 Project Steps

### 1. Data Loading & Exploration
- Loaded CSV with `latin1` encoding
- Inspected data types and shapes (`1303 rows × 13 columns`)
- Confirmed **no missing values** in the dataset

### 2. Exploratory Data Analysis (EDA)
- Computed descriptive statistics (mean, min, max, std)
- Plotted a **correlation heatmap** of numeric features
- Visualized **price distribution** using histogram and boxplot
- Analyzed **laptop type counts** (Notebook, Gaming, Ultrabook, etc.)

### 3. Data Preprocessing
- **Label Encoding:** Applied `LabelEncoder` on `TypeName`
- **Unit Cleaning:**
  - Removed `"kg"` from `Weight` → renamed to `Weight_kg` (float)
  - Removed `"GB"` from `Ram` → renamed to `Ram_GB` (float)
- **Feature Scaling:** Applied both `StandardScaler` and `MinMaxScaler` on `Inches`, `Ram_GB`, `Weight_kg`
- **One-Hot Encoding:** Used `pd.get_dummies()` on the full dataset

### 4. Model Training
- **Model:** `LinearRegression` from scikit-learn
- **Train/Test Split:** 80% train, 20% test (`random_state=42`)
- **Training shape:** 1042 × 1149 features after encoding

### 5. Model Evaluation

| Metric    | Score    |
|-----------|----------|
| R² Score  | **0.618** |
| MSE       | **193,909.42** |

### 6. Feature Importance
Top features influencing price (by coefficient magnitude):
- `Product_EliteBook 820` → **+2,641**
- `Product_EliteBook x360` → **+2,053**
- `Weight_1.13kg` → **+1,786**
- `Product_Inspiron 5770` → **-1,809**

---

## 📊 Laptop Type Distribution

| Type               | Count |
|--------------------|-------|
| Notebook           | 727   |
| Gaming             | 205   |
| Ultrabook          | 196   |
| 2 in 1 Convertible | 121   |
| Workstation        | 29    |
| Netbook            | 25    |

---

## 🚀 How to Run

1. Clone or download the project
2. Install the requirements:
   ```bash
   pip install numpy pandas matplotlib seaborn scikit-learn
   ```
3. Update the CSV file path in the notebook:
   ```python
   MyData = pd.read_csv("path/to/laptop_price.csv", encoding="latin1")
   ```
4. Run `notebook.ipynb` cell by cell

---

## 📌 Notes

- The model achieves an R² of ~0.62, meaning it explains about 62% of the variance in laptop prices.
- Performance could be improved with feature engineering, better encoding strategies, or more advanced models (e.g., Random Forest, XGBoost).