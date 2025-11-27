# Air Quality Monitor Representativeness in the Contiguous United States \-&gt; data \-&gt; **air monitors**

## Description

**Project Objective:** Determine whether state and local governments site air monitors in areas that capture data that are representative of actual air quality. 

**Project Folder:** The Air Monitors folder contains the scripts for three analyses. The first analysis cleans the EPA's 2019 air monitor dataset. The second analysis extracts daily alternative PM2.5 data to the air monitors from analysis one. The third analysis asseses the combined dataset from analysis 2, with the goal to determine whether the alternative air quality dataset is appropriate for use in our project objective.

## Data Collection

- **Period**: January\-December 2019
- **Sites**: Contiguous United States \(after Alaska, Hawaii, and territories are dropped in Analysis 2\)
- **Frequency**: Daily
- **Instruments**: State and Local PM2.5 Air Monitoring Sites; Machine Learning Alternative PM2.5 estimates

## File Organization

- `A_air_monitors/` \- R script in a Jupyter Notebook used to explore and clean EPA's 2019 AQS dataset
- `B_air_monitors_w_alt_data/` \- R script in a Jupyter Notebook used to combine the alternative air quality dataset with the cleaned EPA 2019 AQS dataset
- `C_air_monitors_w_alt_data_QA_check/` \- R scripts in a Jupyter Notebook used to assess the quality of the alternative air quality dataset relative to the project objective

## Requirements

- R
- Packages: dplyr, tidyr, readr, vroom, ggplot2, stringr, terra, naniar

## Contact

Seth Gerhart \- [TBD@email.com](mailto:TBD@email.com)

## License

Please cite when using this data. 
