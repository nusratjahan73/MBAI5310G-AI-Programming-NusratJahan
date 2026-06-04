# Assignment 5: Unsupervised Learning for Pattern Discovery and Customer Segmentation

**Business Name:** ReturnWise Retail Analytics

---

### The Business Problem

ReturnWise Retail Analytics is a decision-support project for a mid-sized online retailer selling apparel, footwear, electronics, beauty products, home goods, and accessories. The company processes thousands of orders each month but is struggling with high product return rates that are eating into profit margins and making inventory planning difficult.

The goal of this assignment is to use unsupervised learning to discover hidden patterns in the order data and group customers into meaningful segments based on their purchasing and return behavior. This helps the business move from reacting to returns after they happen to understanding which types of orders carry higher risk before those returns occur.

---

### The Dataset

The dataset contains 455 order records with 22 columns. After removing 5 duplicate rows, the working dataset has 450 records. The columns cover customer profile information, product details, purchase channel, shipping method, discount and promotion data, past customer behavior, and a Returned column indicating whether the order was returned.

Missing values were present in four columns. Region had 7 missing entries filled with the most frequent value. Product_Price and Discount_Percent each had 6 missing entries filled with the median. Product_Rating had 7 missing entries filled with the median.

I selected 11 numerical features for clustering: Customer_Age, Product_Price, Discount_Percent, Delivery_Time_Days, Items_In_Order, Previous_Orders, Prior_Return_Count, Product_Rating, Product_Page_Views, Return_Window_Days, and Returned. All features were scaled using StandardScaler before training.

---

### The Clustering Method

I used K-Means Clustering, an unsupervised machine learning algorithm that groups data points into K clusters based on similarity. Before training, I applied the Elbow Method by testing K values from 1 to 10 and plotting the inertia for each. The inertia dropped most noticeably up to K=3, after which the improvement became smaller with each additional cluster. I chose K=3 because it produces three clearly distinct and business-meaningful segments.

The final model was trained with K=3, random_state=42, and n_init=10. I also applied PCA to reduce the 11 features into two components for 2D visualization purposes. PCA was used only for visualization and did not affect the cluster assignments.

---

### The Main Results

The K-Means model produced three customer and order segments with very distinct characteristics.

| Segment | Orders | Avg Previous Orders | Avg Discount | Return Rate |
|---|---|---|---|---|
| High Return Risk Orders | 131 | 6.17 | 14.16% | 100% |
| Loyal Frequent Buyers | 116 | 15.32 | 10.04% | 3% |
| Occasional Safe Buyers | 203 | 3.65 | 10.74% | 0% |

The High Return Risk segment stands out immediately because every single order in this group was returned. These orders had the highest average discount and the lowest product rating. The Loyal Frequent Buyers group has the most purchase history and almost no current returns. The Occasional Safe Buyers are the largest group, with newer customers who buy carefully and return nothing.

---

### The Business Recommendation

For High Return Risk Orders, I recommend reviewing the discount and promotion strategy to attract customers who genuinely want the product rather than impulse buyers. Improving product descriptions, size guides, and product photos would also help reduce the gap between customer expectations and what they receive.

For Loyal Frequent Buyers, I recommend a loyalty program with tier-based rewards, personalized recommendations, and early access to new products. These customers are already the most valuable and retaining them is more cost-effective than acquiring new ones.

For Occasional Safe Buyers, I recommend a content strategy that introduces them to more products based on their safe purchase history. Gentle re-engagement campaigns and reliable delivery experiences can help move this group toward becoming more frequent buyers.

Overall, this analysis shifts the business from a reactive returns management approach to a proactive one. The segments give the marketing and operations teams a clear picture of where to focus attention and resources.

---

### One Limitation

The dataset is synthetic and may not fully reflect real customer behavior. The patterns in real retail data would likely show more overlap between segments and be influenced by external factors like seasonality and economic conditions. Before using this model in a production environment, it should be validated on real historical order data and reviewed regularly for fairness and accuracy.
