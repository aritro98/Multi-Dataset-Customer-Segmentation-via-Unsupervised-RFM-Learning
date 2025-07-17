# Multi-Dataset Customer Segmentation via Unsupervised RFM Learning

In modern digital ecosystems, customer data originates from diverse channels such as web analytics, transactional logs, and e-commerce platforms. However, these datasets often exist in isolation, making it challenging for organizations to derive unified insights. This project addresses that gap by presenting a scalable, end-to-end unsupervised learning pipeline that standardizes core behavioral metrics (Recency, Frequency, Monetary) across multiple sources, enabling consistent, actionable customer segmentation.

## Table of Contents
1. [Overview](#overview)
2. [Dataset Description](#dataset-description)
3. [Project Workflow](#project-workflow)
4. [Technologies Used](#technologies-used)
5. [Key Features](#key-features)
6. [Installation and Setup](#installation-and-setup)
7. [Usage](#usage)
8. [Results](#results)
9. [Future Scope](#future-scope)

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

## Key Features
* **RFM Feature Engineering**: Computes Recency, Frequency, and Monetary metrics per user/customer.
* **Dimensionality Reduction**: Visualizes data using PCA (2D/3D) and t-SNE embeddings.
* **Clustering Algorithms**: K-Means, Hierarchical (Ward), DBSCAN, MeanShift, Gaussian Mixture Models, and BIRCH each are tuned to four clusters.
* **Automated Tuning**: Inline search routines determine optimal bandwidth for MeanShift and ε for DBSCAN.
* **Multi-Metric Evaluation**: Compares Silhouette Score, Davies–Bouldin Index, Calinski–Harabasz Index, and WCSS to choose the best algorithm via aggregate ranking.
* **Cluster Profiling**: Merges cluster labels back to original transactions and compute segment profiles on RFM metrics.

## Installation and Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/aritro98/Multi-Dataset-Customer-Segmentation-via-Unsupervised-RFM-Learning.git
   cd Multi-Dataset-Customer-Segmentation-via-Unsupervised-RFM-Learning
   ```
2. Create and activate a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Linux/mac OS
   venv\Scripts\activate     # On Windows
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage
1. Run all the notebooks under the `notebooks` directory.
2. View results:
   * Interactive and static plots for PCA, t-SNE, elbow curves, and cluster visualizations.
   * Printed evaluation metrics and chosen best algorithm.
   * Segment profiles with RFM

## Results
After running the clustering pipeline on each dataset, we will obtain:
- **Dimensionality Reduction Visuals**:  
  - **PCA Projections** (2D and 3D) illustrating how customers group in principal‐component space.  
  - **t-SNE Embeddings** showing nonlinear neighborhood structure and validating cluster separability.
- **Clustering Evaluation**:  
  - A **summary table** of Silhouette Score, Davies–Bouldin Index, Calinski–Harabasz Index, and WCSS for all six algorithms.  
  - A **log‑scale bar chart** comparing these metrics side‑by‑side to highlight trade‑offs in cluster cohesion, separation, and compactness.
- **Selected Algorithm**: The algorithm with the best **aggregate rank** is automatically chosen and highlighted in the console output.
- **Cluster Visualizations**: 2D scatter plots for each method with centroids marked, enabling visual inspection of cluster shapes.
- **Final Cluster Profiles**:
  - Tables summarizing each segment’s average Recency, Frequency, Monetary values.
  - Ability to merge cluster labels back into the original data for downstream analysis or export.

## Future Scope
- **System Integration**:
  - Integrate segmentation model with CRM and marketing platforms.
  - Set up automated data pipelines for continuous segmentation updates.
- **Dashboard and Reporting**:
  - Develop interactive dashboards for monitoring segmentation results.
  - Create automated reports for stakeholders.
- **Personalization and Strategy Implementation**:
  - Design personalized marketing strategies based on customer segments.
  - Implement targeted campaigns and promotions.
  - Track the performance of these strategies.
- **Monitoring and Refinement**:
  - Continuously monitor the performance of the segmentation model.
  - Collect feedback and adjust the model and strategies accordingly.
- **Real‑Time Segmentation**: Integrate streaming data pipelines (e.g., Kafka, Airflow) to update RFM features and re‑segment customers continuously.
- **Automated Cluster‑Count Selection**: Implement methods like the Gap Statistic or Bayesian nonparametrics to determine the optimal number of clusters per dataset dynamically.
- **A/B Testing & Campaign Tracking**: Embed segmentation outputs into marketing workflows to run targeted experiments and measure lift in engagement and revenue.