# Credit Card Fraud Analysis (SQL + Python )

## What problem did I solve?

A bank wanted to understand fraud patterns across its credit card transactions in order to identify high-risk transaction types and reduce fraud exposure. Using a dataset of 20,000 transactions, I analyzed which merchant categories, authentication methods, channels, and transaction contexts (foreign vs. domestic, VPN use, time of day) were associated with higher fraud rates, then turned those patterns into concrete recommendations.

## What tools and skills did I use?

- **Python** (pandas) for data loading and manipulation
- **SQL** (via SQLite, queried through `sqlite3` + `pandas.read_sql`) for aggregation and grouped analysis — `COUNT`, `SUM`, `GROUP BY`, `ORDER BY`, and rate calculations
- **Matplotlib / Seaborn** for exploratory visualizations (bar charts, line chart)
- Core skills: exploratory data analysis (EDA), SQL query writing, data visualization, and translating analytical findings into business recommendations

## How did I approach it?

1. **Loaded the data** — 20,000 credit card transactions with 26 features, including transaction amount, merchant category, authentication method, device/channel, and fraud indicators (VPN use, IP/country mismatch, velocity score, etc.), into a pandas DataFrame and an in-memory SQLite database.
2. **Established a baseline** — calculated the overall transaction count and fraud rate.
3. **Broke fraud down by dimension** — wrote grouped SQL queries to compute transaction volume, fraud case count, and fraud rate by merchant category, authentication method, channel, foreign vs. domestic transaction, time of day, VPN usage, and IP/country mismatch.
4. **Visualized each breakdown** — used seaborn bar and line charts to make the highest-risk categories easy to spot.
5. **Synthesized findings into recommendations** — summarized the key drivers of fraud and proposed operational changes to reduce it.

## Where is the code?

The full analysis is in [https://github.com/diarrawade939-svg/Kaggle-projects/blob/main/credit-card-fraud-analysis-using-sql-and-tableau.ipynb`] in this repository.

Dataset source: [Credit Card Fraud Detection 2026 (Kaggle)](https://www.kaggle.com/datasets/uditjain13/credit-card-fraud-detection-2026)

## What was the outcome?

Out of 20,000 transactions, **339 were fraudulent — an overall fraud rate of 1.7%**. The analysis surfaced several clear risk drivers:

- **Merchant category**: Crypto Exchange (4.99%), Gift Cards (4.38%), and Gaming (3.67%) had the highest fraud rates, well above categories like Online Retail (0.94%) and Travel (1.13%).
- **Authentication method**: Transactions with **no authentication** had a fraud rate of 4.44%, nearly 6x higher than Biometric-authenticated transactions (0.78%).
- **Channel**: Online transactions had the highest fraud rate (1.98%); Contactless had the lowest (1.41%).
- **Foreign transactions**: Fraud rate was **5.89%** for foreign transactions vs. **1.42%** for domestic — over 4x higher.
- **VPN use and IP/country mismatch**: Both were disproportionately represented among fraud cases relative to their share of total transactions.

**Recommendations:**

- Require stronger authentication (e.g., biometric or 3D Secure) for high-risk merchant categories like crypto exchanges and gift cards.
- Add enhanced monitoring and step-up verification for foreign transactions.
- Flag VPN usage and IP/country mismatches for additional review.
- Increase fraud detection thresholds and scrutiny for high-risk channels (Online).
