# Customer Segmentation Project

Segments customers into actionable groups based on behavioral and demographic data using **K-Means clustering** (scikit-learn), with full visualization and a written business insights report.

## What This Project Does

1. **Loads customer data** — demographics (age, income) + behavior (spending score, purchase frequency, recency, average order value)
2. **Preprocesses** — standardizes features so no single variable dominates the clustering
3. **Finds the optimal number of segments** — using the Elbow Method and Silhouette Score
4. **Clusters customers** — K-Means with k=4
5. **Visualizes segments** — PCA 2D scatter plot + characteristic heatmap
6. **Auto-labels segments** — translates cluster math into business language (e.g. "At-Risk", "Loyal Premium")
7. **Generates an insights report** — segment profiles + recommended marketing actions

## Tech Stack

| Tool | Purpose |
|---|---|
| Python 3 | Core language |
| pandas | Data handling |
| scikit-learn | KMeans clustering, PCA, StandardScaler, silhouette score |
| matplotlib | Visualizations |

## How to Run

```bash
pip install pandas scikit-learn matplotlib
python segmentation.py
```

All outputs are saved to `outputs/`.

## Output Files

| File | Description |
|---|---|
| `customers_segmented.csv` | Original data + assigned segment for every customer |
| `segment_profiles.csv` | Average feature values + labels per segment |
| `01_elbow_silhouette.png` | Charts used to choose k |
| `02_pca_segments.png` | 2D visualization of clusters |
| `03_segment_heatmap.png` | Heatmap comparing segment traits |
| `insights_report.md` | Written summary + recommended actions per segment |

## Using Your Own Data

Replace the synthetic data block in `segmentation.py` with:

```python
df = pd.read_csv("customers.csv")
```

Required columns: `age`, `annual_income`, `spending_score`, `purchase_frequency`, `recency_days`, `avg_order_value` (rename/add features as needed — just update the `features` list).

## Discovered Segments (Example Run)

| Segment | Label | Size | Key Traits |
|---|---|---|---|
| 0 | Loyal Premium Customers | 25% | High frequency, high spend, low recency — core revenue base |
| 1 | At-Risk / Churn-Prone | 25% | Long time since last purchase, low frequency |
| 2 | Affluent Occasional Shoppers | 25% | High income, high order value, low frequency |
| 3 | Young High-Value Spenders | 25% | Younger, high spending score, frequent buyers |

## Power BI Alternative

`customers_segmented.csv` can be loaded directly into Power BI:
1. Get Data → CSV → select `customers_segmented.csv`
2. Build a scatter chart (PC1 vs PC2, colored by `segment`)
3. Add slicers for `segment`, `age`, `annual_income`
4. Use a matrix/table visual for `segment_profiles.csv` to show averages per segment

## Learning Outcomes

- Unsupervised learning with K-Means
- Feature scaling and dimensionality reduction (PCA)
- Choosing k via elbow method and silhouette score
- Translating clusters into business personas
- Visual storytelling for stakeholder reports

## License

MIT — free to use, modify, and distribute.
# customer-segmentation
