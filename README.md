
# Business Understanding:

Develop a predictive model for used car prices using a vehicle dataset which contains various attributes of the cars. This involves identifying and quantifying the relationships between price and corresponding car attributes such as **mileage, year, make, model, features**. The model needs to evaluate accurately the prices for unseen cars and needs to identify the most dominant features.

# Summary of Findings

The evaluation of the regression models uses Mean Squared Error (MSE) and R-squared (R2).

*   **MSE:** Measures the average squared difference between predicted and actual prices.  Lower MSE indicates better model performance.  

*   **R2:** Represents the proportion of variance in the target variable (price) explained by the model.  Ranges from 0 to 1, with higher values indicating better fit. An R2 of 1 means the model perfectly explains the variance.  An R2 close to 0 means the model does not explain much of the variance.

**Next steps and recommendations:**

1.  **Baseline Model:** Establish a baseline model (e.g., predicting the average price) to compare performance against.  This will provide context for how much better the more complex models are.

2.  **Feature Importance:** The code uses Random Forest.  Random forests provide feature importance scores, which indicate which features have the most influence on the price prediction. The code computes feature importance but doesn't present the scores.   This information will be key to providing insights to the used-car dealership.

3.  **Model Comparison:** Explicitly compare the models using both MSE and R2. Which model performs better according to each metric?

3.  **Root Mean Squared Error (RMSE):**  Consider using RMSE (square root of MSE) which is more interpretable as it's in the same units as the target variable (price).

3.  **Visualizations:** Visualizations (scatter plots of predicted vs. actual, residual plots) will aid in assessing model performance and identifying potential issues.  This can also help explain the performance to the used car dealership.


# Location of Jupyter Notebook: 
practical_application_2.ipynb