# Introduction

This repository contains the code and data for my Master’s thesis analyzing the impact of macroeconomic conditions on Airbnb supply across European capital cities. 

Using a balanced monthly panel of all 27 EU capital cities from August 2020 to December 2024 ($N = 27, T = 53, N \times T = 1,431$), the study measures how interest rates, inflation, tourism demand and employment conditions drive listing growth, also decomposed across property types: Entire homes, Private rooms, Shared rooms.


## Data Sources

* Airbnb Supply Metrics ([AirRoi](https://www.airroi.com/)): Active listing counts
* Macroeconomic Regressors ([Eurostat](https://ec.europa.eu/eurostat)): National GDP, unemployment rates, housing price indices, consumer confidence index, electricity prices, tourist arrivals. 
* Monetary Policy Indicators ([European Central Bank](https://www.ecb.europa.eu/)): Bank interest rates
* Pandemic Restrictions ([Oxford Covid-19 Government Response Tracker - OxCGRT](https://www.bsg.ox.ac.uk/research/covid-19-government-response-tracker)): Pandemic restriction indices


## Econometric Framework

The baseline specification estimates listing supply $S_{i,j,t}$ for property type $j$ in city $i$ at month $t$:

$$\ln(S_{i,j,t}) = \alpha_i + \boldsymbol{\beta} \mathbf{X}_{i,t} + \varepsilon_{i,j,t}$$

### Estimated Models
1. Pooled OLS: Benchmark model with standard errors clustered at the city level.
2. Fixed Effects: Controls for time-invariant city amenities, geography and baseline housing stock.
3. Random Effects: Evaluated against FE using the Hausman specification test.
4. FE-2SLS (Instrumental Variables): Corrects for reverse causality.
   * Endogenous regressor: Tourism arrivals
   * Bartik shift share instrument - Covid stringency index x Passenger shares