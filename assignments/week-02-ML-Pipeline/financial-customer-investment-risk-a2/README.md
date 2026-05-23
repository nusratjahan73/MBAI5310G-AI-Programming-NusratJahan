# Assignment 2: Investment Risk Classification

Course: MBAI 5310G-001 AI Programming
Instructor: Zahra Atf
Institution: Ontario Tech University


## Project Overview

This project builds a supervised machine learning pipeline to predict whether a financial customer is a high investment risk or not. The target variable is High Investment Risk which has two possible values: No (not high risk) and Yes (high risk). This is a binary classification problem.

The goal is to help financial companies identify which customers are likely to take high investment risks so that advisors can provide better and more tailored advice.


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


## Project Structure

```
asiignment2/
|
|-- assignment2_investment_risk.ipynb   Main notebook with full pipeline
|
|-- data/
|   |-- financial_customer_investment_risk_dataset.csv   Raw input dataset
|
|-- output/
|   |-- cleaned_dataset.csv            Dataset after removing duplicates and filling missing values
|   |-- classification_outputs.csv     Actual vs predicted values for all test samples
|
|-- README.md                          This file
```


## Pipeline Steps

The notebook follows these 8 steps.

**Step 1: Understanding the Problem**
Defines the business problem, identifies the target variable and all features, and explains why this is a supervised binary classification task.

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

**Step 7: Model Training**
Trains a Logistic Regression model (max_iter=1000, random_state=42) on the preprocessed training data.

**Step 8: Evaluation**
Evaluates the model using a confusion matrix, accuracy, precision, recall and F1 score. Saves actual vs predicted values to `output/classification_outputs.csv`.


## Results

| Metric | Score |
|---|---|
| Accuracy | 93.42% |
| Precision | 0.00% |
| Recall | 0.00% |
| F1 Score | 0.00% |

Confusion Matrix:

| | Predicted No High Risk | Predicted High Risk |
|---|---|---|
| Actual No High Risk | 71 (True Negative) | 1 (False Positive) |
| Actual High Risk | 4 (False Negative) | 0 (True Positive) |

The model achieved 93.42% accuracy but failed to correctly identify any of the 4 actual high-risk customers in the test set. This is caused by the severe class imbalance in the dataset. The model learned to predict No High Risk for nearly every customer because that strategy produces high overall accuracy on imbalanced data.


## Known Limitation

The dataset is heavily imbalanced with only 5.3% of customers labelled as high risk. This causes Logistic Regression to ignore the minority class entirely. To improve recall on the high-risk class, the following approaches can be applied in future work:

1. Use `class_weight="balanced"` in Logistic Regression to penalize missed high-risk predictions more heavily.
2. Use SMOTE (Synthetic Minority Oversampling Technique) to create synthetic high-risk examples before training.


## How to Run

1. Open the notebook `assignment2_investment_risk.ipynb` in Jupyter Notebook, JupyterLab, VS Code, or Google Colab.
2. Make sure the `data/` folder contains the dataset file.
3. Run all cells from top to bottom using Kernel > Restart and Run All.
4. Output files will be saved automatically to the `output/` folder.


## Requirements

- Python 3.x
- pandas
- scikit-learn
- matplotlib
