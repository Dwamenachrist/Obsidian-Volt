### 1. What is supervised machine learning?
Supervised machine learning is a type of machine learning where the model is trained on labelled data. The training data consists of input-output pairs, where the input is the feature set, and the output is the corresponding label or target. The goal is to learn a mapping from inputs to outputs so that the model can predict the correct output for new, unseen inputs. Common algorithms include linear regression, logistic regression, decision trees, and neural networks.

---

### 2. Stroke Risk Dataset
#### a. How many possible models exist for the scenario described by the features in this dataset?
- There are 4 Boolean features: HIGH BP, SMOKER, DIABETES, HEART DISEASE.
- Each feature can take 2 values (true or false), so there are \(2^4 = 16\) possible combinations of feature values.
- For each combination, the output (STROKE RISK) can be one of 3 categories: low, medium, or high.
- Therefore, the total number of possible models is \(3^{16}\), since each of the 16 input combinations can map to any of the 3 output categories.

#### b. How many of these potential models would be consistent with this sample of data?
- The dataset contains 5 examples, each with a specific combination of features and a corresponding STROKE RISK label.
- A model is consistent with the data if it correctly predicts the STROKE RISK label for all 5 examples.
- For the remaining \(16 - 5 = 11\) combinations not in the dataset, the model can assign any of the 3 categories.
- Therefore, the number of consistent models is \(3^{11}\).

---

### 3. U.S. Census Data: RACE Feature
The higher proportion of the category "White" in the RACE feature might be due to:
- Population Distribution: The white population might naturally be larger in the U.S, so they show up more in the data. Example:  If you surveyed 100 people in a small town where most residents are "White," most survey results will reflect that.
- Sampling bias: The dataset might overrepresent the White population due to how the data was collected. **Example**: If the survey was mostly done in areas with a high "White" population, you'll see more "White" responses.
- Demographic distribution: The dataset might reflect the actual demographic distribution of the U.S., where the White population is the majority.
- Data collection methods: Certain groups might be underrepresented due to barriers in data collection (e.g., language, accessibility).

---

### 4. High Accuracy but Poor Generalization
A model with high accuracy on a dataset might not generalize well after deployment because:
- Overfitting: The model has learned noise or specific patterns in the training data that do not generalize to new data.

- Dataset bias: The training data might not be representative of the real-world data the model encounters after deployment.
	**Simple Example**: Imagine a chef who only practices cooking Italian dishes and excels at it. When asked to cook a French dish, they struggle because their training didn't cover a wide range of cuisines.

- Data drift: The distribution of data might change over time, making the model's predictions less accurate. 
	-**Simple Example**: Consider a weather prediction model trained on past climate data. If climate patterns change due to global warming, the model's predictions based on historical data may become less accurate.

---

### 5. Predictive Analytics for Customer Churn

### NB: Okay so create a list of way she meant like 2 or more
#### Approaches:
1. Churn Prediction Model:
   - Model: Build a classification model (e.g., logistic regression, random forest) to predict the likelihood of a customer churning.
   - Use: Identify high-risk customers and target them with retention strategies (e.g., discounts, personalized offers).
   - Impact: Reduce churn by proactively addressing customer dissatisfaction.

2. Customer Segmentation Model:
   - Model: Use clustering (e.g., k-means) to group customers based on behavior, preferences, and demographics.
   - Use: Tailor marketing campaigns and offers to specific segments.
   - Impact: Improve customer satisfaction and loyalty by addressing specific needs.

3. Recommendation System:
   - Model: Build a collaborative filtering or content-based recommendation system.
   - Use: Suggest movies or content that align with customer preferences.
   - Impact: Increase engagement and reduce the likelihood of churn.

---

### 6. Revenue Commission: Tax Audits
#### a. Machine Learning Solution
One way to address this problem using machine learning is to develop a predictive model that identifies companies likely to be in breach of tax regulations. This model could be a classification model where the target variable indicates whether a company is likely to be non-compliant (yes/no).

