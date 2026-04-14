# 📈 Primetrade.ai - Data Science Intern Assignment

## 📌 Objective

This project analyzes the relationship between market sentiment
(Fear/Greed) and trader behavior/performance on the Hyperliquid
platform. The goal is to uncover behavioral patterns and propose
actionable trading strategies or risk management rules.

## 🛠️ Datasets & Preprocessing

1.  **Bitcoin Market Sentiment:** Daily classification of market
    sentiment (Fear, Extreme Fear, Greed, Extreme Greed).
2.  **Historical Trader Data (Hyperliquid):** Execution-level trading
    data including account, size, side, execution price, and closed PnL.

**Data Engineering Steps:** - Standardized timestamps and merged the two
datasets on a daily level. - Aggregated trader metrics per day (Daily
PnL, Total Trades, Win Rate). - **Leverage Proxy:** In the absence of
explicit leverage data, `Size USD` was utilized as a proxy to segment
traders into 'High Volume' (High Exposure) and 'Low Volume' groups.

## 🧠 Bonus Tasks Implemented

-   **Predictive Modeling:** Built a Random Forest Classifier to predict
    next-day profitability based on current execution metrics and
    sentiment.
-   **Behavioral Clustering:** Applied K-Means clustering to segment
    traders into distinct behavioral archetypes based on their
    historical performance and risk profiles.
-   **Interactive Dashboard:** Created a Streamlit application to
    visualize PnL distributions and win rates across different market
    sentiments dynamically.

## 📊 Key Findings & Insights

1.  **Sentiment Asymmetry & Risk:** During 'Extreme Fear' periods, the
    distribution of Daily PnL exhibits significant negative outliers.
    While the median PnL remains near zero, the probability of
    catastrophic drawdowns increases sharply.

2.  **Execution \> Macro Sentiment:** The predictive model (\~63%
    baseline accuracy) revealed that a trader's personal execution
    habits (`total_trades`, `daily_pnl`, `win_rate`) are far stronger
    predictors of their next-day profitability than macro market
    sentiment. The model showed a high recall (75%) for predicting
    winning days.

3.  **Behavioral Archetypes (K-Means):**

    -   **Cluster 0 (Trend Followers):** Low win rate but highly
        profitable due to strong risk management.
    -   **Cluster 1 (Whales):** Highest trade frequency and large profit
        potential but high volatility.
    -   **Cluster 2 (Consistent Snipers):** Highest win rate and lowest
        volatility with stable profits.

## 🚀 Actionable Strategy Recommendations

### Rule 1: Dynamic Risk Reduction (Extreme Fear)

**Trigger:** Market sentiment shifts to 'Extreme Fear'.\
**Action:** Automatically cap maximum allowable position sizing
(`Size USD`) by 20--30%, especially for high‑volume traders to reduce
large drawdowns.

### Rule 2: Capital Allocation Strategy

**Trigger:** General market conditions.\
**Action:** Allocate conservative capital to consistent traders (Cluster
2). Use high‑risk capital for whale traders (Cluster 1) mainly during
strong bullish sentiment periods.

## 💻 How to Run the Project

1.  Clone the repository
2.  Install dependencies

``` bash
pip install -r requirements.txt
```

3.  Place dataset files (`file_1.csv` and `file_2.csv`) in the project
    root directory.

4.  Run the notebook

``` bash
jupyter notebook Himesh_Primetrade_Analysis.ipynb
```

5.  Launch the Streamlit dashboard

``` bash
streamlit run app.py
```

------------------------------------------------------------------------

Prepared by **Himesh Raghuwanshi** for the Primetrade.ai Data Science
Internship Application.
