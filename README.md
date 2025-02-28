<h1 align="center">Custom CPI Analysis Research</h1>

<div>
  <table align="center">
    <tr>
      <td colspan="2" align="center" style="background-color: white; color: black;"><strong>Table of Contents</strong></td>
    </tr>
    <tr>
      <td style="background-color: white; color: black; padding: 10px;">1. <a href="#project-overview" style="color: black;">Project Overview</a></td>
      <td style="background-color: gray; color: black; padding: 10px;">6. <a href="#conclusion" style="color: black;">Conclusion</a></td>
    </tr>
    <tr>
      <td style="background-color: gray; color: black; padding: 10px;">2. <a href="#data-sources" style="color: black;">Data Sources</a></td>
      <td style="background-color: white; color: black; padding: 10px;">7. <a href="#how-to-run-the-project" style="color: black;">How to Run the Project</a></td>
    </tr>
    <tr>
      <td style="background-color: white; color: black; padding: 10px;">3. <a href="#inflation-analysis" style="color: black;">Inflation Analysis</a></td>
      <td style="background-color: gray; color: black; padding: 10px;">8. <a href="#license" style="color: black;">License</a></td>
    </tr>
    <tr>
      <td style="background-color: gray; color: black; padding: 10px;">
        4. <a href="#visualization" style="color: black;">Visualization</a><br>
      </td>
      <td style="background-color: white; color: black; padding: 10px;">
        5. <a href="#methodology" style="color: black;">Methodology</a><br>
        &nbsp;&nbsp;&nbsp;- <a href="#consumer-product-selection" style="color: black;">Consumer Product Selection</a><br>
        &nbsp;&nbsp;&nbsp;- <a href="#weight-assignment" style="color: black;">Weight Assignment</a><br>
        &nbsp;&nbsp;&nbsp;- <a href="#api-data-retrieval" style="color: black;">API Data Retrieval</a><br>
        &nbsp;&nbsp;&nbsp;- <a href="#cpi-calculation" style="color: black;">CPI Calculation</a>
      </td>
    </tr>
  </table>
</div>

## Project Overview
This project provides an analysis of the Consumer Price Index (CPI) as it relates to college students by creating a tailored CPI based on essential products and services commonly used by this demographic. The customized CPI accounts for various regions in the U.S. and highlights the inflationary pressures that affect students. Products and services selected for this CPI include transportation, food staples, utilities, recreation, alcohol, apparel, and rent.

The goal of this project is to evaluate how the CPI for college students varies compared to the general CPI and to identify which items or services contribute the most to price changes. The CPI is calculated for three regions: Northeast, Midwest, and South, providing a comprehensive look at regional inflation.

## Data Sources
The data for this analysis is sourced from the U.S. Bureau of Labor Statistics (BLS) API, which offers historical data on price changes for various consumer goods and services. We retrieve CPI data for the following regions and product categories from January 2017 to January 2022:

- Northeast
- Midwest
- South

Each series corresponds to a specific product or service, with each having a weighted value in the overall CPI calculation.

## Inflation Analysis
In this section, we analyze the inflation rate using the custom CPI for college students, comparing it with the general CPI. The custom CPI is calculated by assigning weights to key products and services. By comparing year-over-year inflation rates (12-month inflation), we assess how fluctuations in prices for student-essential items differ from the general consumer market.

```
def myinflation(lag):
    """Compute the percent change in CPI over a 12-month period."""
    new = mycpi[lag]
    old = mycpi[12 + lag]
    change = (new / old - 1) * 100
    return change
```

## Methodology

### API Data Retrieval
We used the BLS API to retrieve CPI data for the selected regions and products. The API allows us to pull historical data for multiple time periods, ensuring we have data spanning from January 2017 to January 2022. The function `multiSeriesV4` is responsible for querying the BLS API and compiling the results into a dataframe for further analysis.

```
import requests
import json
# API call logic...
```
### CPI Calculation
The custom CPI for college students was calculated by combining the weighted price changes of each product in the basket. We used the following formula for each month:

```math
CPI = \sum \left( \text{{weight of product}} \times \text{{price change of product}} \right)
```

This was done for each region (Northeast, Midwest, and South) as well as for the overall CPI (general market).

```
myData["myCPI"] = (0.034 * myData["CUUR0300SAT"] + 0.068 * myData["CUUR0300SETB01"]
                     + 0.034 * myData["CUUR0300SAF111"] + 0.034 * myData["CUUR0300SAR"]
                     + 0.034 * myData["CUUR0300SAF116"] + 0.034 * myData["CUUR0300SAS2RS"]
                     + 0.034 * myData["CUUR0300SEHF01"] + 0.068 * myData["CUUR0300SAA"])
```


### Consumer Product Selection
The commodities selected for this project were chosen based on a convenience survey conducted among senior economics majors at the University of Pittsburgh. The survey asked participants to provide information on their most common spending categories and products. This data was used to create a representative list of items and services that college students typically purchase and use. These include:

- **Transportation**: Including commuting and busing.
- **Cereal**: A common breakfast staple for many students.
- **Gas**: Necessary for transportation to and from school and work.
- **Recreation**: Vital for social life and leisure.
- **Alcoholic Beverages**: A common expenditure on college campuses.
- **Rent**: Most students rent apartments or dorms.
- **Electricity**: Essential for powering devices for school.
- **Apparel**: Necessary for daily wear.

These products were chosen to represent key spending areas for students that can be impacted by inflation.

### Weight Assignment
Each product and service is assigned a weight based on the number of appearances in the survey. The weights for each category are:

- **Transportation**: 0.034
- **Cereal**: 0.034
- **Gas**: 0.068
- **Recreation**: 0.034
- **Alcoholic Beverages**: 0.034
- **Rent**: 0.034
- **Electricity**: 0.034
- **Apparel**: 0.068

These weights were chosen to reflect the relative significance of each item in the CPI calculation for college students.


## Visualization
The inflation analysis is visualized by plotting the 12-month inflation for both the general CPI and the custom CPI across different time periods. This helps identify trends, volatility, and differences in inflationary pressures for college students compared to the broader population. The plot shows how specific products like gas, rent, and recreation influence the overall CPI for students.

<p align="center">
  <img src="https://github.com/RoryQo/Custom-CPI-Analysis-Research/raw/main/Fig1.jpg" width="450px"/>
</p>

## Conclusion
While the custom CPI based on student products does not have the robustness of the general CPI (due to its smaller, less diverse product base), it does capture the overall inflationary trend. The CPI for college students is often more volatile, particularly due to the high variability in rent, transportation costs, and recreational expenses, which are critical to students' everyday lives.

## How to Run the Project
To run the project on your own machine, follow these steps:

1. Clone the repository or download the source files.
```bash
   git clone https://github.com/your-username/Custom-CPI-Analysis-Research.git
```
2. Ensure you have Python 3.x installed and the following libraries:
   - requests
   - json
   - pandas
   - numpy
   - matplotlib
3. Obtain your BLS API key and save it as an environment variable (`BLS_API_key`).
```
import os
os.environ["BLS_API_key"] = "your_api_key_here"
```
4. Run the main script to download the data and perform the CPI calculations. The script will automatically call the BLS API and process the data for analysis.

## License
This project is licensed under the MIT License - see the LICENSE file for details.
