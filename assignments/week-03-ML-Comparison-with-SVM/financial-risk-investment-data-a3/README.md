# Assignment 3: Comparing Classification Models

Course: MBAI 5310G-001 AI Programming
Instructor: Zahra Atf
Institution: Ontario Tech University


## Project Overview

This project extends Assignment 2 by training and comparing two supervised machine learning models to predict whether a financial customer is a high investment risk or not. The target variable is High Investment Risk which has two possible values: No (not high risk) and Yes (high risk). This is a binary classification problem.

The two models compared are Logistic Regression and Support Vector Machine (SVM). Both models are evaluated using the same five metrics so the comparison is fair.

A key improvement over Assignment 2 is the use of `class_weight="balanced"` in both models. In Assignment 2, Logistic Regression was trained without this parameter and scored 0 percent on precision, recall and F1 because the model predicted No High Risk for almost every customer due to the severe class imbalance in the dataset. In this assignment, class weighting is applied to both models to force them to pay more attention to the rare High Risk class during training.


## Dataset

File: `data/financial_customer_investment_risk_dataset.csv`

The dataset contains information about 387 financial customers. After removing 7 duplicate rows the cleaned dataset has 380 rows and 13 columns.

| Column | Type | Description |
|---|---|---|
| Customer_ID | Numerical | Unique identifier for each customer (not used as a feature) |
| Age | Numerical | Age of the customer in years |
| Employment_Status | Categorical | Full-time, Part-time, Retired, Student, or Self-employed |
| Annual_Income | Numerical | Annual income in dollars |
| Investment_Experience_Years | Numerical | Number of years the customer has been investing |
| Portfolio_Value | Numerical | Total current value of investments in dollars |
| Risk_Tolerance | Categorical | Self-reported risk comfort level: Low, Medium, or High |
| Number_of_Investment_Products | Numerical | How many investment products the customer holds |
| Market_Volatility_Concern | Numerical | Score from 1 to 5 for concern about market changes |
| Financial_Literacy_Score | Numerical | Score measuring financial knowledge |
| Advisor_Contacted | Categorical | Whether the customer contacted a financial advisor: Yes or No |
| Previous_Investment_Loss | Categorical | Whether the customer experienced a past investment loss: Yes or No |
| High_Investment_Risk | Categorical | Target variable: Yes or No |

Class distribution: 360 customers are No High Risk (94.7%) and 20 customers are Yes High Risk (5.3%). The dataset is heavily imbalanced.


## Pipeline Steps

The notebook follows these 10 steps.

**Step 1: Understanding the Problem**
Defines the business problem, identifies the target variable and all features, and explains why this is a supervised binary classification task. Introduces the two models to be compared and explains why class weighting is needed.

**Step 2: Data Inspection**
Loads the raw dataset and checks the shape, column names, data types, missing values, duplicate rows, and class distribution.

**Step 3: Data Cleaning**
Creates a clean copy of the dataset, removes 7 duplicate rows, fills missing numerical values with the column median, and fills missing categorical values with the most common value. Saves the cleaned dataset to `output/cleaned_dataset.csv`.

**Step 4: Feature and Target Definition**
Defines X (11 feature columns) and y (target column) from the cleaned data. Converts the target from text (No/Yes) to numbers (0/1).

**Step 5: Train and Test Split**
Splits the data into 80 percent training (304 rows) and 20 percent testing (76 rows) using stratified splitting to preserve class proportions.

**Step 6: Preprocessing**
Applies StandardScaler to numerical features and OneHotEncoder to categorical features using a ColumnTransformer. The preprocessor is fitted only on training data to prevent data leakage.

**Step 7: Training Logistic Regression**
Trains a Logistic Regression model (`max_iter=1000`, `random_state=42`, `class_weight="balanced"`) on the preprocessed training data. The balanced class weight is added as a direct improvement over Assignment 2 where its absence caused 0 percent recall.

**Step 8: Evaluating Logistic Regression**
Evaluates the model using a confusion matrix, accuracy, precision, recall and F1 score.

**Step 9: Training and Evaluating SVM**
Trains a Support Vector Machine model (`kernel="rbf"`, `random_state=42`, `class_weight="balanced"`) and evaluates it using the same four metrics. Uses a turquoise confusion matrix heatmap for visual consistency.

**Step 10: Comparing the Two Models**
Creates a side-by-side comparison table of all four metrics for both models. Displays a grouped pastel bar chart to make the differences easy to see. Saves comparison results to `output/model_comparison_results.csv`.


## Results

### Logistic Regression

| Metric | Score |
|---|---|
| Accuracy | 92.11% |
| Precision | 33.33% |
| Recall | 50.00% |
| F1 Score | 40.00% |

Confusion Matrix:

| | Predicted No High Risk | Predicted High Risk |
|---|---|---|
| Actual No High Risk | 68 (True Negative) | 4 (False Positive) |
| Actual High Risk | 2 (False Negative) | 2 (True Positive) |

### SVM

| Metric | Score |
|---|---|
| Accuracy | 92.11% |
| Precision | 0.00% |
| Recall | 0.00% |
| F1 Score | 0.00% |

Confusion Matrix:

| | Predicted No High Risk | Predicted High Risk |
|---|---|---|
| Actual No High Risk | 70 (True Negative) | 2 (False Positive) |
| Actual High Risk | 4 (False Negative) | 0 (True Positive) |

### Model Comparison

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---|---|---|---|
| Logistic Regression | 92.11% | 33.33% | 50.00% | 40.00% |
| SVM | 92.11% | 0.00% | 0.00% | 0.00% |

Logistic Regression is the better model for this business problem. Although both models achieved the same overall accuracy of 92.11 percent, Logistic Regression correctly identified 2 out of 4 actual High Risk customers while SVM identified none. Adding `class_weight="balanced"` improved Logistic Regression recall from 0 percent (Assignment 2) to 50 percent. SVM still scored 0 percent recall despite the same fix, which shows that the RBF kernel struggles more with this level of class imbalance when the minority training set is very small.


## Key Improvement Over Assignment 2

In Assignment 2, Logistic Regression without `class_weight="balanced"` achieved 93.42 percent accuracy but 0 percent recall. The model was predicting No High Risk for almost every customer and completely missing all real high risk customers.

In this assignment, `class_weight="balanced"` is applied to both models. This tells sklearn to automatically increase the training penalty for misclassifying the minority class. The result for Logistic Regression was a significant improvement: recall increased from 0 percent to 50 percent and F1 score increased from 0 percent to 40 percent.


## How to Run

1. Open `assignment3_investment_risk.ipynb` in Jupyter Notebook, JupyterLab, VS Code, or Google Colab.
2. Make sure the `data/` folder contains the dataset file.
3. Run all cells from top to bottom using Kernel > Restart and Run All.
4. Output files will be saved automatically to the `output/` folder.


## Requirements

- Python 3.x
- pandas
- scikit-learn
- matplotlib
