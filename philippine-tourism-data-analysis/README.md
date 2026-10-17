# Philippine Tourism Data Analysis - Group 6 
 
Exploratory Data Analysis of Philippine tourism data. 

# After the World Fell Silent: The Rise, Collapse and Unfinished Comeback of Philippine Tourism

Philippine Tourism Trends by Market, 2008-2024

DS311 Exploratory Data Analysis - Midterm Lab Exam - Group 6 (Culture and Tourism)

Members: Aque, Badilla, Beturin, Dellosa, Ganhinhin, Pamplona, Ruiz

## Overview

This project analyses international visitor arrivals to the Philippines from January 2008 to December 2024, using the Department of Tourism (DOT) visitor-arrival statistics. The tables sit inside 17 yearly PDF reports whose layouts change over the years, so a large part of the work is extracting them correctly, checking them against the totals printed in the reports, and building one consistent dataset of 50 source markets over 201 months with data.

Business question:
How fast has international tourism to the Philippines grown since 2008, which source markets drove that growth, and how did COVID-19 change the way markets move relative to each other?

## Key Findings

- Arrivals grew from 3,139,422 (2008) to 8,260,913 (2019), a CAGR of 9.2% a year. The only pre-COVID dip was 2009 (-3.9%).
- COVID-19 was a sudden break: monthly arrivals fell from 796,164 (Jan 2020) to 948 (Apr 2020). Yearly arrivals dropped 82.1% in 2020 and a further 88.9% in 2021.
- The recovery is real but unfinished: 66% of the 2019 level in 2023 and 72% in 2024 (5,949,350 arrivals).
- Markets recovered unevenly. Jan-Oct 2023 vs Jan-Oct 2019: USA 85.1%, Korea 72.7%, Japan 43.5%, China 14.9%.
- China accounts for 48.1% of the remaining gap to 2019 (Korea 16.5%, Japan 12.1%, USA 4.9%, Taiwan 4.4%).
- Markets look linked mainly because they all grew over the same years. The Korea-China correlation drops from 0.85 to 0.14 once each series' linear trend is removed, and the median correlation of year-over-year growth across 8 markets is only 0.10.
- Seasonality (trend-adjusted): January (115.8) and December (115.5) are the busiest months; September (82.5) and October (88.7) are the quietest.

## Repository Structure

data/
  raw/          17 original DOT PDF reports (2008.pdf ... 2024.pdf)
  processed/    data_cleaned.xlsx (long format: month x market)
                data_monthly_summary.xlsx (one row per calendar month)
notebooks/      Group 6 midterm lab notebook (.ipynb)

## Notebook Contents

1. Problem statement and business question
2. Data source and variables
3. Data extraction from PDF, cleaning and quality checks
4. Univariate analysis I: distribution of monthly arrivals
5. Univariate analysis II: growth and recovery, remaining gap, composition, seasonality
6. Bivariate analysis: correlation matrices, Korea vs China regression, correlation by period, rolling correlation
7. Conclusions, recommendations, limitations

## Data

Source: Philippine Department of Tourism, visitor arrival statistics
https://remote.tourism.gov.ph/tourism/demand-statistics/

No pre-compiled spreadsheet is used. The notebook reads the tables directly from the PDFs. The extraction was reconciled against the subtotals and grand totals printed in each report.

Unit: one row per month and source market.
Coverage: January 2008 to December 2024 (204 calendar months, 201 with data).
Markets: 50 core markets listed individually in every year 2008-2021 and in the 2024 top-60 table, grouped into 7 regions.

## How to Run

1. Clone the repository:
   git clone https://github.com/Ajooooooo/EDA-Group-6.git
   cd EDA-Group-6

2. Install the requirements:
   pip install pandas numpy matplotlib seaborn scipy statsmodels pdfplumber openpyxl jupyter

3. Open the notebook and run all cells. It finds the repository root automatically, whether you run it from the notebooks folder or from the repository root, and needs the PDFs in data/raw. The two processed Excel files are written to data/processed.

## Data Notes and Limitations

- The 2022 report starts in February and counts air arrivals only, by nationality. January 2022 is missing.
- The 2023 report stops in October. November and December 2023 are missing. They are left as blank (NaN), not zero.
- The 2024 report lists only the top 60 markets and has no separate overseas-Filipino row. The 2024 market figures look higher than earlier years for the eight largest markets checked, so they are read as indicative, not exact. Totals use the official DOT grand total and are not affected.
- 47 dash placeholders in the core markets were treated as zero and flagged in the dataset (was_dash).
- The analysis describes what happened, not why. The data have no spending, visa, flight or home-country information.

## References

- Philippine Department of Tourism, visitor arrival statistics: https://remote.tourism.gov.ph/tourism/demand-statistics/
- Group 6 repository: https://github.com/Ajooooooo/EDA-Group-6
