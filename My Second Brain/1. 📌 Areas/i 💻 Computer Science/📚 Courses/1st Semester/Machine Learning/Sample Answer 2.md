Let's break this down question by question:

---

### 1. What is supervised machine learning?

Supervised machine learning is a type of machine learning where the model is trained on labeled data. This means that for each input in the training dataset, the correct output (or label) is provided. The goal of the model is to learn the relationship between the input features and the output label so that it can predict the correct label for new, unseen data.

---

### 2. The following table lists a dataset of five individuals...

#### a. How many possible models exist for the scenario described by the features in this dataset?

- The dataset has 4 Boolean features (HIGH BP, SMOKER, DIABETES, HEART DISEASE), each of which can have two possible values (True/False).
- Thus, there are \( 2^4 = 16 \) possible combinations of these features. For each combination, a model would assign a class (low, medium, high) to the individual.

#### b. How many of these potential models would be consistent with this sample of data?

- A model is consistent if it predicts the same STROKE RISK (low, medium, or high) for each individual based on the given features in the dataset.
- Since we are working with a small dataset (only 5 individuals), the possible models are constrained by the unique combinations of input features and their associated stroke risk labels in the table.
- It’s impossible to calculate the exact number without performing an exhaustive analysis of all possible combinations, but we can say there are multiple models that could be consistent, depending on the labels assigned to various feature combinations.

---

### 3. Why might the RACE feature have a higher proportion of the category White than you expected?

The higher proportion of "White" in the RACE feature could be due to several factors, such as:
- Sampling bias: The dataset might not be representative of the general population, and it might contain more data from regions or groups where White individuals are overrepresented.
- Data collection issues: The way the data was collected could have influenced the representation of different races, leading to an overrepresentation of White individuals.
- Historical or demographic trends: Certain regions or periods might have had higher populations of White individuals, skewing the dataset.

---

### 4. Why might a prediction model with very high accuracy on a dataset not generalize well after deployment?

A high accuracy on the training dataset might indicate overfitting, where the model has learned the noise and specific patterns of the training data rather than the underlying general trends. As a result, it may not perform well on new, unseen data. Overfitting can happen when the model is too complex or trained for too long without sufficient regularization.

---

### 5. Ways predictive analytics could help address the customer churn problem:

- Model: A **classification model (e.g., logistic regression, decision trees) could be built to predict the likelihood of a customer canceling their subscription based on their usage patterns, demographics, etc.
- Business Use: The company could use this model to identify high-risk customers and take proactive measures (such as offering discounts or personalized content) to retain them.
- Impact: By targeting customers who are likely to churn, the company can reduce churn rates and improve customer retention.

---

### 6. Revenue Commission's Audit Problem:

#### a. Propose a machine learning solution:

- Model: A **classification model (e.g., logistic regression, decision trees) could be trained to predict the likelihood of a company being in breach of tax regulations, using historical data like the type of industry, company size, and past audits.
- Business Use: This model would allow the commission to prioritize audits on companies most likely to be non-compliant, reducing wasteful audits.
- Impact: It will make the audit process more efficient and targeted, saving resources and improving compliance detection.

#### b. Data Required:

- Type of data: Historical audit data, including company size, industry type, previous audit results, financial records, etc.

---

### 7. Descriptive Feature Analysis for Insurance Dataset:

#### a. Feature Types:

- ID: Textual (identifier)
- Occupation: Categorical
- Gender: Binary
- Age: Numeric
- Motor Value: Numeric
- Policy Type: Categorical
- Preferred Channel: Categorical

#### b. Levels of Features:

- Occupation: Multiple levels (various occupations listed)
- Gender: 2 levels (Male, Female)
- Policy Type: Multiple levels (Plan A, Plan B, Plan C)
- Preferred Channel: Multiple levels (SMS, Phone, Email)

---

### 8. Predictive Analytics for Online Fashion Retailer:

