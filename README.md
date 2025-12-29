# Health Insurance Coverage Before and After the Affordable Care Act

## Project Overview

This portfolio examines how health insurance coverage changed across U.S. states before and after the Affordable Care Act (ACA), focusing on the period 2010–2016 using the provided `states.csv` dataset. It analyzes uninsured rates, marketplace enrollment, Medicaid expansion status, and public program enrollment to understand how policy and program changes affected coverage nationally and by state.

The project also uses a regression-based scenario model to explore what could happen to the nationwide uninsured rate over the next five years under different policy and coverage assumptions.

## Data Description

The primary dataset, `states.csv`, contains one row per state (plus a United States aggregate) with the following variables.

- **State**: U.S. state or District of Columbia, plus a United States total row. 
- **Uninsured Rate (2010)**: Percentage of residents without health insurance before ACA marketplaces and major coverage expansions took effect.  
- **Uninsured Rate (2015)**: Percentage of residents uninsured several years into ACA implementation.
- **Uninsured Rate Change (2010–2015)**: Percentage-point change in uninsured rate; negative values indicate reductions in the uninsured share.
- **Health Insurance Coverage Change (2010–2015)**: Change in the number of people with health insurance coverage over the period.
- **Employer Health Insurance Coverage (2015)**: Number of people covered by employer-sponsored insurance in 2015. 
- **Marketplace Health Insurance Coverage (2016)**: Number of people enrolled in ACA marketplace plans in 2016.  
- **Marketplace Tax Credits (2016)**: Number of marketplace enrollees receiving premium tax credits in 2016.
- **Average Monthly Tax Credit (2016)**: Average monthly premium tax credit (USD) among recipients.
- **State Medicaid Expansion (2016)**: Indicator (True/False) showing whether the state had adopted Medicaid expansion under the ACA by 2016.  
- **Medicaid Enrollment (2013, 2016)**: Total Medicaid enrollment before and after ACA-era expansions, used to measure growth.
- **Medicaid Enrollment Change (2013–2016)**: Absolute change in Medicaid enrollment over the period.
- **Medicare Enrollment (2016)**: Total Medicare enrollment, giving additional context on public coverage.  

## Research Questions

Using these variables, the project addresses the following questions.

- How did uninsured rates change between 2010 and 2015 at state and national levels?  
- Do Medicaid expansion states experience larger reductions in uninsured rates than non-expansion states?  
- How are marketplace enrollment and premium tax credits related to changes in uninsured rates?  
- Which states saw the largest gains in overall coverage and Medicaid enrollment?  
- Under different policy and coverage scenarios, what might happen to the nationwide uninsured rate over the next five years?

## Analysis Plan and Modeling Approach

The analysis is organized into several focused notebooks, each with a clear goal.

- `notebooks/01_data_preparation.ipynb`  
  - Load `states.csv`, clean percentage and currency fields, convert the Medicaid expansion flag to a Boolean, and handle missing values.

- `notebooks/02_uninsured_trends.ipynb`  
  - Describe uninsured rates in 2010 and 2015, compute changes by state, and summarize national patterns.
  - Highlight states with the largest reductions or smallest improvements in uninsured rates.

- `notebooks/03_medicaid_expansion_vs_nonexpansion.ipynb`  
  - Compare uninsured rate changes and coverage gains between Medicaid expansion and non-expansion states.  
  - Relate Medicaid enrollment changes (2013–2016) to changes in uninsured rates. 

- `notebooks/04_marketplace_coverage.ipynb`  
  - Analyze marketplace enrollment, tax credits, and average credit amounts across states.
  - Explore how these marketplace variables correlate with uninsured rate changes.

- `notebooks/05_uninsured_rate_projection.ipynb`  
  - Build an interpretable **regression model** using state-level data to understand how coverage and policy variables relate to changes in uninsured rates.
  - Example targets:  
    - `Uninsured Rate Change (2010-2015)`; or  
    - `Uninsured Rate (2015)` with `Uninsured Rate (2010)` as a control.
  - Example predictors:  
    - `State Medicaid Expansion (2016)`  
    - `Health Insurance Coverage Change (2010-2015)`  
    - `Medicaid Enrollment Change (2013-2016)`  
    - `Marketplace Health Insurance Coverage (2016)`  
    - `Marketplace Tax Credits (2016)`  
    - `Average Monthly Tax Credit (2016)`  
    - `Employer Health Insurance Coverage (2015)` (possibly scaled).
  - Use the fitted regression to construct **scenarios** for the next five years (e.g., more Medicaid expansions, changes in marketplace enrollment), and combine those effects with an external starting national uninsured rate to illustrate possible future paths.

Visualizations from these notebooks (bar charts, scatter plots, and maps, if used) are exported into the `plots/` directory for use in the portfolio narrative.

## Repository Structure

- `README.md` – Project overview, data description, modeling approach, and analysis roadmap (this file).  
- `data/`  
  - `states.csv` – State-level ACA coverage and enrollment indicators.
- `notebooks/`  
  - `01_data_preparation.ipynb`  
  - `02_uninsured_trends.ipynb`  
  - `03_medicaid_expansion_vs_nonexpansion.ipynb`  
  - `04_marketplace_coverage.ipynb`  
  - `05_uninsured_rate_projection.ipynb`  
- `plots/` – Exported figures used in the portfolio.  
- `requirements.txt` – Python dependencies (for example: pandas, numpy, matplotlib, seaborn, statsmodels, jupyter). 
