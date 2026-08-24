# Customer Segmentation using RFM Analysis & K-Means Clustering

An end-to-end customer segmentation project that identifies distinct customer groups from transactional data using RFM (Recency, Frequency, Monetary) feature engineering and K-Means clustering, then visualizes actionable personas in an interactive Power BI dashboard.

## Problem Statement

Businesses often treat all customers the same, wasting marketing spend on low-value segments while under-investing in retaining their most valuable ones. This project segments customers into behavior-based groups so that marketing and retention strategy can be targeted rather than generic.

## Dataset

Transactional e-commerce data with columns: `InvoiceNo, CustomerID, InvoiceDate, Product, Quantity, UnitPrice`. ~500 customers, ~4,700 invoices, ~11,700 line items.

## Methodology

1. **Data Cleaning** — removed cancelled/negative-quantity transactions, null CustomerIDs, and duplicates.
2. **Feature Engineering (RFM)** — calculated Recency (days since last purchase), Frequency (unique orders), and Monetary (total spend) per customer.
3. **Transformation** — log-transformed RFM values to correct right-skew, then standardized with `StandardScaler`.
4. **Cluster Selection** — tested K=2 through K=9 using the Elbow Method and Silhouette Score; both methods converged clearly on **K=4**.
5. **Clustering** — fit K-Means (K=4) on the scaled features and assigned each customer to a segment.
6. **Visualization** — built an interactive Power BI dashboard (scatter plot, heatmap matrix, radar chart, KPI cards, persona slicer).

## Customer Segments (Personas)

| Persona | Avg. Recency (days) | Avg. Frequency | Avg. Monetary | Customers |
|---|---|---|---|---|
| **High-Value Loyalists** | 16.7 | 22.1 | ₹27,860.6 | 87 |
| **Steady Regulars** | 26.9 | 12.8 | ₹3,601.9 | 129 |
| **At-Risk / Churned** | 285.8 | 6.0 | ₹3,258.2 | 141 |
| **Low-Engagement / New** | 65.2 | 1.7 | ₹775.6 | 143 |

- **High-Value Loyalists** buy often, spend the most, and purchased recently — the top retention priority. A VIP program or early-access perks would protect this segment.
- **Steady Regulars** are recent and moderately frequent — a natural upsell target to move them toward Loyalist status.
- **At-Risk / Churned** customers used to spend meaningfully but haven't ordered in ~9-10 months — the clearest win-back campaign target.
- **Low-Engagement / New** customers have minimal order history and spend — likely one-time buyers or recent signups needing an onboarding push.

## Dashboard

![Dashboard Overview](<img width="1158" height="559" alt="dashboard-overview" src="https://github.com/user-attachments/assets/5991ed1f-0494-47eb-bbf2-65b0a3b287e1" />
)

**Segment Scatter Plot** — Recency vs. Monetary, colored by persona:
![Scatter Plot](https://github.com/Vikramcntrivikram/Customer-Segmentation-Project/blob/main/scatter-plot.png)

**Segment Heatmap** — average RFM values per persona:
![Heatmap](https://github.com/Vikramcntrivikram/Customer-Segmentation-Project/blob/main/heatmap.png
)

**Radar Chart** — normalized RFM shape comparison across personas:
![Radar Chart](https://github.com/Vikramcntrivikram/Customer-Segmentation-Project/blob/main/radar-chart.png)

## Business Insight

High-Value Loyalists make up only ~17% of the customer base but account for a disproportionately large share of total revenue — reinforcing the case for prioritizing retention spend on this segment over broad, undifferentiated marketing.

## Tools Used

- **Python**: pandas, numpy, scikit-learn, matplotlib
- **Power BI Desktop**: data modeling, DAX, interactive visuals

## Files in this Repo

- `segmentation.ipynb` — full data cleaning, RFM engineering, and clustering notebook
- `customer_segments.csv` — final labeled dataset (RFM + cluster + persona per customer)
- `segmentation_dashboard.pbix` — Power BI dashboard file
- `screenshots/` — dashboard visuals
