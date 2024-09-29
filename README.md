# <p align="center">CPI Project</p>

## Table of Contents

1. [Overview](#overview)
2. [Discussion, Conclusion, and Results Visualization](#discussion-conclusion-and-results-visualization)
3. [Data Sources](#data-sources)
4. [Key Components](#key-components)
5. [CPI Calculation](#cpi-calculation)
6. [API Data Retrieval](#api-data-retrieval)

## Overview

This project analyzes the Consumer Price Index (CPI) for college students by evaluating essential products and services they typically consume. It computes a custom CPI based on selected items and their respective weights across different regions in the U.S.

## Discussion, Conclusion, and Results Visualization

While this CPI isn't as resistant to fluctuations (less robust) as the much larger general CPI, it still captures the overall trend of inflation impacting college students. The results indicate that essential consumer products integral to students' lives, such as gas, recreation, and rent, are more sensitive to inflation changes. This can contribute to the volatility of their CPI compared to the general CPI.

The analysis highlights the importance of considering specific demographics when assessing inflation impacts, as the experiences of college students may significantly differ from the broader population.

A comparative graph is created to visualize the inflation rates of the custom CPI against the general CPI over various lag periods.

## Consumer Products and Weights

The following products and services have been identified as essential for college students, along with their respective weights:

- **Transportation**: 0.034
- **Cereal**: 0.034
- **Gas**: 0.068
- **Recreation**: 0.034
- **Alcoholic Beverages**: 0.034
- **Rent**: 0.034
- **Electricity**: 0.034
- **Apparel**: 0.068

## Data Sources

Prices for the above products are collected from three regions, identified by their respective series codes:

- **Northeast (0100)**
- **Midwest (0200)**
- **South (0300)**

## Data Collection

An API call is made to download the CPI data for the last five years (January 2017 to January 2022). The API retrieves data for both the custom basket and the general CPI (CUUR0000SA0) for comparison.

## Custom CPI Calculation

The custom CPI is calculated by applying the specified weights to the collected price data.

## Inflation Calculation

Inflation rates are computed using specific functions that calculate the percent change over specified lag periods.
```python
def myinflation(lag):
    """Compute the percent change in the level of myCPI for the 
    12 months starting '12+lag' months ago and ending 'lag' months ago.
    
    Args:
        lag (int): The number of months lag.
    
    Returns:
        float: Percent change in CPI.
    """
    new = mycpi[lag]
    old = mycpi[12 + lag]
    change = (new / old - 1) * 100
    return change
```
## Results Visualization

A comparative graph is created to visualize the inflation rates of the custom CPI against the general CPI over various lag periods. The graph includes labeled axes and a legend for clarity.

## Discussion of Findings

The findings indicate that the custom CPI, while less robust than the general CPI, effectively captures the inflation trends relevant to college students. Notably, essential products such as gas, recreation, and rent demonstrate higher sensitivity to inflation, highlighting the financial pressures faced by students.

## Usage

1. Set up your API key in `APIkeys.py`.
2. Run the main script to collect data, calculate CPI, and visualize results.

## Conclusion

This project provides valuable insights into the cost of living for college students, demonstrating the necessity for tailored economic indicators to address specific demographic needs.