- Model: 
	- **Input Features:** Various features from the company's financial data, industry type, location, history of compliance, changes in directorship, and any other relevant data.
    
	- **Model Type:** A supervised learning model, such as a decision tree, random forest, or gradient boosting classifier.
    
	- **Training Data:** Historical data on companies, including their financial reports, tax returns, and past audit results.
-
- Use: Rank companies based on their predicted risk of non-compliance and prioritize audits for high-risk companies.
- Impact: Increase the yield of audits by focusing on companies more likely to be non-compliant.

#### b. Required Data
- Historical audit results (whether a company was found non-compliant).
- Company registration data (industry, location, directors).
- Financial data from tax returns and public filings.

---

### 7. Insurance Policyholders Dataset
#### a. Data Types
![[Pasted image 20250219234440.png]]
# Evidence from text book
![[Pasted image 20250219234508.png]]


#### b. Levels in Categorical/Binary Features
![[Pasted image 20250219234610.png]]


---

### 8. Online Fashion Retailer: Increasing Sales
#### Approaches:
4. Customer Lifetime Value (CLV) Model:
   - Model: Predict the future value of customers based on their purchase history.
   - Use: Target high-value customers with personalized offers.
   - Impact: Increase revenue by focusing on the most profitable customers.

5. Product Recommendation System:
   - Model: Build a recommendation system using collaborative filtering or matrix factorization.
   - Use: Suggest products that align with customer preferences.
   - Impact: Increase sales by improving customer engagement.

6. Demand Forecasting Model:
   - Model: Use time series analysis to predict future demand for products.
   - Use: Optimize inventory management and marketing campaigns.
   - Impact: Reduce stockouts and overstocking, leading to higher sales.

---

### 9. Oil Exploration: Predictive Analytics
#### a. Solution
- Model: Build a binary classification model (e.g., random forest, neural network) to predict the likelihood of finding a viable oil well at a potential site.
- Use: Rank potential drilling sites based on their predicted viability and prioritize high-probability sites.
- Impact: Reduce costs by focusing on sites with the highest likelihood of success.

#### b. Required Data
- Geological data (rock and soil samples, gravitational and seismic measurements).
- Historical data on past drilling sites (success/failure outcomes).
- Environmental data (aerial photographs, ordinance survey maps).

---

### 10. Movie Success Prediction Dataset
**a. Data Types of Features:**

- **ID:** Ordinal (or Numeric Discrete). While a number, it primarily serves as a unique identifier and implies an order.
- **TITLE:** Textual. Movie titles are descriptive text.
- **LENGTH:** Numeric (continuous). Running time is a measurable quantity.
- **RATING:** Ordinal. Movie ratings (G, PG, PG-13, R) have a clear order or ranking.
- **GENRE:** Categorical (nominal). Movie genres are distinct categories with no inherent order.
- **COSTNER:** Binary. This feature represents a true/false or yes/no condition.
- **YEAR:** Numeric (discrete or interval). While we represent it as a number, the year of release has meaning in terms of time, making it closer to an interval type.
- **HIT:** Binary. The movie is either a hit or a miss.

**b. Number of Levels for Categorical, Binary, and Ordinal Features:**

- **ID:** 8 levels (1 through 8 in this sample). In a larger dataset, this would be much higher.
- **RATING:** 4 levels: G, PG, PG-13, R.
- **GENRE:** 6 levels in this sample: action, sci-fi, adventure, drama, children's, comedy. (A larger dataset would likely have more.)
- **COSTNER:** 2 levels: true, false.
- **HIT:** 2 levels: hit, miss.

---

### 11. Hospital Readmission for Diabetes Patients
#### a. Solution
- Model: Build a binary classification model (e.g., logistic regression, gradient boosting) to predict the likelihood of a diabetes patient being readmitted within 30 days.
- Use: Identify high-risk patients and adjust their care plans (e.g., longer hospital stays, post-discharge follow-ups).
- Impact: Reduce readmission rates while avoiding unnecessary hospital stays.

#### b. Required Data
- Patient demographics (age, gender).
- Medical history (previous admissions, comorbidities).
- Treatment details (medications, procedures).
- Post-discharge follow-up data.

---

### 12. Astronaut Oxygen Consumption

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

### 13. Logistic Regression Predictions

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
