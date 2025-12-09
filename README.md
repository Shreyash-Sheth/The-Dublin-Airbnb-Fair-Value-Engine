# The Dublin Airbnb "Fair Value" Engine
*(A Data Science Portfolio Project using Python & Machine Learning)*

###  Project Overview
In a saturated short-term rental market like Dublin, price does not always equal value. This project analyses **5,000+ active Airbnb listings** to answer a key commercial question:
> **"Can we use Machine Learning to identify properties that are significantly undervalued (Gems) or overpriced (Traps) based on their features?"**

* **Role:** Business Intelligence / Data Analyst
* **Tech Stack:** Python, Pandas, Scikit-Learn (Random Forest), Folium, Seaborn
* **Key Result:** Identified **823 "Undervalued Gems"** (Accuracy: 65%) with an average price gap of >€30/night.

---

### 🔎 Key Insights & Visuals

#### 1. What Drives Price? (The "Answer Key")
Using a Random Forest model, I identified the top features influencing price.
* **Insight:** **Size (Accommodates)** and **Location (GPS)** account for >60% of the price variance. Surprisingly, traditional "Neighbourhood Names" matter far less than exact coordinates.

<img width="990" height="590" alt="image" src="https://github.com/user-attachments/assets/c1251f2a-e461-4af4-9e9b-8b131466da2e" />

#### 2. Statistical Validation (Correlation Matrix)
Before training, I analysed the dataset to understand linear relationships.
* **Insight:** "Accommodates" (0.67) has the strongest positive correlation with price, while "Parking" (-0.01) has virtually no linear correlation, proving that high-value city listings often lack parking. 

<img width="1162" height="989" alt="image" src="https://github.com/user-attachments/assets/1c2524a7-74ff-4d52-905f-ad5f54ca9fb0" />


#### 2. The Opportunity Map
I built an interactive map to visualise the arbitrage.
* **Green Dots:** Undervalued properties (Gems).
* **Red Dots:** Overpriced properties (Traps).
* **Finding:** The City Centre is a high-variance zone, containing the highest density of *both* gems and traps.

<img width="1125" height="607" alt="image" src="https://github.com/user-attachments/assets/341ed5d1-2845-4d98-ab89-f4e3166fa7e6" />

*(Note: Interactive map file available in repo as 'dublin_market_map.html')*

---

### ⚙️ Methodology

#### 1. Data Cleaning & Parsing
* **Constraint:** Raw amenities were stored as JSON strings (e.g., `["Wifi", "Parking"]`).
* **Solution:** Wrote a custom parser to unpack these into binary feature columns.
* **Handling Noise:** Filtered out "Extreme Luxury" outliers (>€1,000/night) and ghost listings (0 reviews) to stabilize the model.

#### 2. Machine Learning Strategy
* **Model Choice:** **Random Forest Regressor**. It captures non-linear relationships (e.g., how the value of 'Parking' changes based on location) better than Linear Regression.
* **Tuning:** Tuned hyperparameters (`n_estimators=500`, `min_samples_leaf=4`) to prevent overfitting.
* **Performance:** Achieved an **R² of 0.65** and **MAE of €47**, meaning the model's price estimates are typically accurate to within €47.

---
*Data Source: [Inside Airbnb](http://insideairbnb.com/get-the-data.html) (Dublin, September 2025)*
