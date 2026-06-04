# Assignment 4: Decision Tree Model and Business Interpretation

**Business Name:** ProcurePro Office Supplies

---

### The Business Problem

ProcurePro Office Supplies is a B2B procurement company that helps medium sized organizations get the office products they need. The company works with multiple suppliers across Canada to deliver items like printing supplies, cleaning products, and office furniture to clients such as schools, clinics, and consulting firms.

The problem I am solving is supplier delivery uncertainty. Some purchase orders arrive on time and others get delayed because of things like supplier backorder history, poor on time delivery rates, long shipping distances, or urgent order pressure. When a delivery is late and no one anticipated it, the client may run out of supplies, face emergency costs, or lose trust in ProcurePro.

The goal is to build a model that can flag high risk purchase orders before the promised delivery date so the procurement team can step in early.

---

### The Dataset

The dataset contains 360 purchase order records, each representing one order placed with a supplier. It has 19 input features and one target variable.

The input features cover supplier profile information such as supplier category, region, and contract type. They also include order details like order value, number of line items, and whether the order was urgent. Delivery conditions such as shipping mode, distance, and promised lead time are included, along with supplier performance history like past on time rate, supplier rating, and prior delays in the last six months. Risk indicators such as backorder history, quality incidents, and seasonal demand index are also part of the dataset.

The target variable is Supplier_Delay_Risk with two possible values. Yes means the order is high risk for a supplier delivery delay. No means the order is lower risk.

The Backorder_History column had 127 missing values which I filled with the most frequent value in that column before training. The Purchase_Order_ID column was removed because it is just an identifier and carries no predictive value.

---

### The Machine Learning Model

I used a Decision Tree Classifier to solve this classification problem. The model was trained with a maximum depth of 4 to keep it simple and reduce the risk of overfitting. I chose entropy as the splitting criterion instead of the default gini impurity. Entropy measures how uncertain or mixed a group is at each node, and the tree uses information gain to find the split that reduces uncertainty the most. This approach felt more meaningful for a business problem where I am trying to separate genuinely risky orders from safe ones.

The data was split into 80 percent for training and 20 percent for testing. Categorical columns were encoded using one hot encoding before training.

---

### Main Evaluation Results

| Metric | Score |
|---|---|
| Training Accuracy | 0.8715 |
| Testing Accuracy | 0.7222 |
| Precision | 0.7083 |
| Recall | 0.8500 |
| F1 Score | 0.7727 |

The training accuracy is 0.8715 and the testing accuracy is 0.7222. The gap between the two is around 0.15 which suggests some degree of overfitting even with the depth limit applied. The recall score of 0.85 means the model successfully detected 85 percent of the genuinely high risk orders in the test set, which is the most important outcome for this business problem. The precision of 0.71 means that roughly 29 percent of the orders flagged as high risk were actually safe to begin with.

---

### Key Business Insights

The most important features identified by the model were Past_On_Time_Rate, Prior_Delays_Last_6M, Quality_Incidents_Last_6M, Number_of_Line_Items, and Contract_Type_New Supplier.

Past_On_Time_Rate was by far the strongest predictor with an importance score of 0.544. This tells me that a supplier's track record is the single most reliable signal for whether an order will be delayed. ProcurePro can use this to build a formal supplier scoring system and avoid routing critical orders to low scoring suppliers.

Prior_Delays_Last_6M and Quality_Incidents_Last_6M together suggest that recent supplier behavior matters a lot. Suppliers who have been struggling in the past few months are more likely to cause problems on current orders.

The appearance of Contract_Type_New Supplier as a top feature makes practical sense. New supplier relationships carry more uncertainty because there is no established track record to rely on.

These insights give the procurement team clear signals to act on. They do not need to wait for a delay to happen. They can monitor the right indicators in advance and intervene before problems reach the client.

---

### One Limitation of the Model

The dataset used in this assignment is synthetic, meaning it was generated artificially rather than collected from real procurement operations. Because of this, the patterns in the data may not fully reflect the complexity of real world supplier behavior. Real delays can be caused by events like weather disruptions, factory closures, or supply chain shortages that are difficult to simulate in a generated dataset. A model trained on synthetic data may perform differently when applied to actual business data. Before using this model in a real procurement setting, it should be retrained and validated on genuine historical purchase order records.
