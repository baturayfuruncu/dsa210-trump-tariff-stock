# Stock Market Reactions to Trump’s “Tariff” Mentions

## Motivation
Political statements from influential figures like Donald Trump often trigger short-term volatility in financial markets. This project explores how mentions of *“tariffs”* by U.S. President Donald Trump correlate with fluctuations in U.S. stock market indices, aiming to understand the impact of political rhetoric on investor sentiment and market behavior.

## Data Sources
- **Trump Tweets Dataset:** Historical tweets from @realDonaldTrump, publicly available via the [Trump Twitter Archive](https://www.thetrumparchive.com/) or [Kaggle datasets](https://www.kaggle.com/).
- **Stock Market Data:** Daily stock prices and indices (S&P 500, Dow Jones Industrial Average, NASDAQ) collected via the [Yahoo Finance API (`yfinance`)](https://pypi.org/project/yfinance/).
- **Optional Enrichment:**  
  - Trade policy–related news frequency (e.g., via News API or GDELT).
  - Sector indices (e.g., industrial/manufacturing stocks) to observe differential impact.

## Methodology and Planned Analysis
1. **Data Collection and Cleaning**
   - Extract all Trump tweets from 2016–2021 containing the keyword *“tariff”*.
   - Parse timestamps and align them with daily stock index values.
   - Handle missing trading days (weekends, holidays).

2. **Exploratory Data Analysis (EDA)**
   - Visualize tweet frequency over time.
   - Identify clusters of tariff-related tweet bursts.
   - Compare market performance before and after tweet dates.
   - Correlation between sentiment (positive/negative) and market change.

3. **Hypothesis Testing**
   - **H₀ (Null):** Trump’s tariff-related tweets have no significant effect on stock market returns.
   - **H₁ (Alternative):** Tariff-related tweets significantly affect stock market volatility or direction.

4. **Statistical and ML Methods (for final stage)**
   - Event-study analysis (market movement around tweet days).
   - Regression model predicting market return based on sentiment polarity and tweet volume.
   - Time-series analysis or volatility modeling (ARIMA/GARCH).

5. **Visualization**
   - Time-series plots of tweet activity vs. stock index movements.
   - Sentiment–return scatter plots.
   - Annotated charts for major tariff events.

## Expected Findings
- Short-term stock dips or volatility spikes following tariff-related tweets.
- Sector-specific sensitivity (e.g., manufacturing vs. tech).
- Sentiment polarity may predict return direction more strongly than frequency.

## Tools and Libraries
`pandas`, `numpy`, `matplotlib`, `seaborn`, `yfinance`, `TextBlob` or `VADER`, `scikit-learn`

## Limitations and Future Work
- Tweets’ time zones may not align perfectly with market hours.
- Difficult to isolate tariff mentions from concurrent political or economic factors.
- Future work: expand to compare Trump’s tweets with Biden’s trade-related statements for longitudinal analysis.

- ## - Progress Update — 

### Data Collection (Completed)
- Collected daily S&P 500 data from Yahoo Finance using the `yfinance` library.
- Loaded the Trump tweet archive (`realDonaldTrump_in_office.csv`), covering tweets during his first presidency (2017–2021).
- Filtered tweets to include only the official presidency window (Jan 20, 2017 – Jan 20, 2021).
- Extracted all tweets containing the keyword **"tariff"**.
- Identified that tariff-related tweets occurred on **21 trading days** during the presidency.

### Data Cleaning & Processing (Completed)
- Converted and standardized timestamp data.
- Normalized daily indices for clean alignment with financial data.
- Aggregated tariff-related tweet counts on a per-day basis.
- Mapped tariff-tweet days onto S&P 500 daily returns to build a unified dataset.

### Exploratory Data Analysis (Completed)
- Visualized tariff tweet activity over time.
- Plotted tweet counts versus daily S&P 500 returns.
- Compared return distributions for tweet vs non-tweet days.

### Hypothesis Testing (Completed)
**Research question:**  
*Do tariff-related tweets by Donald Trump coincide with significant changes in S&P 500 daily returns?*

**Method:**  
Two-sample t-test comparing:
- Returns on tariff-tweet days (21 days)
- Returns on non-tweet days (984 days)

**Results:**
- **t-statistic:** -0.542  
- **p-value:** ≈ 0.593  
- **Conclusion:** No statistically significant difference in average daily returns between tweet and non-tweet days.

This indicates that tariff-related tweets alone did not produce measurable impacts on *broad* S&P 500 daily returns during 2017–2021.

### Next Steps
- Consider testing market **volatility** instead of daily returns.
- Explore time windows around tweets (±1 day, intraday effects).
- Add clearer visualizations and prepare for the final report.


