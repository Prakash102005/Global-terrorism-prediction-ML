# 🌍 Global Terrorism Project
### Predicting Number of Kills in Terrorist Attacks | Supervised Machine Learning + Power BI

> Regression models (Linear Regression, Random Forest, XGBoost) predicting fatalities in terrorist attacks. The tuned Random Forest performed best: R² = 0.19, RMSE = 2.94, MAE = 1.42.

---

## 🎯 Objective
The primary objective of this project is to:

**👉 Predict the number of fatalities (`nkill`) in a terrorist attack using historical data and machine learning.**

This is a **Regression problem**, where the target variable is the number of kills.

---

## 📂 Dataset
- **Source:** Kaggle (Global Terrorism Database)
- **Records:** 180,000+ incidents in the full database (1970–2017)
- **Modeling dataset:** 68,760 records after cleaning and outlier removal
- **Target Variable:** `nkill` → Number of kills

### 🔑 Features Used for Modeling
- `iyear` → Year
- `region_txt` → Region
- `targtype1_txt` → Target type
- `weaptype1_txt` → Weapon type

> Country, attack type, group, city, killed and wounded are used in the EDA (not as model inputs).

---

## 🧠 Problem Type
- ✔ Supervised Learning
- ✔ Regression Problem
- ✔ Goal: Predict a continuous value (fatalities)

---

## ⚙️ Methodology

### 🔹 1. Data Preprocessing
- Loaded GTD (`latin1` encoding) and selected relevant columns
- Filled missing `nkill` / `Killed` / `Wounded` with 0 and missing `City` with "Unknown"
- Removed the top 1% of `nkill` values (right-skewed outliers)
- Applied **Label Encoding** to weapon, target and region (one encoder per column, so values can be decoded back)
- Train-test split: **80/20** (55,008 train / 13,752 test, `random_state=42`)

### 🔹 2. Feature Engineering (for EDA)
- `total_casualties` = Killed + Wounded
- `high_casualty` = flag for 10+ casualties
- `decade` = temporal grouping
- Group attribution flag (known vs. unknown group)

### 🔹 3. Exploratory Data Analysis (EDA)
- Attacks per year (trend)
- Top 10 countries by attacks
- Attacks by region
- Attack types and weapon types
- Casualty distribution and correlation heatmap (kills, wounds, total casualties)

👉 **Insight:** Fatalities are heavily right-skewed: most incidents have 0–2 deaths, and a few extreme events drive the tail.

### 🔹 4. Model Development
Three models were trained and compared:
- **Linear Regression** (baseline)
- **Random Forest Regressor**
- **XGBoost Regressor**

The Random Forest was then tuned with **5-fold GridSearchCV** (`n_estimators`, `max_depth`, `min_samples_split`; 60 fits).

**Why Random Forest:** captures non-linear relationships and provides feature importance.

### 🔹 5. Model Evaluation
Metrics: **MAE**, **RMSE**, **R² Score**, measured on unseen test data.

| Model | MAE | RMSE | R² |
|---|---|---|---|
| Linear Regression (baseline) | 1.7715 | 3.2162 | 0.0265 |
| Random Forest (default) | 1.4241 | 2.9780 | 0.1654 |
| XGBoost | 1.4799 | 2.9555 | 0.1779 |
| **Random Forest (tuned)** | **1.4226** | **2.9386** | **0.1873** |

- **Best parameters:** `max_depth=10`, `min_samples_split=5`, `n_estimators=200`
- **Best 5-fold CV R²:** 0.1973

👉 Tree-based models clearly beat the linear baseline. Overall predictive power is modest (R² ≈ 0.19) because only four categorical features were used.

### 🔹 6. Feature Importance (Tuned Random Forest)
| Feature | Importance |
|---|---|
| Target type | 0.309 |
| Weapon type | 0.258 |
| Region | 0.256 |
| Year | 0.178 |

---

## 📊 Power BI Dashboard
Built an interactive dashboard to support analysis and insights:

**🔹 Key Visuals:**
- **KPI Cards:** Total Attacks, Total Fatalities, Average Fatalities
- 🌍 **Map** → Fatalities by country
- 📈 **Line Chart** → Year vs Fatalities
- 🎯 **Slicers** → Region, Attack Type, Year

👉 Helps in identifying high-risk regions and patterns affecting fatalities.

> 📸 Dashboard screenshots / `.pbix` file: *add to the `/powerbi` folder and link here*

---

## 📈 Results
- Tuned Random Forest cut RMSE from **3.22 → 2.94** and raised R² from **0.03 → 0.19** versus the linear baseline
- **Target type** and **weapon type** were the strongest predictors of fatalities
- Fatalities are highly skewed, which limits accuracy of any model using only these features


## 🛠 Tools & Technologies
- **Python:** Pandas, NumPy, Matplotlib, Seaborn
- **Machine Learning:** Scikit-learn (Linear Regression, Random Forest, GridSearchCV), XGBoost
- **Visualization:** Power BI
- **Environment:** Google Colab, Jupyter Notebook

---

## ▶️ How to Run
```bash
git clone https://github.com/Prakash102005/Global-terrorism-prediction-ML.git
cd Global-terrorism-prediction-ML
pip install pandas numpy matplotlib seaborn scikit-learn xgboost jupyter
# Download the Global Terrorism Database from Kaggle and place the CSV in this folder
jupyter notebook Global_Terrorism_Complete_Project.ipynb
```
Update the CSV path in the notebook (`/content/Global Terrorism Data.csv` is the Colab path).

---

## 👤 Author
**Saiprakash Yamsani** | [GitHub](https://github.com/Prakash102005) | [LinkedIn](https://www.linkedin.com/in/)
