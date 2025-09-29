# FinBeta: CAPM Risk & Return Analyzer 📈

[![Streamlit App](https://img.shields.io/badge/Streamlit-Live%20Demo-brightgreen)](https://finbeta.streamlit.app/)

## Overview
**FinBeta** is an interactive **Capital Asset Pricing Model (CAPM) Analyzer** built with [Streamlit](https://streamlit.io).  
It allows users to explore the relationship between stock returns and market risk (systematic risk), compute **Beta values**,  
and estimate **expected returns using CAPM**.

The app fetches **live financial data** from:
- 📊 **Yahoo Finance (`yfinance`)** → Stock prices  
- 📈 **FRED (`pandas_datareader`)** → S&P 500 Index (market benchmark)  

This makes it a **data-driven financial dashboard** for both learners and professionals in finance, data science, and risk analytics.

---

## Features 🚀
- Select multiple stocks and time horizons (in years).  
- Fetch historical adjusted prices from Yahoo Finance & FRED.  
- Display **DataFrame head & tail** for quick inspection.  
- Visualize:
  - Stock prices (absolute scale)  
  - Normalized stock prices (relative performance)  
- Compute **Beta values** of stocks relative to S&P 500.  
- Estimate **Expected Return using CAPM formula**.  
- Interactive scatter plot of **stock return vs. market return** with regression line.  

---

## Mathematical Intuition 📐

### 1. Daily Returns
For each stock price $S_t$ and index $M_t$, daily returns are computed as:

$$ R_t = \frac{P_t - P_{t-1}}{P_{t-1}} $$

This transforms price data into return series suitable for risk-return analysis.

---

### 2. Beta ($\beta$)
The **Beta** of a stock measures its sensitivity to market movements:

$$ R_{stock} = \alpha + \beta R_{market} + \epsilon $$

where:  
- $\beta > 1$: stock is more volatile than the market  
- $\beta < 1$: stock is less volatile than the market  
- $\beta = 1$: stock moves with the market  

In the app, $\beta$ is estimated via **linear regression** (slope of regression line).

---

### 3. CAPM Expected Return
The **Capital Asset Pricing Model** provides expected return:

$$ E(R_i) = R_f + \beta_i (E(R_m) - R_f) $$

where:  
- $E(R_i)$: Expected return of stock $i$  
- $R_f$: Risk-free rate (set to 0 for simplicity in this app)  
- $\beta_i$: Beta of stock $i$  
- $E(R_m)$: Expected return of market (S&P 500)  

This links **systematic risk ($\beta$)** with **expected return**, forming the backbone of modern portfolio theory.

---

## Data Science Intuition 🤖
- **Feature Engineering**: Convert raw prices → returns (stationary, suitable for regression).  
- **Regression Modeling**: Fit linear model between stock returns & market returns.  
- **Normalization**: Compare relative stock performance by scaling all prices to 1 at start date.  
- **Visualization**: Interactive Plotly charts allow exploration of trends & beta risk visually.  
- **Pipeline**: Functions abstract data retrieval, transformation, and modeling for reusability.  

---

## Project Structure 📂
CAPM-Project/
├── capm_functions.py # Helper functions (returns, beta, plotting)
├── CAPM_Return.py # Main Streamlit app (multi-stock analysis)
├── pages/
│ └── Calculate_Beta.py # Streamlit subpage (single-stock beta)
└── .streamlit/
└── config.toml # Dark mode theme config


---

## Screenshots 🖼️

### Multi-Stock Analysis
![Multi-stock](a34a6495-a804-42aa-879f-264835dd8197.png)

### Single Stock Beta
![Single-stock](5d64cd74-bf9f-4507-be6b-55ffd26158ce.png)

This project is live at:

👉 https://finbeta.streamlit.app/
