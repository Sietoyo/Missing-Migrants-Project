# Missing-Migrants-Project
## Analysis of Predictors of Fatal Migration Incidents

### Introduction
Migration incidents often result in tragic outcomes, with many incidents leading to fatalities. Understanding the factors that contribute to fatal migration incidents is crucial for improving safety measures and policies aimed at reducing such occurrences. This analysis aims to identify significant predictors of fatal migration incidents, leveraging data from the Missing Migrants Project by the International Organization for Migration (IOM). By analyzing various factors such as region of incident, migration route, and cause of death, we can gain insights into the key contributors to these tragic events and inform interventions to prevent them.

### Data Overview
The dataset, sourced from the [Missing Migrants Project](https://missingmigrants.iom.int/downloads), contains detailed information about migration incidents, including columns such as "Main ID", "Incident ID", "Incident Type", "Region of Incident", "Incident Date", "Incident Year", "Month", "Number of Dead", "Minimum Estimated Number of Missing", "Total Number of Dead and Missing", "Number of Survivors", "Number of Females", "Number of Males", "Number of Children", "Country of Origin", "Region of Origin", "Cause of Death", "Country of Incident", "Migration Route", "Location of Incident", "Coordinates", "UNSD Geographical Grouping", "Information Source", "URL", "Source Quality", and a binary target variable "Fatal".


### Data Preprocessing
1. **Handling Missing Values:**
   - Numerical columns: Median imputation
   - Categorical columns: Replaced missing values with 'Unknown'
  
2. **Encoding Categorical Variables:**
   - Applied one-hot encoding to "Region of Incident," "Cause of Death," and "Migration Route."

3. **Binary Target Variable:**
   - Created a binary target variable "Fatal" to indicate whether the incident resulted in death.
**Research Question:**  
What factors are significant predictors of fatal migration incidents?

**Methodology:**  
A logistic regression model was used to identify significant predictors of fatal migration incidents. The dataset included categorical predictors such as "Region of Incident," "Migration Route," and "Cause of Death," along with a binary outcome indicating whether the incident was fatal or non-fatal.


### Exploratory Data Analysis
(Included in the analysis)


### Model Selection
Logistic regression was chosen for this analysis due to its suitability for binary classification problems, where the outcome variable has two categories—in this case, "Fatal" vs. "Non-Fatal" incidents. Logistic regression is effective in modeling the probability of a binary outcome based on one or more predictor variables, which aligns well with our goal of identifying significant predictors of fatal migration incidents. Additionally, logistic regression provides interpretable coefficients that help in understanding the relationship between predictors and the outcome, making it a preferred choice for this analysis.


### Model Evaluation
1. **Classification Report:**
   - **Precision for Fatal Incidents (Class 1):** 1.00
   - **Precision for Non-Fatal Incidents (Class 0):** 0.00
   - **Recall for Fatal Incidents (Class 1):** 1.00
   - **Recall for Non-Fatal Incidents (Class 0):** 0.00
   - **F1-score for Fatal Incidents (Class 1):** 1.00
   - **F1-score for Non-Fatal Incidents (Class 0):** 0.00

2. **Confusion Matrix:**
   - **True Negatives (TN):** 0
   - **False Positives (FP):** 4
   - **False Negatives (FN):** 0
   - **True Positives (TP):** 5006

3. **ROC AUC Score:**
   - 0.9557, indicating good overall performance but potentially misleading due to class imbalance.


### Results
- **Class Imbalance:** The dataset shows a severe class imbalance, with a vast majority of incidents labeled as fatal (16688 incidents) and very few as non-fatal (11 incidents).
- **Model Performance for Non-Fatal Incidents:** The model failed to predict any non-fatal incidents, resulting in precision, recall, and F1-scores of 0.00 for the non-fatal class.


### Recommendations
1. **Address Class Imbalance:**
   - Use SMOTE (Synthetic Minority Over-sampling Technique) to oversample the minority class (non-fatal incidents).
   - Adjust class weights in the logistic regression model to penalize misclassifications of the minority class more heavily.

2. **Model Tuning and Validation:**
   - Perform hyperparameter tuning using Grid Search or Random Search to optimize model parameters.
   - Use cross-validation to ensure that the model's performance is consistent across different subsets of the data.

3. **Model Comparison:**
   - Compare the performance of logistic regression with other classification algorithms like Random Forest, Support Vector Machines, or Gradient Boosting to see if another model performs better.

4. **Feature Engineering and Analysis:**
   - Analyze feature importance to understand which features contribute most to the model's predictions.
   - Explore additional feature engineering to create more informative features that might help improve model performance.


### Conclusion
The current logistic regression model highlights significant class imbalance, which hinders its ability to predict non-fatal incidents. By addressing this imbalance and further refining the model through tuning and comparison with other algorithms, we can better identify the factors that significantly predict fatal migration incidents. Implementing these steps can improve the model's accuracy and provide valuable insights into the predictors of fatal migration incidents.
