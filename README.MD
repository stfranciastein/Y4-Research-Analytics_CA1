# CA1 – Data Analytics for Business
**DL836 Y4 – Research & Analytics** · Scenario: **Marketing Director**

This repository has my mode for task 1 and 2. The following tables below are AI generated.

## Repository structure

```
CA1_Data_Analytics/
├── data/                                   # Allocated datasets (unchanged originals)
│   ├── Retail_stores.csv                   # Task 1
│   ├── Customers_list.csv                  # Task 2
│   ├── Products_list.csv                   # Task 2
│   └── Transactions_list.csv               # Task 2
├── notebooks/
│   ├── Task1_Retail_Performance_Analytics.ipynb   ← TASK 1
│   └── Task2_Recommendation_System.ipynb          ← TASK 2
├── outputs/
│   ├── figures/                            # All charts (t1_* = Task 1, t2_* = Task 2)
│   └── tables/                             # Key result tables exported as CSV
├── requirements.txt
└── README.md
```

## Task 1 – Retail Performance Analytics
`notebooks/Task1_Retail_Performance_Analytics.ipynb`

| Section | Contents |
|---|---|
| Data preparation & quality | Missing values (~7% in 4 columns, imputed by StoreType × Region median), 100 duplicate rows removed, IQR outlier investigation, 44 implausible MarketingSpend values re-coded, StoreID consistency issue flagged |
| Feature engineering | 7 features: TotalTraffic, OnlineShare, MarketingPerVisitor, SalesPerStaffHour, MarketingROI*, RevenuePerVisitor*, spend/discount/competitor bands (*EDA only – leakage) |
| EDA | 6 GroupBy analyses (region, season, store type, store, marketing band, discount/competitor), Top 5 stores & locations |
| Pivot tables & correlation | 3 pivot tables + correlation heatmap |
| Predictive models | Linear Regression, Decision Tree, Random Forest, Gradient Boosting (80/20 split + 5-fold CV; MAE, RMSE, R²) + K-Means store segmentation |
| Feature importance | Random Forest + permutation importance, diminishing-returns analysis, marketing budget what-if scenarios |

## Task 2 – Recommendation System
`notebooks/Task2_Recommendation_System.ipynb`

| Section | Contents |
|---|---|
| Data preparation & integration | Category case fix, rating imputation, 386 duplicate transactions removed, Spend/PopularityScore validity checks, 3-way merge, 1000 × 200 interaction matrix |
| Customer analytics | Top 10 by spend, Top 10 by frequency, Pareto analysis, RFM segmentation |
| Product analytics | Top 10 products, revenue by category and brand |
| GroupBy & Pivot | 6 GroupBys (category, brand, loyalty, age, region, tenure), 3 pivot tables |
| Recommenders | Popularity-based, Item-based Collaborative Filtering, Content-based, Hybrid (CF + Popularity) |
| Evaluation | Temporal hold-out test; Precision@K, Recall@K, Hit Rate, Coverage vs random benchmark |
| Examples | Recommendations for 5 example customers across different segments |

## How to run

```bash
pip install -r requirements.txt
jupyter notebook
```
Open each notebook from the `notebooks/` folder and choose **Run All**. Paths are relative (`../data/`), so the notebooks must be run from inside `notebooks/`. Every random process uses `random_state=42`, so results are reproducible. Tested with pandas 2.2 and 3.0.

## Use of AI tools
As permitted by the brief, AI assistance was used for code development in Tasks 1 and 2. Details are recorded in the AI Process Log submitted with the Task 3 & 4 report.
