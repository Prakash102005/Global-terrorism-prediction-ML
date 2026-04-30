# Global-Terrorism

**Predicting Number of Kills in Terrorist Attacks**
Supervised Machine Learning + Power BI Project

Objective

**The primary objective of this project is to:**

**👉 Predict the number of fatalities ** (nkill) in a terrorist attack using historical data and machine learning techniques.

This is a regression problem, where the target variable is the number of kills.


**📂 Dataset**
**Source: **Global Terrorism Database (GTD)
**Records:** 180,000+ incidents
**Target Variable:**
  nkill → Number of kills

**🔑 Features Used:**
iyear → Year
region_txt → Region
country_txt → Country
attacktype1_txt → Attack type
targtype1_txt → Target type
weaptype1_txt → Weapon type

**🧠 Problem Type**
✔ Supervised Learning
✔ Regression Problem
✔ Goal: Predict continuous values (fatalities)

**⚙️ Methodology**
🔹 1. Data Preprocessing
Handled missing values (filled nkill with 0)
Selected relevant features
Applied one-hot encoding for categorical variables

🔹 2. Exploratory Data Analysis (EDA)

Performed analysis to understand factors affecting fatalities:

Year vs fatalities trend
Region-wise distribution
Attack type vs kills
Weapon type vs kills

👉 Insight: Certain attack types and weapons result in significantly higher fatalities.

🔹 3. Model Development


Model Used: Random Forest Regressor


Why:


Captures non-linear relationships


Handles categorical features well


Provides feature importance





🔹 4. Model Evaluation


MAE (Mean Absolute Error): Measures prediction error


R² Score: Measures how well the model explains variance


👉 The model achieved good predictive performance on unseen data.

🔹 5. Feature Importance
Top factors influencing number of kills:


Attack Type


Weapon Type


Region



📊 Power BI Dashboard
Built an interactive dashboard to support analysis and insights:
🔹 Key Visuals:


KPI Cards:


Total Attacks


Total Fatalities


Average Fatalities




🌍 Map → Fatalities by country


📈 Line Chart → Year vs Fatalities


🎯 Slicers → Region, Attack Type, Year


👉 Helps in identifying high-risk regions and patterns affecting fatalities

📈 Results


Bombing/explosion attacks contribute to the highest number of kills


Certain regions consistently show high fatality rates


Fatalities depend heavily on attack and weapon type


Model successfully predicts kill count with reasonable accuracy



🛠 Tools & Technologies


Python: Pandas, NumPy, Scikit-learn


Machine Learning: Random Forest Regression


Visualization: Power BI


Environment: Google Colab, Jupyter Notebook

