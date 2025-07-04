# Multi-Dataset Customer Segmentation via Unsupervised RFM Learning

In modern digital ecosystems, customer data originates from diverse channels such as web analytics, transactional logs, and e-commerce platforms. However, these datasets often exist in isolation, making it challenging for organizations to derive unified insights. This project addresses that gap by presenting a scalable, end-to-end unsupervised learning pipeline that standardizes core behavioral metrics (Recency, Frequency, Monetary) across multiple sources, enabling consistent, actionable customer segmentation.

## Overview
This repository provides a unified, end-to-end pipeline for customer segmentation across multiple data sources (web analytics, transaction logs, and online retail records). By standardizing Recency–Frequency–Monetary (RFM) features and applying six unsupervised clustering algorithms with automated parameter tuning, the project delivers interpretable, actionable customer cohorts.

## Dataset Description
The datasets used in this project include:
1. **Online Retail II Dataset**  
   This dataset contains detailed transactional records from an online retailer spanning 2009–2011. It can be used to perform customer segmentation, basket analysis, and lifetime value modeling.  
   **Key attributes include:**  
   - **Invoice**: Unique invoice number for each transaction  
   - **StockCode**: Identifier for each product  
   - **Description**: Text description of the product  
   - **Quantity**: Number of units purchased  
   - **InvoiceDate**: Date and time of the transaction  
   - **Price**: Unit price of the item  
   - **Customer ID**: Anonymized identifier for each customer  
   - **Country**: Customer’s country of residence  

2. **Transaction Dataset**  
   This dataset captures over one million purchase events from an e‑commerce platform between mid‑2018 and early 2019. It is ideal for RFM analysis, cross‑border buying behaviour, and time‑series studies of purchase patterns.  
   **Key fields include:**  
   - **UserId**: Unique customer identifier  
   - **TransactionId**: Unique transaction reference  
   - **TransactionTime**: Timestamp of purchase (IST)  
   - **ItemCode**: Code for the purchased item  
   - **ItemDescription**: Text description of the item  
   - **NumberOfItemsPurchased**: Quantity of items in the transaction  
   - **CostPerItem**: Price paid per unit  
   - **Country**: Country from which the purchase was made  

3. **Web Analytics Dataset**  
   This monthly time‑series dataset (Sep 2019–Aug 2020) provides channel‑level website performance metrics for analysing user acquisition, engagement, and revenue. It supports understanding the impact of marketing channels on transactions and monetization.  
   **Key columns include:**  
   - **Source / Medium**: Traffic channel (e.g., “google/organic”)  
   - **Year, Month of the Year**: Date of the observation  
   - **Users, New Users**: Total and first‑time visitors  
   - **Sessions**: Number of visits  
   - **Bounce Rate**: Percentage of single‑page sessions  
   - **Pageviews**: Total pages viewed  
   - **Avg. Session Duration**: Mean length of a session  
   - **Conversion Rate (%)**: Percentage of sessions resulting in a transaction  
   - **Transactions, Revenue, Quantity Sold**: E‑commerce performance metrics  

These datasets can be found in **Kaggle**:
1. [Online Retail II Data Set from ML Repository](https://www.kaggle.com/datasets/mathchi/online-retail-ii-data-set-from-ml-repository)
2. [Transaction Data](https://www.kaggle.com/datasets/vipin20/transaction-data)
3. [Web Analytics Dataset](https://www.kaggle.com/datasets/afranur/web-analytics-dataset)

## Project Workflow
- **Data Ingestion & Cleaning**: Load raw datasets (web analytics, transactions, retail) and handle missing values or type conversions.
- **RFM Feature Engineering**: Compute `Recency` (days since last event), `Frequency` (count of sessions/invoices), and `Monetary` (total spend) per user/customer.
- **Feature Scaling**: Apply Z‑score standardization to ensure comparability across RFM features.
- **Dimensionality Reduction & Visualization**:
    - Use Principal Component Analysis (PCA) for 2D/3D projections.
    - Apply t‑SNE for nonlinear embeddings to inspect cluster structure.
- **Automated Clustering Parameter Tuning**: Inline search for optimal bandwidth in `MeanShift` and ε in `DBSCAN` to enforce four clusters.
- **Clustering Algorithm Execution**: Run six methods (`K‑Means`, `Hierarchical`‑Ward, `DBSCAN`, `MeanShift`, `GMM`, `BIRCH`) on the scaled RFM data.
- **Evaluation & Model Selection**:
    - Compute `Silhouette Score`, `Davies–Bouldin Index`, `Calinski–Harabasz Index`, and `WCSS`.
    - Plot metrics (including log‑scale bar chart) and select the best algorithm via rank‑sum aggregation.
- **Cluster Assignment & Profiling**:
   - Assign final labels back to both the user‑level RFM table and original transaction records.
   - Generate segment profiles on RFM metrics.

## Key Features
* **RFM Feature Engineering**: Computes Recency, Frequency, and Monetary metrics per user/customer.
* **Dimensionality Reduction**: Visualizes data using PCA (2D/3D) and t-SNE embeddings.
* **Clustering Algorithms**: K-Means, Hierarchical (Ward), DBSCAN, MeanShift, Gaussian Mixture Models, and BIRCH each are tuned to four clusters.
* **Automated Tuning**: Inline search routines determine optimal bandwidth for MeanShift and ε for DBSCAN.
* **Multi-Metric Evaluation**: Compares Silhouette Score, Davies–Bouldin Index, Calinski–Harabasz Index, and WCSS to choose the best algorithm via aggregate ranking.
* **Cluster Profiling**: Merges cluster labels back to original transactions and compute segment profiles on RFM metrics.

## Technologies Used
- **Python**: Core scripting language
- **Jupyter Notebook**: Interactive development environment
- **pandas**: Data loading and manipulation
- **NumPy**: Numerical computing
- **scikit-learn**: Clustering algorithms, PCA, t‑SNE, and evaluation metrics
- **Matplotlib**: Plotting library for visualizations
- **seaborn**: Statistical data visualization
- **SQLAlchemy**: Database toolkit and ORM for Python
- **PyMySQL**: MySQL database connector
- **openpyxl**: Read/write Excel xlsx/xlsm files