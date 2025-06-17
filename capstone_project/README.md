# Predicting the Severity of Car Accidents in California

---

## Project Overview and Goal

The primary objective of this project is to leverage machine learning to understand and predict the severity of car accidents, measured by the number of fatalities. By analyzing a complex set of variables associated with each incident—including environmental conditions, temporal data, and the specific circumstances of the collision—we aim to build a predictive model that can identify key risk factors.

The ultimate goal extends beyond mere prediction; it seeks to uncover actionable insights that could inform public safety initiatives, guide policy-making for transportation agencies, and contribute to the development of safer driving environments.

---

## Research Question

Can the number of fatalities in a car accident in California be accurately predicted based on environmental conditions (weather, light), accident characteristics (manner of collision, harmful event), and temporal factors (hour, day of the week)?

---

## Methodology

This project followed a structured, end-to-end machine learning pipeline, divided into two distinct phases represented by separate notebooks: experimentation and evaluation.

### 1. Data Sourcing and Preprocessing
The analysis is based on the **Fatality Analysis Reporting System (FARS)** dataset, a nationwide census of fatal traffic crashes. The data was first loaded and filtered to isolate records specifically for the state of **California**. To create a focused initial model, a selection of high-impact features was chosen, and the dataset was cleaned by handling rows with missing values.

### 2. Exploratory Data Analysis (EDA)
Before modeling, a thorough EDA was conducted to uncover initial insights and patterns. This involved creating several visualizations:
* **Histograms and Count Plots:** To understand the distribution of key variables like the number of fatalities, the day of the week, and the hour of the day.
* **Correlation Heatmap:** To analyze the linear relationships between the numerical features in the dataset.

### 3. Feature Engineering
To capture more nuanced temporal patterns, a new feature, **TIME_OF_DAY**, was engineered from the `HOUR` column. This categorical feature segments the day into four distinct periods: 'Morning', 'Afternoon', 'Evening', and 'Night'. This new feature was subsequently one-hot encoded to be compatible with the machine learning models.

### 4. Model Building and Hyperparameter Tuning
Two powerful ensemble models were chosen for the regression task of predicting fatalities:
* **Random Forest Regressor:** An enhanced version of this model was developed by applying `RandomizedSearchCV` to perform hyperparameter tuning. This process systematically searches for the optimal combination of model parameters (like the number of trees and max depth) to improve predictive accuracy.
* **XGBoost Regressor:** A Gradient Boosting model, known for its high performance and efficiency, was implemented to serve as a strong comparative benchmark.

### 5. Model Evaluation and Interpretation
A dedicated evaluation notebook was created to analyze the trained models. This involved:
* **Quantitative Comparison:** The performance of the tuned Random Forest and XGBoost models was rigorously compared using standard regression metrics: Mean Absolute Error (MAE), Mean Squared Error (MSE), Root Mean Squared Error (RMSE), and R-squared (R²).
* **Qualitative Analysis:** Visualizations, including scatter plots of actual vs. predicted values and distributions of prediction errors, were generated to provide a more intuitive understanding of model performance.
* **Feature Importance Analysis:** The feature importances from the best-performing model were extracted and visualized to identify which factors were the most influential in predicting accident fatalities.

---

## Findings and Analysis

The evaluation revealed that while both models could make predictions, they struggled with the specific task of regressing the exact number of fatalities. The **R-squared (R²) scores were negative**, which is a critical finding. A negative R² indicates that the models' predictions are, on average, worse than simply predicting the mean number of fatalities for all accidents. This poor performance is primarily attributed to the severe **imbalance in the target variable**, where the overwhelming majority of fatal accidents in the dataset resulted in a single fatality.

Despite the regression challenges, the feature importance analysis provided valuable insights. The most significant predictors of accident severity were consistently identified as:

* **HARM_EV (Harmful Event):** The primary event that caused the harm in the accident (e.g., rollover, collision with a pedestrian).
* **MAN_COLL (Manner of Collision):** The type of collision (e.g., head-on, rear-end, angle).
* **HOUR:** The hour of the day when the accident occurred.

*(Note: The effectiveness of the model is limited by the current dataset for California, which primarily contains accidents with one or more fatalities. This limits the model's ability to distinguish between fatal and non-fatal accidents.)*

---

## Next Steps and Recommendations

Based on the findings, the following steps are recommended for future iterations of this project:

1.  **Reframe as a Classification Problem:** The most critical next step is to transform the problem from regression to binary classification. A new target variable should be created to predict whether an accident was **fatal (1) or non-fatal (0)**. This approach is better suited to the data's nature and is likely to yield a more effective and interpretable model.
2.  **Incorporate More Granular Features:** To enhance the model's predictive power, integrate more detailed features from the original FARS dataset, particularly those related to the vehicle (e.g., `BODY_TYP`, `MAKE`) and more specific geographical data.
3.  **Apply Advanced Imbalance Handling Techniques:** For the new classification task, it will be essential to address the inherent class imbalance. Techniques like **SMOTE (Synthetic Minority Over-sampling Technique)** should be applied to create a more balanced training dataset, which helps the model learn the characteristics of the minority class (fatal accidents) more effectively.
4.  **Explore and Tune Classification Models:** Implement and rigorously evaluate a range of powerful classification algorithms, such as Logistic Regression, Support Vector Machines (SVM), and specifically tuned versions of XGBoost Classifier and Random Forest Classifier.
5.  **Feature Selection:** After creating additional features, apply feature selection methods to identify the most impactful features and potentially simplify the model.
