# CPI Project README
 
## Table of Contents
1. [Project Overview](#project-overview)
2. [Data Sources](#data-sources)
3. [Methodology](#methodology)
   - [Consumer Product Selection](#consumer-product-selection)
   - [Weight Assignment](#weight-assignment)
   - [API Data Retrieval](#api-data-retrieval)
   - [CPI Calculation](#cpi-calculation)
4. [Inflation Analysis](#inflation-analysis)
5. [Visualization](#visualization)
6. [Conclusion](#conclusion)
7. [How to Run the Project](#how-to-run-the-project)
8. [License](#license)

## Project Overview
This project analyzes the Consumer Price Index (CPI) as it relates to college students by creating a tailored CPI based on common products and services used by this demographic. The analysis includes transportation, food staples, utilities, and more, providing insights into the inflationary pressures faced by students across different U.S. regions.

## Data Sources
The data for this project is sourced from the U.S. Bureau of Labor Statistics (BLS) API, which provides historical CPI data for various consumer products and services.

## Methodology

### Consumer Product Selection
The following products and services have been identified as relevant for college students:
- Transportation
- Cereal
- Gas
- Recreation
- Alcoholic Beverages
- Rent
- Electricity
- Apparel

### Weight Assignment
Weights for each product/service were assigned based on their importance in the typical college student’s budget, resulting in the following distribution:
- Transportation: 0.034
- Cereal: 0.068
- Gas: 0.034
- Recreation: 0.034
- Alcoholic Beverages: 0.034
- Rent: 0.068
- Electricity: 0.034
- Apparel: 0.034

### API Data Retrieval
The project makes an API call to download CPI data for the selected products over a five-year period (January 2017 to January 2022), including the general CPI for comparison.
```
import requests
import json
# API call logic...
```

### CPI Calculation
The custom CPI is computed using the weights assigned to each product and the corresponding CPI data retrieved from the API.
```
myData["myCPI"] = 0.034 * myData["CUUR0300SAT"] + ... + 0.068 * myData["CUUR0200SAA"]

```
## Inflation Analysis
12-month inflation rates are computed for both the custom CPI and the general CPI to assess trends and volatility over time.
```
def myinflation(lag): # Compute the percent change in the level of myCPI for
the 12 months starting '12+lag' months ago and ending 'lag' months ago.

Args:
lag (int): The number of months lag.

Returns:
float: Percent change in CPI.
#
new = mycpi[lag]
old = mycpi[12 + lag]
change = (new / old - 1) * 100
return change
```

## Visualization
A comparative line graph illustrates the inflation trends for the custom CPI and the general CPI over various lag periods.

## Conclusion
While this CPI isn't as resistant to fluctuations (less robust) as the much larger general CPI, it still captures the overall trend of inflation impacting college students. The results indicate that essential consumer products integral to students' lives, such as gas, recreation, and rent, are more sensitive to inflation changes. This can contribute to the volatility of their CPI compared to the general CPI. The analysis highlights the importance of considering specific demographics when assessing inflation impacts, as the experiences of college students may significantly differ from the broader population. A comparative graph is created to visualize the inflation rates of the custom CPI against the general CPI over various lag periods.

## How to Run the Project
1. Ensure you have Python and the necessary libraries (`requests`, `pandas`, `matplotlib`) installed.
2. Set up your BLS API key in a secure environment variable.
3. Run the main script to retrieve data, perform calculations, and generate visualizations.

## License
This project is licensed under the MIT License. See the LICENSE file for details.
