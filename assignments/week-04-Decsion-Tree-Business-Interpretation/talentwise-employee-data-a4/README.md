# Assignment 4: Decision Tree Model and Business Interpretation

**Business Name:** TalentWise Advisory

---

### The Business Problem

TalentWise Advisory is a mid-sized consulting and business services firm with teams across departments like sales, customer support, operations, finance, marketing, IT, and human resources. The company delivers project-based services to corporate clients and depends heavily on skilled employees who carry client knowledge and project experience.

The problem I am solving is employee attrition that goes undetected until it is too late. By the time someone resigns, the company has already lost the window to address the issues that were pushing that person toward the door. The business wants to identify employees who are at risk of leaving before they actually make that decision, so HR managers and department heads can step in early with supportive actions like a workload adjustment, a career conversation, or a salary review.

---

### The Dataset

The dataset contains 360 employee records, each representing one person at the company. It has 17 input features and one target variable.

The features cover the employee profile including department, role level, employment type, and education level. They also include work history variables like tenure, promotion status, and absence days. Workload and effort are captured through overtime hours, workload score, and performance rating. Satisfaction signals include engagement score, manager support score, and salary satisfaction. Work arrangement details like remote work days and commute distance are also included.

The target variable is Left_Company with a value of 1 meaning the employee left and 0 meaning the employee stayed. There were no missing values and no duplicate rows in this dataset. The Employee_ID column was removed before training because it is just a unique label with no predictive value.

One important characteristic of this dataset is a significant class imbalance. Only 68 out of 360 employees left, which is about 19 percent of the data. This means the model had far fewer examples of attrition to learn from compared to examples of employees who stayed.

---

### The Machine Learning Model

I used a Decision Tree Classifier to solve this binary classification problem. The model was trained with a maximum depth of 4 to keep the tree structure manageable and reduce the risk of overfitting. I chose entropy as the splitting criterion. Entropy measures how uncertain or mixed a group is at each decision node, and the tree uses information gain to find the split that reduces uncertainty the most. I chose entropy over gini impurity because it gives a clearer picture of how well each split is separating the two classes, which felt more appropriate for this type of HR problem.

The data was split into 80 percent for training and 20 percent for testing. Categorical columns were encoded using one hot encoding before training.

---

### Main Evaluation Results

| Metric | Score |
|---|---|
| Training Accuracy | 0.8854 |
| Testing Accuracy | 0.6667 |
| Precision | 0.2941 |
| Recall | 0.2941 |
| F1 Score | 0.2941 |

The gap between training accuracy and testing accuracy is approximately 0.22, which indicates overfitting. The model performed well on the data it was trained on but did not generalize as effectively to new employee records. The recall score of 0.29 for the leaver class is the most important number to focus on. It means the model only detected about 29 percent of employees who actually left. This low recall is largely driven by the class imbalance in the dataset. With only 19 percent of records belonging to the attrition class, the model had limited signal to work from.

---

### Key Business Insights

The feature importance analysis revealed that the top predictors of employee attrition were Engagement_Score, Commute_Distance_KM, Tenure_Months, Manager_Support_Score, and Training_Hours_Last_Quarter.

Engagement_Score being the strongest predictor tells me that how connected an employee feels to their work is the most valuable signal available for predicting attrition. A declining engagement score over time is worth investigating before it becomes a resignation letter.

Commute_Distance_KM appearing high in the rankings suggests that long commutes accumulate into a push factor over time. Offering more remote work flexibility to employees with long commutes could help reduce that pressure.

Manager_Support_Score in the top five confirms that how supported an employee feels by their manager is a meaningful driver of the decision to leave. Investing in manager coaching and checking in on teams with low support scores is a practical action the company can take.

Together these insights give the HR team specific, actionable things to monitor rather than waiting for resignation letters to arrive.

---

### One Limitation of the Model

The most significant limitation of this model is the class imbalance in the dataset. Only 19 percent of employees left, which means the model was trained on far more examples of employees who stayed than employees who left. This makes it harder for the model to learn the subtle patterns of attrition. The result is a low recall score for the leaver class, which is precisely the class the business cares most about predicting correctly. In a real HR analytics setting, this would need to be addressed through techniques like class weighting, oversampling the minority class, or collecting more historical attrition data before deploying the model for production use.
