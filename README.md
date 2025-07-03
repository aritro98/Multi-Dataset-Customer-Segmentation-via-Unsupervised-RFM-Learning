# Multi-Dataset Customer Segmentation via Unsupervised RFM Learning

## Overview
This repository provides a unified, end-to-end pipeline for customer segmentation across multiple data sources (web analytics, transaction logs, and online retail records). By standardizing Recency–Frequency–Monetary (RFM) features and applying six unsupervised clustering algorithms with automated parameter tuning, the project delivers interpretable, actionable customer cohorts.

## Dataset Description
The datasets used in this project include:
1. Online Retail II Dataset: This dataset contains detailed transactional records from an online retailer spanning 2009–2011. It can be used to perform customer segmentation, basket analysis, and lifetime value modelling.

Key attributes include:
* **Invoice**: Unique invoice number for each transaction
* **StockCode**: Identifier for each product
* **Description**: Text description of the product
* **Quantity**: Number of units purchased
* **InvoiceDate**: Date and time of the transaction
* **Price**: Unit price of the item
* **Customer ID**: Anonymized identifier for each customer
* **Country**: Customer’s country of residence
2)	Transaction Dataset: This dataset captures over one million purchase events from an e-commerce platform between mid-2018 and early 2019. It is ideal for RFM analysis, cross-border buying behaviour, and time-series studies of purchase patterns. 
Key fields include:
•	UserId: Unique customer identifier
•	TransactionId: Unique transaction reference
•	TransactionTime: Timestamp of purchase (IST)
•	ItemCode: Code for the purchased item
•	ItemDescription: Text description of the item
•	NumberOfItemsPurchased: Quantity of items in the transaction
•	CostPerItem: Price paid per unit
•	Country: Country from which the purchase was made
3)	Web Analytics Dataset: This monthly time-series dataset (Sep 2019–Aug 2020) provides channel-level website performance metrics for analysing user acquisition, engagement, and revenue. It supports understanding the impact of marketing channels on transactions and monetization. 
Key columns include:
•	Source / Medium: Traffic channel (e.g., “google/organic”)
•	Year, Month of the Year: Date of the observation
•	Users, New Users: Total and first-time visitors
•	Sessions: Number of visits
•	Bounce Rate: Percentage of single-page sessions
•	Pageviews: Total pages viewed
•	Avg. Session Duration: Mean length of a session
•	Conversion Rate (%): Percentage of sessions resulting in a transaction
•	Transactions, Revenue, Quantity Sold: E-commerce performance metrics

## Key Features
* **RFM Feature Engineering**: Computes Recency, Frequency, and Monetary metrics per user/customer.
* **Dimensionality Reduction**: Visualizes data using PCA (2D/3D) and t-SNE embeddings.
* **Clustering Algorithms**: K-Means, Hierarchical (Ward), DBSCAN, MeanShift, Gaussian Mixture Models, and BIRCH each are tuned to four clusters.
* **Automated Tuning**: Inline search routines determine optimal bandwidth for MeanShift and ε for DBSCAN.
* **Multi-Metric Evaluation**: Compares Silhouette Score, Davies–Bouldin Index, Calinski–Harabasz Index, and WCSS to choose the best algorithm via aggregate ranking.
* **Cluster Profiling**: Merges cluster labels back to original transactions and compute segment profiles on RFM metrics.