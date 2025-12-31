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

- ## - Progress Update - 

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

## Interpretation and Discussion

Although tariff-related tweets by Donald Trump attracted significant public and media attention during his first presidency, the results suggest that such tweets did not correspond to statistically significant changes in overall daily market returns. One possible explanation is that financial markets may have already anticipated changes in trade policy based on earlier announcements and economic information, which reduced the impact of individual tweets.

Additionally, the S&P 500 is a diverse index that aggregates the performance of many sectors, which may dilute sector-specific reactions to trade policy rhetoric. Some industries, such as manufacturing or technology, may react more strongly to tariff-related news, but these effects may not appear clearly in a broad market index.

Another important limitation is the relatively small number of tariff-tweet days (21 trading days), which reduces statistical power and makes it more difficult to detect subtle effects. 

Overall, these findings suggest that tariff-related Twitter activity alone was not sufficient to consistently influence broad U.S. stock market performance, highlighting the importance of considering market expectations, policy context, and data granularity in financial impact studies.

## Use of AI Tools

Portions of this project were completed with assistance from AI tools (ChatGPT). 
AI support was used for:
- debugging code,
- clarifying errors,
- verifying methodology,
- organizing steps, and
- refining explanations.

All coding, analysis, data collection, and final decisions were performed by me.

### Machine Learning Results and Interpretation

A linear regression model was trained to predict daily market volatility, measured as the absolute return of the S&P 500, using tariff-related tweet frequency and trading volume as input features. The model achieved an R² of approximately 0.35 on the test set, indicating moderate explanatory power, which is reasonable given the volatile nature of daily financial data.

The estimated coefficient for tariff-related tweet count was positive, suggesting that days with more tariff-related tweets are associated with higher predicted market volatility, even after controlling for overall market activity through trading volume. However, the magnitude of this effect is relatively small, indicating that tariff-related tweets alone are not a dominant factor for volatility.

Overall, these results support the idea that while tariff-related Twitter activity may contribute to increased market uncertainty, its predictive power is limited and should be interpreted in the context of broader market dynamics.


