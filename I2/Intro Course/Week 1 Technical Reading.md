# Linear Regression
- refer to Coursera notes

# Logistic Regression
Cost function - log-likelihood loss function
- measures how well model's predictive probabilities match class labels
Multiclass classification - one-vs-res (OvR). Training multiple logistic regression models, with one responsible for whether an input belongs to one class or another. The model that outputs the highest probability for belonging to that class is used to decide the final label.

# K-Means Clustering: Unsupervised Learning

With unsupervised data, the goal is to find structure/groups in the data. For K-clustering, this means finding K groups that are all close to one another.
**How it works**
- iteratively assigns data points to clusters and then calculates a centroid.
- distances to centroids are minimized, making points in a cluster more similar to each other than points in other clusters
Step 1 - Initialization: randomly selects k initial cluster centroids from the dataset, acts as starting points.
Step 2 - Assignment: Each point is assigned to closest centroid based on distance (ie. Euclidean), forming k clusters
Step 3 - Update: once points are assigned to clusters, centroids are recalculated. New centroid is mean of all data points in cluster
Step 4 - Repeat: 2 and 3 are repeated until centroids no longer move significantly, or the cluster assignments don't change. CONVERGENCE!

## Within-Cluster Distance
We want to minimize the within-cluster distance, which is measured through the mean squared error. This ensures that all data points in a cluster are closely clumped together.

## Choosing K
Critical to determine value of *k*, or how many clusters there will be. Not known in advance, so can use the **elbow method**. With the **elbow method**, final SSEs are plotted vs. various *k* values, and the point where *k* provides diminishing returns is where increasing *k* is no longer helpful. Can also use **silhouette score**, which is a measure of how similar a data point is to its cluster vs. other clusters. Higher silhouette score indicates better-defined clusters. (?)

## Limitations of K-Means Clustering
- Sensitive to outliers, which may skew the centroids disproportionately
- Have to know the value of k to start with
- Sensitive to initialization - if you start with the wrong centroids, very possible to take long to train/get stuck in a local minima - K-Means++ can help with preventing this

# K-Means vs K-Medians Clustering
Instead of using mean as the centroid, centroid is determined to be the median. Also uses absolute distance (Manhattan distance) from centroid to measure closeness instead of squared difference.
- more robust and stable in the presence of outliers
- used when hella outliers
- used when the absolute difference is more meaningful than mean squared distance
- when data is not normally distributed (?)
- a bit less computationally efficient

## Bias-Variance Tradeoff
relates to over and underfitting!
bias - how well the model captures the true underlying curve - higher bias is bad!
variance - how much your model would change if you removed a few data points - should not completely refit, swerving to go through data points! This is called **robustness** of model.

We want to **minimize both**.
![[Screenshot 2024-10-16 at 3.45.46 PM.png]]

## Convex
With a convex model, reaching a minimum means you found the most optimal weights! With a non-convex model, there can be many local minima and even saddle points - reaching a low point != global minimum. 

