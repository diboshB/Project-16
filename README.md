# Project-16
Captsone_Project - Clustering - Supermarket_Analysis

1. Introduction
Customer behavior in a supermarket context is a critical factor for improving
business strategies such as marketing, inventory management, and product
placement. By clustering customers based on their purchasing behavior,
supermarkets can identify distinct customer segments, tailor product
recommendations, optimize promotions, and improve operational efficiency.
This project utilizes unsupervised machine learning techniques to analyze and
segment supermarket customers, focusing on their order patterns, product
choices, and overall shopping behavior.
The goal of this analysis is to cluster customers using purchase-related
features and provide actionable insights that businesses can leverage to
enhance customer engagement and streamline their operations.
2. Data Collection
The dataset used in this project is derived from a supermarket's transaction
records. The data consists of several features that capture customer order
behaviors, including:
• order_id: Unique identifier for each order.
• user_id: Unique identifier for each customer.
• order_number: The sequential number of the order placed by a user.
• order_dow: The day of the week the order was placed.
• order_hour_of_day: The hour of the day when the order was placed.
• days_since_prior_order: The number of days since the customer's
last order.
• product_id: ID of the product purchased.
• add_to_cart_order: The position of the product in the shopping cart.
• reordered: Indicates if the product was previously ordered.
• department_id: The department to which the product belongs.
• department: Name of the product department.
• product_name: Name of the product.
This dataset provides a comprehensive view of customer purchasing patterns,
which can be used for further segmentation and clustering.
3. Data Preprocessing
Before performing clustering, several preprocessing steps were applied to
clean and prepare the data:
3.1 Handling Missing Values
• Missing values in the 'days_since_prior_order' column: The
missing values were filled with the median value of this column to ensure
no data is lost.
• No missing values were identified in other columns based on the
output from data.isnull().sum().
3.2 Feature Engineering
• Dropping Irrelevant Columns: The order_id column was dropped as it
was not relevant for clustering.
• Binary Column Conversion: Any Boolean columns (if present) were
converted to integers (0 or 1).
3.3 Scaling
• MinMax Scaling: Continuous numerical features (e.g., order_number,
days_since_prior_order, etc.) were scaled using MinMax scaling to
normalize the data between 0 and 1, ensuring that all features
contribute equally during clustering.
4. Clustering and Number of Clusters
4.1 Feature Selection
The selected features for clustering include:
• order_number: Indicates how many orders the customer has placed,
which is an important feature to measure customer loyalty.
• days_since_prior_order: Reflects customer frequency and purchase
recency, which are crucial for segmentation.
• add_to_cart_order: Represents how often a customer adds products
to their cart, providing insight into shopping behavior.
• reordered: This feature is essential for understanding repeat purchase
behavior.
• unique_products: The number of unique products a customer has
purchased, which reflects variety in purchasing behavior.
4.2 Clustering Model (DBSCAN)
The DBSCAN (Density-Based Spatial Clustering of Applications with Noise)
algorithm was chosen because it can identify clusters of varying shapes and
sizes and can handle noise effectively. The model was applied with the
following parameters:
• eps=0.5: This parameter defines the maximum distance between two
points for them to be considered as in the same neighborhood.
• min_samples=5: Minimum number of samples in a neighborhood to form
a dense region (cluster).
The DBSCAN algorithm assigns each customer to a cluster or labels them as
noise (denoted by -1).
4.3 Results of Clustering
After applying DBSCAN, customers were clustered into different segments
based on their purchasing patterns. The results showed a range of clusters,
with some customers being categorized as noise (those with no clear cluster,
labeled as -1).
5. Model Evaluation
5.1 Silhouette Score
To evaluate the quality of the clusters, the Silhouette Score was calculated.
The silhouette score measures how similar an object is to its own cluster
compared to other clusters, with a score close to 1 indicating well-defined
clusters. The computed silhouette score for the model was 0.50, indicating
that the clustering performed moderately well but could be improved.
5.2 Cluster Visualization
To visualize the clusters, Principal Component Analysis (PCA) was applied to
reduce the data to two dimensions. A scatter plot was created to show the
distribution of clusters based on the first two principal components.
6. Results & Insights
6.1 Cluster Characteristics
The clusters identified by DBSCAN reveal distinct customer groups. Some
customers are highly loyal (frequent reorders and higher average cart size),
while others make less frequent purchases but tend to order larger volumes
or unique products.
• Cluster 0: Customers who order regularly with a moderate cart size
and frequent reorders.
• Cluster 1: Customers who order less frequently, often placing large
orders in terms of unique product variety.
• Cluster 2: Customers who place orders occasionally but tend to reorder
products frequently.
• Cluster 3: Customers with sporadic ordering behavior and lower variety
in product choice.
6.2 Business Insights
The insights drawn from the clustering can help supermarket businesses tailor
their strategies:
• Frequent Reorderers (Cluster 2) should be targeted with loyalty
programs or subscription models to enhance retention.
• High Variety Shoppers (Cluster 1) could be presented with
personalized promotions based on product categories they tend to
explore.
• Occasional Shoppers (Cluster 3) might benefit from targeted
discounts or offers that encourage repeat purchases.
By understanding these segments, supermarkets can better manage
inventory, create targeted marketing campaigns, and optimize product
placements to meet the needs of each group.
7. Conclusion
This project successfully demonstrated the use of unsupervised learning
(DBSCAN clustering) to segment customers based on their purchase behavior.
The resulting clusters provide meaningful insights into customer loyalty,
product preferences, and shopping frequency. The use of clustering models
like DBSCAN helped identify distinct patterns that would be difficult to capture
manually.
Despite the promising results, further optimization of clustering parameters
(like eps and min_samples) and the inclusion of additional features (e.g.,
seasonal trends, promotions) could improve the segmentation accuracy.
