# Customer Segmentation with K-Means and DBSCAN

**Project Overview**
This project performs customer segmentation using transactional data. The goal is to group customers based on purchase behavior and analyze K-Means vs DBSCAN clustering techniques, & understand which is one to use and when?   

**Key objectives:**
- Understand customer behavior using RFM (Recency, Frequency, Monetary) metrics.
- Segment customers into actionable groups.
- Compare K-Means and DBSCAN clustering results.
- Identify outliers and VIP customers.

---

## Dataset
The dataset contains retail transactional data with columns:

| Column      | Description |
|------------|-------------|
| InvoiceNo  | Invoice number for each transaction |
| StockCode  | Product code |
| Description| Product description |
| Quantity   | Number of items purchased |
| InvoiceDate| Date and time of transaction |
| UnitPrice  | Price per item |
| CustomerID | Unique ID for each customer |
| Country    | Customer's country |

Example snapshot:

| InvoiceNo | StockCode | Description | Quantity | InvoiceDate         | UnitPrice | CustomerID | Country       |
|-----------|-----------|-------------|---------|-------------------|----------|------------|---------------|
| 536365    | 85123A    | WHITE HANGING HEART T-LIGHT HOLDER | 6 | 2010-12-01 08:26 | 2.55 | 17850 | United Kingdom |

---

## Environment Setup
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans, DBSCAN
from sklearn.metrics import silhouette_score
from warnings import filterwarnings
filterwarnings('ignore')
```
## Key Takeaways
- K-Means segments customers for targeted marketing campaigns.
- DBSCAN detects anomalies and extreme customers.
- Using both together ensures meaningful segmentation and outlier detection.
- RFM analysis provides actionable insights for retention and engagement strategies.

## Next Steps:
- If Goal is customer segementation for marketing or strategy -> trust K-Means even if Silhouette score
- If Goal is to detect anomalies (VIP, Fruad, Unusual buyers) -> DBSCAN is more appropriate and higher Silhouette just refelects DBSCAN chose not to cluster


