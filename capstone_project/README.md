
# California Car Accident Fatality Prediction

## Project Goal

The goal of this project is to build a machine learning model that can predict the number of fatalities in car accidents occurring in California based on various factors like environmental conditions, vehicle characteristics, and time of the incident.

## Research Question

Can the number of fatalities in a car accident in California be accurately predicted based on environmental conditions, vehicle information, and temporal factors at the time of the incident?

## Methodology

This project involved the following steps:

1.  **Data Loading and Exploration:** The dataset containing car accident information was loaded and initially explored.
2.  **Data Preprocessing:** The data was filtered to include only accidents that occurred in California. Relevant features were selected, and missing values were handled by dropping rows.
3.  **Feature Engineering:** Categorical features were converted into a numerical format using one-hot encoding to prepare the data for the machine learning model.
4.  **Model Building:** A Random Forest Regressor model was chosen and trained on the preprocessed and encoded data to predict the number of fatalities.
5.  **Model Evaluation:** The performance of the regression model was evaluated using standard regression metrics.

## Findings

The Random Forest Regressor model was trained to predict the number of fatalities. The evaluation metrics on the test set were as follows:

*   **Mean Absolute Error (MAE):** [Insert MAE value here] - Represents the average absolute difference between the predicted number of fatalities and the actual number.
*   **Mean Squared Error (MSE):** [Insert MSE value here] - Gives more weight to larger prediction errors.
*   **Root Mean Squared Error (RMSE):** [Insert RMSE value here] - The square root of MSE, bringing the error magnitude back to the original scale of fatalities.
*   **R-squared (R2):** [Insert R2 value here] - Indicates the proportion of the variance in the number of fatalities that is predictable by the model.

*(Note: The effectiveness of the model is limited by the current dataset for California, which primarily contains accidents with one or more fatalities. This limits the model's ability to distinguish between fatal and non-fatal accidents.)*

## Next Steps

To potentially improve the model's performance and explore the predictive factors further, the following steps are recommended:

1.  **More Advanced Feature Engineering:**
    *   Create new features from existing time columns (e.g., time of day categories, day type).
    *   Investigate potential interaction terms between features.
    *   If available, incorporate more detailed geographical information.
2.  **Hyperparameter Tuning:** Optimize the parameters of the Random Forest Regressor using techniques like Grid Search or Randomized Search to potentially improve its accuracy.
3.  **Explore Different Models:**
    *   Implement and evaluate other powerful regression models such as XGBoost or LightGBM.
    *   **Try building a Neural Network model** to capture potentially complex non-linear relationships in the data.
4.  **Address Data Limitations:**
    *   If possible, obtain a dataset for California that includes a substantial number of accidents with zero fatalities to enable binary classification or a more robust regression.
    *   Alternatively, explore using data from other states in the original dataset if they contain a mix of fatal and non-fatal accidents.
5.  **Feature Selection:** After creating additional features, apply feature selection methods to identify the most impactful features and potentially simplify the model.
