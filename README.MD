# README for Diabetes Prediction Using Machine Learning

---

## Project Overview
This project analyzes a diabetes dataset using various data preprocessing and machine learning techniques to predict the likelihood of diabetes in individuals. The analysis includes data cleaning, feature engineering, and model training with performance evaluation using metrics like accuracy.

---

## Dataset
- **Source:** [Kaggle - Diabetes Dataset](https://www.kaggle.com/datasets/mathchi/diabetes-data-set)
- **Description:**
  - The dataset contains 768 observations with 9 columns. Each row represents an individual, and the columns represent their medical diagnostic data.
  - **Features:**
    - **Pregnancies:** Number of times the individual has been pregnant.
    - **Glucose:** Plasma glucose concentration (mg/dL) measured after a 2-hour oral glucose tolerance test.
    - **BloodPressure:** Diastolic blood pressure (mm Hg).
    - **SkinThickness:** Triceps skinfold thickness (mm), a measure of body fat.
    - **Insulin:** Serum insulin levels (µU/mL) measured after a 2-hour test.
    - **BMI:** Body mass index (weight in kg / (height in m)^2).
    - **DiabetesPedigreeFunction:** A score indicating diabetes risk based on family history.
    - **Age:** Age of the individual in years.
    - **Outcome:** Target variable indicating whether the individual has diabetes (1) or not (0).
  - **Key Insights:**
    - Certain features, such as `Glucose` and `BMI`, show stronger correlations with the diabetes outcome.
    - Missing or zero values are observed in `Glucose`, `BloodPressure`, `SkinThickness`, `BMI`, and `Insulin`, which require imputation for accurate analysis.

---

## Key Dependencies
- **Python Libraries:**
  - `numpy`, `pandas`: Data manipulation
  - `matplotlib`, `seaborn`: Data visualization
  - `scikit-learn`: Machine learning models and evaluation metrics
  - `rasterio`: Handling raster data (for visualization purposes)
  - `warnings`: Ignoring unnecessary warnings

---

## Workflow and Results

### 1. Data Loading and Initial Analysis
- The dataset was loaded, and initial inspections revealed:
  - No null values, but several features contained `0`, which were considered missing values.
  - Features like `Glucose`, `BloodPressure`, and `BMI` needed cleaning and imputation.
- Dataset preview provided information on column types and distributions.

### 2. Data Cleaning
- **Methods Used:**
  - Replaced zero values with:
    - **Mean and Median Values**: Based on the diabetes outcome.
    - **KNN Imputation**: Handled missing values using 3 nearest neighbors for interpolation.
- **Results:**
  - Mean and median provided a simple strategy for imputation.
  - KNN imputation yielded better correlation among features and improved dataset completeness.

### 3. Data Visualization
- **Results:**
  - Distributions of features (like `Glucose`, `BMI`, etc.) showed distinct trends for individuals with diabetes (Outcome = 1) versus those without (Outcome = 0).
  - Correlation heatmaps highlighted strong relationships between features:
    - `Glucose` had the strongest correlation with the diabetes outcome.

### 4. Feature Engineering
- **Normalization:**
  - Applied Z-score normalization \((x - \mu) / \sigma\) to standardize all features.
- **Results:**
  - Improved model performance due to scaled feature ranges.

### 5. Machine Learning Models
- **K-Nearest Neighbors (KNN):**
  - Tested with varying `k` values to find optimal neighbors.
  - **Results:**
    - Best `k` = 5 with an accuracy of **78%** on the test set.
- **Grid Search with Cross-Validation:**
  - Tested several models with parameter tuning:
    - **Support Vector Machines (SVM):** Achieved **79%** accuracy.
    - **Decision Tree:** Achieved **77%** accuracy with `max_depth=8`.
    - **Random Forest:** Achieved **82%** accuracy with `n_estimators=15` and `max_depth=5`.
    - **Logistic Regression:** Achieved **76%** accuracy.
    - **Naive Bayes:** Achieved **74%** accuracy.

### 6. Model Evaluation
- **Confusion Matrix:**
  - Visualized predictions versus actual outcomes using percentages.
  - **Results:**
    - Random Forest had the best performance with a balanced confusion matrix and high precision.

### 7. Prediction
- Tested the Random Forest model on new, unseen data.
- **Results:**
  - The model predicted diabetes outcomes for the test inputs accurately.

---

## Comparison of Imputation Methods
- **Mean:** Simple, but not effective for highly skewed distributions.
- **Median:** Better for features with outliers.
- **KNN Imputation:** Provided the most accurate and consistent results by considering feature relationships.

---

## How to Use
1. Clone this repository or download the code.
2. Install the required libraries:
   ```bash
   pip install numpy pandas matplotlib seaborn scikit-learn rasterio
   ```
3. Download the dataset from the Kaggle link and place it in the project directory.
4. Run the Jupyter notebook file (`diabetes.ipynb`) step by step to preprocess the data, train models, and evaluate performance.

---

## Future Improvements
- Experiment with advanced feature selection techniques.
- Incorporate additional data, if available, for better generalization.
- Use deep learning models for potentially better performance.
