# Day 2 — DBSCAN & Hierarchical Clustering

## Overview

Day 2 focuses on **DBSCAN** and **Hierarchical Clustering**, two unsupervised learning techniques used to discover natural groups and structures within data.

The main goal is to understand how these clustering algorithms work, how they differ from K-Means, how to identify clusters and noise points, and how to evaluate and interpret the resulting clusters.

The day covers **DBSCAN**, its `eps` and `min_samples` parameters, noise and outlier detection, **Hierarchical Clustering**, dendrograms, linkage methods, distance thresholds, and the **Silhouette Score** for evaluating clustering quality.

## Learning Objectives

By the end of this day, the main objectives were to:

* Understand the basic idea behind DBSCAN clustering.

* Understand the role of `eps` and `min_samples` in DBSCAN.

* Identify clusters and noise points using DBSCAN.

* Understand why DBSCAN can detect outliers as noise.

* Understand the limitations of K-Means and when alternative clustering algorithms are useful.

* Understand Hierarchical Clustering and how clusters are progressively formed.

* Understand the purpose of a dendrogram.

* Use a distance threshold to determine the number of hierarchical clusters.

* Evaluate clustering results using the Silhouette Score.

* Compare DBSCAN and Hierarchical Clustering based on their results.

## 1. DBSCAN Clustering

**DBSCAN** stands for **Density-Based Spatial Clustering of Applications with Noise**.

Unlike K-Means, DBSCAN does not require the number of clusters to be specified in advance.

Instead, it identifies clusters based on the **density of data points**.

DBSCAN groups together points that are located in dense regions and separates points that are located in less dense regions.

### Main Parameters

DBSCAN mainly depends on two parameters:

* `eps`: Defines the maximum distance between two points for them to be considered neighbors.

* `min_samples`: Defines the minimum number of neighboring points required to form a dense region.

These parameters have a direct effect on the number of clusters and noise points detected by the algorithm.

## 2. Core Points, Border Points, and Noise

DBSCAN classifies data points into three main categories:

### Core Points

A core point has at least `min_samples` points within the `eps` neighborhood.

These points form the dense regions of a cluster.

### Border Points

A border point does not have enough neighbors to be a core point itself, but it is located close enough to a core point to belong to its cluster.

### Noise Points

A noise point does not belong to any cluster because it is located in a region with insufficient density.

In Scikit-learn, DBSCAN represents noise points using the label:

```python
-1
```

Therefore, the number of noise points can be calculated by counting the points labeled `-1`.

## 3. DBSCAN Practical Application

DBSCAN was applied to the **Mall Customers dataset** using:

* Annual Income
* Spending Score

Before applying DBSCAN, the features were standardized using `StandardScaler`.

The workflow included:

* Loading the dataset.

* Selecting numerical features.

* Scaling the features.

* Applying DBSCAN.

* Counting the number of clusters.

* Counting the number of noise points.

* Visualizing the resulting clusters.

* Evaluating the clustering using the Silhouette Score.

The obtained result was:

* **Number of clusters:** 2
* **Number of noise points:** 8
* **Silhouette Score:** 0.3876

## 4. Hierarchical Clustering

**Hierarchical Clustering** is another unsupervised learning technique that creates a hierarchy of clusters.

Instead of directly assigning all data points to a fixed number of clusters, the algorithm progressively merges similar observations into larger groups.

The result can be represented using a **dendrogram**.

### Linkage

Linkage determines how the distance between clusters is calculated.

In the practical application, the **Ward linkage method** was used.

```python
Z = linkage(X_scaled, method="ward")
```

Ward's method attempts to minimize the increase in within-cluster variance when clusters are merged.

## 5. Dendrogram

A **dendrogram** is a tree-like visualization that shows how observations or clusters are progressively merged.

The vertical axis represents the **distance** at which clusters are merged.

A larger vertical distance indicates that the merged clusters are more different from each other.

A horizontal cut through the dendrogram can be used to determine the final number of clusters.

## 6. Choosing the Number of Hierarchical Clusters

After creating the linkage matrix and dendrogram, `fcluster()` was used to create the final cluster labels.

A distance threshold of `12` was used:

```python
hierarchical_labels = fcluster(
    Z,
    t=12,
    criterion="distance"
)
```

This resulted in:

**Number of hierarchical clusters: 3**

The Silhouette Score was then calculated to evaluate the quality of the clustering.

**Hierarchical Silhouette Score: 0.4610**

## 7. Comparing DBSCAN and Hierarchical Clustering

The two algorithms produced different clustering results:

| Method                  | Clusters | Noise Points | Silhouette Score |
| ----------------------- | -------: | -----------: | ---------------: |
| DBSCAN                  |        2 |            8 |           0.3876 |
| Hierarchical Clustering |        3 |            — |           0.4610 |

Based on the Silhouette Score, **Hierarchical Clustering produced better-separated clusters for this dataset**.

However, the Silhouette Score should not be the only factor considered. The choice of clustering algorithm also depends on the structure of the data and the purpose of the analysis.

## 8. DBSCAN vs. K-Means

DBSCAN and K-Means approach clustering differently.

| K-Means                                       | DBSCAN                                  |
| --------------------------------------------- | --------------------------------------- |
| Requires choosing `k`                         | Does not require the number of clusters |
| Distance-based                                | Density-based                           |
| Works well with relatively spherical clusters | Can detect irregularly shaped clusters  |
| Every point is assigned to a cluster          | Can identify noise points               |
| Sensitive to outliers                         | Can explicitly label outliers as noise  |

This makes DBSCAN useful when the dataset contains **noise or irregularly shaped clusters**.

## 9. Practical Application

During the hands-on practice, both DBSCAN and Hierarchical Clustering were applied to the **Mall Customers dataset**.

The workflow included:

* Loading and inspecting the dataset.

* Selecting Annual Income and Spending Score.

* Scaling the features using `StandardScaler`.

* Applying DBSCAN.

* Identifying clusters and noise points.

* Visualizing DBSCAN clusters.

* Creating a hierarchical clustering linkage matrix.

* Visualizing the dendrogram.

* Selecting a distance threshold.

* Creating hierarchical cluster labels.

* Calculating the Silhouette Score.

* Comparing the clustering results of DBSCAN and Hierarchical Clustering.

## Tools Used

* Python

* Pandas

* Scikit-learn

* SciPy

* Matplotlib

* Jupyter Notebook

* `DBSCAN`

* `StandardScaler`

* `silhouette_score`

* `linkage`

* `dendrogram`

* `fcluster`

## Key Takeaways

* DBSCAN is a **density-based clustering algorithm**.

* DBSCAN does not require the number of clusters to be specified beforehand.

* `eps` and `min_samples` strongly affect DBSCAN's results.

* DBSCAN can identify **noise and potential outliers** using the label `-1`.

* Hierarchical Clustering builds a hierarchy of clusters through progressive merging.

* A **dendrogram** helps visualize the hierarchical relationships between data points.

* A distance threshold can be used to determine the final number of hierarchical clusters.

* Feature scaling is important because both methods rely on distances between data points.

* The **Silhouette Score** can be used to evaluate and compare clustering quality.

* In this practical application, DBSCAN produced **2 clusters and 8 noise points**, while Hierarchical Clustering produced **3 clusters**.

* Hierarchical Clustering achieved a higher Silhouette Score (**0.4610**) than DBSCAN (**0.3876**) on this dataset.

* The best clustering method depends on the structure of the data, the presence of noise, and the goal of the analysis.
