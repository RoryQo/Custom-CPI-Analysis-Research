# Custom-CPI-Analysis-Research

<table align="center">
  <tr>
    <td colspan="2" align="center"><strong>Table of Contents</strong></td>
  </tr>
  <tr>
    <td>1. <a href="#project-overview">Project Overview</a></td>
    <td>5. <a href="#visualization">Visualization</a></td>
  </tr>
  <tr>
    <td>2. <a href="#data-sources">Data Sources</a></td>
    <td>6. <a href="#conclusion">Conclusion</a></td>
  </tr>
  <tr>
    <td>3. <a href="#inflation-analysis">Inflation Analysis</a></td>
    <td>7. <a href="#how-to-run-the-project">How to Run the Project</a></td>
  </tr>
  <tr>
    <td colspan="2"><a href="#license">8. License</a></td>
  </tr>
  <tr>
    <td colspan="2">9. <a href="#methodology">Methodology</a>
      <ul>
        <li><a href="#consumer-product-selection">Consumer Product Selection</a></li>
        <li><a href="#weight-assignment">Weight Assignment</a></li>
        <li><a href="#api-data-retrieval">API Data Retrieval</a></li>
        <li><a href="#cpi-calculation">CPI Calculation</a></li>
      </ul>
    </td>
  </tr>
</table>



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
