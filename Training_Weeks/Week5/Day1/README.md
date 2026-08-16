# Day 1 — Unsupervised Learning & K-Means

## Overview

Day 1 focuses on the fundamentals of **Unsupervised Learning** and **K-Means Clustering**.

The main goal is to understand how machine learning can discover hidden patterns and natural groups in data without using predefined labels.

The day covers the difference between supervised and unsupervised learning, how clustering works, the K-Means algorithm, methods for choosing the number of clusters, and the importance of feature scaling.

## Learning Objectives

By the end of this day, the main objectives were to:

* Understand unsupervised learning and how it differs from supervised learning.
* Understand the purpose of clustering.
* Apply the K-Means clustering algorithm.
* Understand how K-Means assigns data points to clusters.
* Choose an appropriate number of clusters using the Elbow Method.
* Validate candidate cluster numbers using the Silhouette Score.
* Understand why feature scaling is important before clustering.
* Interpret the resulting clusters and their centroids.

## 1. Supervised vs. Unsupervised Learning

In supervised learning, the data contains known labels or target values. The model learns to predict the target based on the input features.

In unsupervised learning, there are no predefined target labels. Instead, the goal is to discover hidden structures or patterns within the data.

### Main Difference

| Supervised Learning                  | Unsupervised Learning                                             |
| ------------------------------------ | ----------------------------------------------------------------- |
| Uses labeled data                    | Uses unlabeled data                                               |
| Predicts a known target              | Discovers hidden structure                                        |
| Examples: Classification, Regression | Examples: Clustering, Dimensionality Reduction, Anomaly Detection |

## 2. What is Clustering?

Clustering is an unsupervised learning technique that groups data points based on their similarity.

The goal is to make points within the same cluster more similar to each other while keeping different clusters as distinct as possible.

A practical example is **customer segmentation**, where customers can be grouped based on characteristics such as age, income, and spending behavior.

## 3. K-Means Clustering

K-Means is a clustering algorithm that divides data into a predefined number of clusters, represented by `k`.

The algorithm repeatedly performs two main operations:

1. Assign each data point to its nearest centroid.
2. Update each centroid to the mean position of the points assigned to it.

These steps are repeated until the centroids become stable.

### Centroids

A centroid represents the center of a cluster.

After the algorithm finishes, the position of each centroid summarizes the average characteristics of the data points belonging to that cluster.

## 4. Choosing the Number of Clusters

One of the main challenges in K-Means is choosing the appropriate value of `k`.

Two methods were studied to help make this decision:

### Elbow Method

The Elbow Method evaluates different values of `k` and calculates the **inertia** for each one.

Inertia represents the total within-cluster distance between data points and their corresponding centroids.

As the number of clusters increases, inertia decreases. The goal is to identify the point where the improvement starts to decrease significantly, creating an "elbow" in the plot.

### Silhouette Score

The Silhouette Score provides a quantitative way to evaluate how well-defined the clusters are.

The score ranges from `-1` to `1`.

A higher score generally indicates that data points are well matched to their own cluster and well separated from neighboring clusters.

The Silhouette Score can therefore be used to compare candidate values of `k` and support the choice made using the Elbow Method.

## 5. Feature Scaling

Feature scaling is an important preprocessing step before applying K-Means.

K-Means is a distance-based algorithm, so features with larger numerical ranges can have a greater influence on the clustering results.

`StandardScaler` is used to standardize the features so that they are placed on a comparable scale before clustering.

## 6. Practical Application

During the hands-on practice, K-Means clustering was applied to a numerical dataset.

The workflow included:

* Loading and inspecting the dataset.
* Selecting numerical features for clustering.
* Checking for missing values.
* Scaling the features using `StandardScaler`.
* Running K-Means for different values of `k`.
* Using the Elbow Method to identify candidate values.
* Comparing candidates using the Silhouette Score.
* Training the final K-Means model.
* Visualizing the resulting clusters.
* Interpreting the clusters and their centroids.

## Tools Used

* Python
* Pandas
* Scikit-learn
* Matplotlib
* Jupyter Notebook
* `KMeans`
* `StandardScaler`
* `silhouette_score`

## Key Takeaways

* Unsupervised learning works with data that does not have predefined labels.
* Clustering can reveal natural groups and hidden structures in data.
* K-Means assigns data points to clusters based on their distance from centroids.
* The number of clusters should be selected carefully rather than chosen arbitrarily.
* The Elbow Method provides a visual way to identify candidate values of `k`.
* The Silhouette Score provides a quantitative way to compare cluster quality.
* Feature scaling is essential for distance-based algorithms such as K-Means.
* Clustering results should be interpreted based on the characteristics of the resulting groups rather than relying only on the algorithm's output.