- Model: A **classification model could be built to predict whether a customer will purchase based on their browsing behavior, demographic information, and previous purchase history.
- Business Use: The model could help the retailer personalize marketing campaigns and product recommendations to increase sales.
- Impact: The retailer can target the right customers with personalized offers, potentially increasing conversion rates and sales.

---

### 9. Predictive Analytics for Oil Exploration Company:

#### a. Machine Learning Approach:

- Model: A **classification model could be used to predict the likelihood of a site having a viable oil well based on geological and environmental features.
- Business Use: The model would help prioritize drilling sites, saving costs by focusing on high-probability sites.
- Impact: This would reduce the number of exploratory drills and improve the efficiency of oil exploration.

#### b. Required Data:

- Data: Geological data, rock/soil sample analysis, seismic measurements, and other environmental indicators.

---

### 10. Predictive Analytics for Movie Hit Prediction:

#### a. Feature Types:

- Title: Textual
- Length: Numeric
- Rating: Ordinal (PG, PG-13, R)
- Genre: Categorical
- Costner: Binary
- Year: Numeric
- Hit: Binary

#### b. Levels of Features:

- Rating: 3 levels (PG, PG-13, R)
- Genre: Multiple levels (e.g., Action, Drama, Comedy, etc.)
- Costner: 2 levels (True, False)
- Hit: 2 levels (Hit, Miss)

---

### 11. Predictive Analytics for Diabetes Patient Readmission:

#### a. Solution:

- Model: A **classification model could predict the likelihood of readmission based on patient history, treatment details, and discharge plans.
- Business Use: The model can assist hospital staff in identifying patients at high risk of readmission and ensuring they receive proper care before discharge.
- Impact: It would help reduce unnecessary readmissions and improve patient care.

#### b. Required Data:

- Data: Patient medical history, treatment plans, discharge notes, and demographic details.

---

### 12. Oxygen Consumption Prediction Model:

![[Pasted image 20250220073108.png]]
![[Pasted image 20250220073124.png]]
![[Pasted image 20250220073144.png]]
![[Pasted image 20250220073204.png]]
![[Pasted image 20250220073226.png]]
![[Pasted image 20250220073244.png]]
![[Pasted image 20250220073345.png]]
#### Sum of Squared Errors (SSE):

SSE=434.31+455.40+353.06+218.15+330.15+287.30+251.86+289.68+181.17+637.56+399.60+196.00SSE=434.31+455.40+353.06+218.15+330.15+287.30+251.86+289.68+181.17+637.56+399.60+196.00
![[Pasted image 20250220073439.png]]

---

### 13. Multivariate Logistic Regression for Repeat Purchase Prediction:

![[Pasted image 20250220074703.png]]
![[Pasted image 20250220074723.png]]

---

### 14. House Price Prediction Model:

#### a. Explanation of Model Errors:

The predictions seem off because the model may have overfitted or there's an issue with the training data (perhaps some features are not properly scaled).

#### b. Strategies to Reduce Errors:

- Regularization: Reduce overfitting.
- Feature engineering: Improve the model by adding more relevant features.

---

### 15. Loan Default Prediction Model Adjustment:

The bank should incorporate additional features to improve predictive power while using regularization techniques to reduce overfitting.

---

### 16. Cross-validation Strategy for Manufacturing Dataset:

A typical cross-validation strategy would involve k-fold cross-validation, where the dataset is split into \(k\) subsets, and the model is trained on \(k-1\) subsets, then tested on the remaining subset. This process is repeated \(k\) times, and the results are averaged.

---

### 17. Regularization for Retail Chain Sales Forecast:

Adjusting the regularization parameter helps balance the model's complexity by penalizing overly complex models that may fit the training data too well, thus avoiding overfitting.

---

### 18. Ridge Regression for Energy Consumption Prediction:

Ridge regression penalizes large coefficients, which helps address multicollinearity by shrinking the influence of highly correlated predictors.

---
