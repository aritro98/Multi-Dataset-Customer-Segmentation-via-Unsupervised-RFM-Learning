# Multi-Dataset Customer Segmentation via Unsupervised RFM Learning

## Overview
This repository provides a unified, end-to-end pipeline for customer segmentation across multiple data sources (web analytics, transaction logs, and online retail records). By standardizing Recency–Frequency–Monetary (RFM) features and applying six unsupervised clustering algorithms with automated parameter tuning, the project delivers interpretable, actionable customer cohorts.

## Key Features
* **RFM Feature Engineering**: Computes Recency, Frequency, and Monetary metrics per user/customer.
* **Dimensionality Reduction**: Visualizes data using PCA (2D/3D) and t-SNE embeddings.
* **Clustering Algorithms**: K-Means, Hierarchical (Ward), DBSCAN, MeanShift, Gaussian Mixture Models, and BIRCH each are tuned to four clusters.
* **Automated Tuning**: Inline search routines determine optimal bandwidth for MeanShift and ε for DBSCAN.
* **Multi-Metric Evaluation**: Compares Silhouette Score, Davies–Bouldin Index, Calinski–Harabasz Index, and WCSS to choose the best algorithm via aggregate ranking.
* **Cluster Profiling**: Merges cluster labels back to original transactions and compute segment profiles on RFM metrics.