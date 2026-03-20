# Air Quality Monitor Representativeness in the Contiguous United States \-&gt; data \-&gt; **air monitors**

## Description

**Project Objective:** Determine whether state and local governments site air monitors in areas that capture data that are representative of actual air quality. 

**Project Folder:** The Air Monitors folder contains the scripts for five analyses. 

- The first analysis \(A\) cleans the EPA's 2019 air monitor dataset. 
- The second analysis \(B\) extracts daily alternative PM2.5 data to the air monitors from analysis one. 
- The third \(C\) analysis asseses the combined dataset from analysis 2, with the goal to determine whether the alternative air quality dataset is appropriate for use in our project objective. 
- The fourth \(E\) analysis assigns county identifers to the monitor dataset to ease future comparisons to county median PM2.5 values. 
- The fifth \(F\) analysis compares PM2.5 values at the monitors to relevant county PM2.5 medians.

_Note: A sixth intermediary analysis is in the alternative\_PM25\_data folder because it only pertains to cleaning the alternative PM2.5 data_

## Data Collection

- **Period**: January\-December 2019
- **Sites**: Contiguous United States \(after Alaska, Hawaii, and territories are dropped in Analysis 2\)
- **Frequency**: Daily
- **Instruments**: State and Local PM2.5 Air Monitoring Sites; Machine Learning Alternative PM2.5 estimates

## File Organization

- `A_air_monitors/` \- R script in a Jupyter Notebook used to explore and clean EPA's 2019 AQS dataset
- `B_air_monitors_w_alt_data/` \- R script in a Jupyter Notebook used to combine the alternative air quality dataset with the cleaned EPA 2019 AQS dataset
- `C_air_monitors_w_alt_data_QA_check/` \- R scripts in a Jupyter Notebook used to assess the quality of the alternative air quality dataset relative to the project objective
- `E_air_monitors_w_alt_data_and_county_ID` \- R scripts in a Jupyter Notebook used to add county IDs to the monitor dataset for future comparison to county medians
- `F_air_monitors_altvalue_…dian__altvalue_comparison` \- R scripts in a Jupyter Notebook used to compare PM2.5 values at the monitor to PM2.5 county medians

## Requirements

- R  
  _Packages: dplyr, tidyr, readr, vroom, ggplot2, stringr, terra, naniar, tidyterra,   exactextractr, sf, lubridate, ggtext_

## Contact

Seth Gerhart \- [TBD@email.com](mailto:TBD@email.com)

## License

Please cite when using this data. 

