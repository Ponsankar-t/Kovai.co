# Public Transport Time Series Analysis – Explanation

This notebook analyzes daily public transport passenger journeys across different service types. Below is a concise explanation of each step.

---

## 1. Load Data
Import the CSV file and display shape, columns, and first rows.  
**Why:** Verify the file loaded correctly and understand the structure.

---

## 2. Data Cleaning
- Drop completely empty rows and duplicates.
- Fill numeric missing values with **median**, categorical with **mode**.
- Convert date-like text columns to datetime format.
- Strip whitespace from text columns.

**Why:** Ensures clean, usable data for analysis without errors from missing or malformed values.

---

## 3. Sort by Date
Sort the dataframe chronologically by the date column.  
**Why:** Time-series analysis requires data in proper date order.

---

## 4. Daily Time Series Plot
Plot all service types (Local Route, Light Rail, Peak Service, Rapid Route, School, Other) over time.  
**Why:** Get a quick visual overview of all trends and patterns.

---

## 5. Monthly Smoothed Plot
Resample to monthly averages, then apply a 3-month rolling mean.  
**Why:** Reduces daily noise to reveal clearer medium-term trends.

---

## 6. Rapid Route Share Analysis
Calculate daily `Rapid Route / Total Journeys %`, apply 90-day moving average, and show long-term average.  
**Why:** Determines if Rapid Routes are the backbone of the system (~40% share indicates yes).

---

## 7. Local Route vs Light Rail Correlation (Post-2022)
- Scatter plot showing relationship between the two services.
- 30-day rolling correlation over time.

**Why:** Quantifies how closely these services move together (high correlation = similar demand patterns).

---

## 8. Peak Service Decline
Compare average daily Peak Service journeys **before 2020** vs **2022+**, show percentage change, and plot the time series with both averages marked.  
**Why:** Clearly shows the persistent drop in Peak Service after the pandemic.

---

## 9. School Ridership Volatility
- Calculate **Coefficient of Variation (CV = std/mean × 100)** for pre-2020 and 2022+.
- Boxplot per year showing distribution changes.

**Why:** CV measures how variable School journeys are; higher CV in 2022+ indicates more unpredictable ridership.

---

## 10. Detect Unusual "Other" Spikes
Flag days where `Other > mean + 3×std` and highlight them on the total journeys timeline.  
**Why:** Identifies rare, unusual events (anomalies) captured in the "Other" category.

---

## 11. 7-Day Forecast
Fit a **linear regression** on the last 90 days of total journeys and predict the next 7 days. Show forecast with ±1 std confidence band.  
**Why:** Provides a simple, interpretable short-term forecast based on recent trends.

---

## Key Insights

| Analysis | Finding |
|----------|---------|
| Rapid Route Share | ~40% of total journeys – a major backbone |
| Local Route & Light Rail | Highly correlated post-2022 |
| Peak Service | Significant decline from pre-2020 levels |
| School Ridership | More volatile in 2022+ compared to pre-2020 |
| "Other" Spikes | Rare anomalies detected on specific dates |
| Forecast | Linear trend predicts next 7 days based on recent 90-day pattern |

---

## Methods Used

- **Median/Mode imputation** – robust to outliers
- **Rolling averages** – smooths noise while preserving trends
- **Coefficient of Variation** – standardized measure of volatility
- **3-sigma rule** – simple anomaly detection threshold
- **Linear Regression** – straightforward trend-based forecasting

---

*This analysis provides a comprehensive view of public transport usage patterns, service comparisons, volatility, anomalies, and short-term forecasting.*
