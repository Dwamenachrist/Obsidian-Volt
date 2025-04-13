### 1. What is supervised machine learning?
Supervised machine learning is a type of machine learning where the model is trained on labeled data. The training data consists of input-output pairs, where the input is the feature set, and the output is the corresponding label or target. The goal is to learn a mapping from inputs to outputs so that the model can predict the correct output for new, unseen inputs. Common algorithms include linear regression, logistic regression, decision trees, and neural networks.

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
- *Sampling bias*: The dataset might overrepresent the White population due to how the data was collected.
- *Demographic distribution*: The dataset might reflect the actual demographic distribution of the U.S., where the White population is the majority.
- *Data collection methods*: Certain groups might be underrepresented due to barriers in data collection (e.g., language, accessibility).

---

### 4. High Accuracy but Poor Generalization
A model with high accuracy on a dataset might not generalize well after deployment because:
- *Overfitting*: The model has learned noise or specific patterns in the training data that do not generalize to new data.
- *Dataset bias*: The training data might not be representative of the real-world data the model encounters after deployment.
- *Data drift*: The distribution of data might change over time, making the model's predictions less accurate.

---

### 5. Predictive Analytics for Customer Churn
#### Approaches:
1. *Churn Prediction Model*:
   - *Model*: Build a classification model (e.g., logistic regression, random forest) to predict the likelihood of a customer churning.
   - *Use*: Identify high-risk customers and target them with retention strategies (e.g., discounts, personalized offers).
   - *Impact*: Reduce churn by proactively addressing customer dissatisfaction.

2. *Customer Segmentation Model*:
   - *Model*: Use clustering (e.g., k-means) to group customers based on behavior, preferences, and demographics.
   - *Use*: Tailor marketing campaigns and offers to specific segments.
   - *Impact*: Improve customer satisfaction and loyalty by addressing specific needs.

3. *Recommendation System*:
   - *Model*: Build a collaborative filtering or content-based recommendation system.
   - *Use*: Suggest movies or content that align with customer preferences.
   - *Impact*: Increase engagement and reduce the likelihood of churn.

---

### 6. Revenue Commission: Tax Audits
#### a. Machine Learning Solution
- *Model*: Build a binary classification model (e.g., logistic regression, gradient boosting) to predict the likelihood of a company being non-compliant with tax regulations.
- *Use*: Rank companies based on their predicted risk of non-compliance and prioritize audits for high-risk companies.
- *Impact*: Increase the yield of audits by focusing on companies more likely to be non-compliant.