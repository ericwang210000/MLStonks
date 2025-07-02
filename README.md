# ML Stonks

**Machine-learning–augmented Black–Litterman portfolio engine**

InvestmentViewML combines the mathematical rigor of the Black–Litterman model with real-time text-derived sentiment and search-trend signals. It is designed to help investors and researchers build transparent, data-driven return forecasts and portfolio allocations.

---

## Key Features

| Feature                     | Description                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| **Black–Litterman Backbone** | Provides a robust Bayesian framework for blending market equilibrium with subjective views |
| **Sentiment Adjustment**     | Incorporates natural language sentiment scores using VADER to inform expected returns |
| **Google Trends Integration** | Enhances view construction through macroeconomic attention metrics |
| **Sector-Specific Simulations** | Includes dedicated scripts for portfolios in Real Estate and Consumer Discretionary sectors |

---

## Methodology Overview

1. **Baseline Construction**  
   - Equilibrium returns computed using reverse optimization on historical market data  
   - Market cap and volatility data used to derive implied excess returns  

2. **View Generation**  
   - Articles from financial sources are scraped and scored using VADER sentiment analysis  
   - Google Trends provides supplementary data for macroeconomic attention shifts  
   - Scores are aggregated by asset class and sector  

3. **BL Integration**  
   - Views are injected into the Black–Litterman model as adjusted expected returns  
   - Posterior returns are computed and used for portfolio optimization  

---

## Example Module: Real Estate & Consumer Discretionary

The file `real_estate_&_consumer_discretionary.py` contains a prototype pipeline that:

- Gathers price data for real estate equities (e.g., AMT, BXP, EQIX, PLD, CCI)  
- Applies uniform weights across selected tickers  
- Computes portfolio-level returns  
- Adjusts return expectations based on sentiment scores  

This module serves as a proof-of-concept for integrating VADER-derived sentiment views into sector-specific investment models.

---

## Example Module: Google Trends Signal Extraction

The file `google_trends.py` provides an independent implementation for collecting and analyzing keyword search interest using Google Trends. It:

- Uses the `pytrends` library to access Google Trends data  
- Defines keyword groups related to finance and technology (e.g., “Inflation”, “Stock Market”, “Tech”)  
- Maps keywords to their topic IDs and retrieves time series data for attention tracking  

This module is currently not yet integrated with the sentiment or portfolio scripts but is intended to form part of the final macroeconomic view adjustment mechanism in the Black–Litterman engine.

---

## Roadmap

- [x] Core Black–Litterman engine  
- [x] Sentiment scoring with VADER  
- [x] Sector-focused simulation (Real Estate, Consumer Discretionary)  
- [x] Google Trends signal extraction  
- [ ] View aggregation & weighting refinement  
- [ ] Web scraping and Google Trends automation  
- [ ] Full dashboard visualization  
- [ ] Cross-integrated view adjustment model  

---

## Setup

To run the example scripts:

```bash
pip install -r requirements.txt
python real_estate_&_consumer_discretionary.py
python google_trends.py