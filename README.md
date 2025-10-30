# 🏠 California Housing Price Prediction – Initial Report (EDA & Baseline)

**Author:** *Krishnan Ramaswami*  

---

## 🧭 Executive Summary

This capstone project explores how demographic, housing, and geographic factors influence real-estate prices in California.  
Using the `fetch_california_housing` dataset, this initial stage covers **data loading, preprocessing, exploratory data analysis (EDA), feature engineering, outlier handling**, and the establishment of a **baseline model** for predictive benchmarking.

---

## 📂 Dataset Overview

| Property             | Description |
|----------------------|-------------|
| **Source**           | California Housing Dataset *(Scikit-learn built-in / Kaggle equivalent)* |
| **Rows**             | 20,640 |
| **Columns**          | 9 |
| **Target Variable**  | `MedHouseValue` |
| **Null Values**      | None |
| **File Size**        | ~1.4 MB |

**Columns:**  
`MedInc`, `HouseAge`, `AveRooms`, `AveBedrms`, `Population`, `AveOccup`, `Latitude`, `Longitude`, `MedHouseValue`

**Data Summary:**  
All features are numerical, with no missing values. The dataset captures demographic and housing attributes across California districts.

---

## ⚙️ Data Preparation and Preprocessing

1. **Train–Test Split:** 80% training / 20% testing.  
2. **Scaling:** Standardized all numeric variables using `StandardScaler`.  
3. **Encoding:** *Not required* – all columns are numeric.  
4. **Feature Engineering:** Added derived ratio-based features to enhance interpretability:  
   - `Rooms_per_Household = AveRooms / AveOccup`  
   - `Bedrooms_per_Room = AveBedrms / AveRooms`  
   - `Population_per_Household = Population / AveOccup`  
5. **Outlier Handling:** IQR-based capping for all numeric and engineered features.

---

## 🔍 Exploratory Data Analysis (EDA)

EDA visualizations were generated to understand distributions, relationships, and spatial trends in the housing data.

### 📊 **Generated Plots**
| Visualization | Description | File |
|----------------|-------------|------|
| **Correlation Heatmap** | Shows relationships among numeric features; `MedInc` strongly correlates with `MedHouseValue`. | `images/Correlation Heatmap.png` |
| **Feature Histograms** | Displays feature distributions after scaling and outlier capping. | `images/housing_feature_histograms.png` |
| **Median Income vs House Value** | Demonstrates direct proportionality between `MedInc` and house value. | `images/median_income_vs_housevalue.png` |
| **Geographic Distribution** | Maps property value clusters by latitude and longitude—high-value districts near coastal California. | `images/geographic_distribution.png` |

### 🔎 **Key Observations**
- **Income:** `MedInc` is the most significant predictor of housing value.  
- **Geography:** High-value homes cluster along the **California coastline** and **urban centers**.  
- **Feature Shape:** Most variables are **right-skewed**, reflecting natural economic distribution.

---

## 🧩 Baseline Model Definition

The **Baseline Model** used in this project is the **Median Predictor**, a simple statistical model that always predicts the **median house value (`MedHouseValue`)** from the training dataset for every record in the test set.  

This approach provides a **non-learning benchmark**, ensuring that advanced machine learning models deliver measurable improvement.

### 📘 **Model Details**

| Parameter | Description |
|------------|--------------|
| **Model Type** | Statistical (Non-ML) |
| **Method** | Predict median of target (`y_train`) |
| **Purpose** | Establish baseline accuracy for comparison |
| **Equation** | `ŷ = median(y_train)` |

### 🧠 **Relevance to Research Question**

> “How accurately can we predict the median house value of California districts based on demographics, housing characteristics, and geography?”

The baseline model provides a reference to determine how much *predictive accuracy* machine learning adds.  
If models such as Random Forest or Ridge Regression outperform the median predictor substantially in R² and error metrics, it validates that the chosen features truly explain housing-price patterns.

### ✅ **Benefits Achieved**
- Defines a **performance baseline** for future models.  
- Acts as a **sanity check** for model learning validity.  
- Measures **predictive contribution** of features like `MedInc`, `Latitude`, and `Longitude`.

---

## 📊 Baseline Model Results

| Metric | Value |
|---------|-------|
| **Mean Squared Error (MSE)** | 1.3762 |
| **Mean Absolute Error (MAE)** | 0.8740 |
| **R² Score** | -0.0502 |

📈 *Interpretation:*  
The R² value below zero confirms that predicting a constant median performs worse than using the mean of the target itself — emphasizing the necessity of data-driven learning models.

---

## 🗂️ Outline of Included Code Sections

1. **Load dataset and inspect structure**  
2. **Feature and task understanding**  
3. **Data cleaning and preparation**  
4. **Preprocessing and scaling**  
5. **Feature engineering**  
6. **Exploratory Data Analysis (EDA)**  
7. **Outlier handling (IQR method)**  
8. **Baseline model performance calculation**

---

## 🚀 Next Steps

Subsequent project stages will involve:
- Training multiple ML models (Linear, Ridge, Decision Tree, Random Forest, etc.)  
- Hyperparameter tuning and comparative evaluation  
- Visualizing model accuracy, feature importance, and learning curves  

---

## 📬 Contact

📧 *your.email@example.com*  
🔗 GitHub: [your-github-username](https://github.com/your-github-username)
