# Module 4 - Predicting House Sales Prices using Time Series Data from Zillow

## Business Understanding
Aries Real Estate Investors buys and rehabs homes in high-growth urban areas. Homes are purchased to be renovated and sold (or flipped). Properties held longer than 30 days past end of renovation are rented for 3-5 years, then re-entered into the housing market. Aries is looking to expand its offering to buyers with a wider range of budgets to capture more market share. To make sure that new areas of investment are ideal, 5 zipcodes have been identified using the following criteria:

* Zipcodes are located in the Top 5 in 2019 Market rankings for Overall Real Estate Prospects according to Price Waterhouse Cooper's Emerging Trends in Real Estate 2019 Report
* Areas have demonstrated 30% or greater Return On Investment in the last 10 years
* Risk has been mitigated by selecting zipcodes in several geographical areas
* Price and return dispersion (measured by coefficient of variation) kept to minimum to lower risk

## Zillow Economic Research Dataset
Zillow is a top real estate marketplace that has a dedicated research team to provide accurate housing data and unbiased insights to home buyers and home sellers alike. The dataset contains historical sales price data back to 1996 for the United States.

## Approach

1. Data imported and cleaned to remove or replace missing values and outliers
2. Data for Top 5 Markets (Dallas-For Worth, Brooklyn, Raleigh-Durham, Orlando, Nashville) extracted based on the following:
    * Highest ROI over period 2008 to 2018 (post housing crash and Great Recession)
    * Coefficient of Variation below 0.5 for zip codes selected
3. Top 5 zip codes in each market selected
    * Brooklyn and Orlando had no zip codes that met the selection criteria
4. Separate model for Each zip code built using Facebook Prophet
5. Facebook Prophet predictions used to calculate percentage growth from 2018-2023
6. Top 5 zip codes selected based on higest percentage growth and model performance based on root mean squared error. 

## Files

- README.md: Instruction guide
- Zillow Time Series Analysis FBProphet.ipynb : a jupyter notebook file
- zillow_data.csv : Contains historical sales data for the United States from 1996 to 2018
- Overall_Real_Estate_Prospects: an image file that includes the US rankings for Overall Real Estate Prospects
- hottestMarkets_2019-9528a0: an image file that includes the top 10 markets from Zillow Economic Research
- us-states.json: a JSON file with the geometry of every state needed to support Folium Map creation
- Aries Real Estate Investors.pdf: presentation slides that hightlight the results from this project

## Requirements

In order to run the code in the jupyter notebook, you must have Python installed on you computer. Use Anaconda, as it had many useful libraries pre-installed. 

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install pystan and Facebook Prophet.

```bash
!pip install pystan
```
```bash
!pip install fbprophet
```
Import the following libraries:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
import seaborn as sns
plt.style.use('seaborn')
from fbprophet import Prophet as proph
from fbprophet.diagnostics import cross_validation
from fbprophet.diagnostics import performance_metrics
from fbprophet.plot import plot_cross_validation_metric
import folium
import warnings
warnings.filterwarnings('ignore')
```

If you are not able to install Facebook Prophet using the above method, install using Anaconda following the instructions below:

Open Git Bash Console

conda install gcc

conda install -c conda-forge fbprophet

## Findings

According to our models, we chose the following zipcodes because they exhibit high growth potential and a low amount of risk. These zipcodes have a projected growth between 47% and 54%:

Dallas-Fort Worth:
* 75235 - 53.78% Growth
* 75218 - 47.42% Growth
* 75081 - 47.28% Growth

Nashville:
* 37115 - 48.65% Growth
* 37211 - 46.70% Growth

Our models show that these zipcodes forecast excellent returns for the 5 year period 2018-2023. Although Raleigh-Durham was the number 1 market in the Emerging Trends in Real Estate Guide, none of the zipcodes were in the top 5 for growth.
