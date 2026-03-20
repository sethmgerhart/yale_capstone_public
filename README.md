# Air Quality Monitor Representativeness in the Contiguous United States

<span style='font-size:small'>_Note: This README contains this assignment's highlights. You may find the final report, which contains more comprehensive details and supporting figures, at the following location:_</span>

- <span style='font-size:small'>`capstone/A_data/E_outputs/Final_Report.ipynb`</span>

## Project Question

Determine whether state and local governments site PM2.5 monitors in areas that capture data that are representative of actual air quality.

## Key Findings

While 64 percent of PM2.5 monitors are in areas that generally represent county-level air quality, nearly 6 percent of monitors are in areas where PM2.5 concentrations fall below the county median at least 75 percent of the year. Geospatial analysis indicates that these monitors are in Maryland, North Dakota, Nevada, and Missouri. Their locations in these states may result in underestimates of representative air quality by approximately 15.0, 7.8, 3.7, and 3.6 percent, respectively. If monitor placement persistently understates ambient pollution levels, the Environmental Protection Agency could rely on data that underrepresents actual air quality conditions when assessing compliance with Clean Air Act standards and the public may be unknowingly exposed to elevated levels of pollution.

Because a portion of the monitoring network appears persistently located in low pollution areas, additional research is warranted to determine whether the observed pattern reflects legitimate siting constraints or whether these monitors truly underrepresent ambient PM2.5 levels. This additional research should incorporate additional years of data, additional pollutants, an analysis of regulatory siting criteria, and an assessment of monitor design values relative to regulatory thresholds to determine whether further oversight work is appropriate.

## Data Collection

<span style='font-size:small'>_Note: The raw data was too large to provide in the GitHub repository. Please see the the links and descriptions below to access the raw data for replication purposes._</span>

Summary-level information about the raw data:

- **Period**: January\-December 2019
- **Geospatial Scope**: Contiguous United States
- **Frequency**: Daily
- **Instruments**: State and local PM2.5 air monitoring sites; machine learning alternative PM2.5 estimates; U.S. Census Bureau administrative boundaries

This analysis used the following raw data:

- **Title:** _daily\_88101\_2019.csv_
  - **Description:** Derived from the U.S. EPA Pre\-Generated Data Files webpage on 10/28/2025, this dataset contains the PM2.5 air monitor data for every day in the year 2019 for all monitors in the United States and its territories.
  - **Data Dictionary:** [https://www.epa.gov/aqs/aqs\-data\-dictionary](https://www.epa.gov/aqs/aqs-data-dictionary) 
  - **Source Link:** [https://aqs.epa.gov/aqsweb/airdata/download\_files.html\#Daily](https://aqs.epa.gov/aqsweb/airdata/download_files.html#Daily) \(see "Particulates" and "2019"\)
- **Title:** _USHAP\_PM2.5\_D1K\_2019\_V1.zip_
  - **Description:** Derived from research out of the Universities of Maryland and Iowa on 11/03/2025, this dataset contains 1\-kilometer resolution PM2.5 estimates in the contiguous United States for every day in the year 2019. The dataset was generated from big data \(e.g., ground\-based measurements, satellite remote sensing products, atmospheric reanalysis, and model simulations\) using artificial intelligence. The researchers show their estimates align well with physical measurements, with 0.82 cross\-validated coefficients of determination.
  - **Paper:** [https://www.thelancet.com/journals/lanplh/article/PIIS2542\-5196\(23\)00235\-8/fulltext](https://www.thelancet.com/journals/lanplh/article/PIIS2542-5196(23)00235-8/fulltext) 
  - **Data:** https://zenodo.org/records/7884640
- **Title:** _tl\_2019\_us\_county.zip_ 
  - **Description:** Derived from the U.S. Census Bureau on 11/30/2025, this dataset contains each of the U.S. county boundaries in shapefile format. 
  - **Data:** [https://www.census.gov/cgi\-bin/geo/shapefiles/index.php](https://www.census.gov/cgi-bin/geo/shapefiles/index.php) 
- **Title:** _State\_FIPS.csv_
  - **Description:** Derived from the Federal Information Processing System \(FIPS\) Codes for States and Counties on 11/30/2025, this dataset contains each of the U.S. county and state's FIPS codes. FIPS codes are numbers which uniquely identify geographic areas.  The number of digits in FIPS codes vary depending on the level of geography.  State\-level FIPS codes have two digits, county\-level FIPS codes have five digits of which the first two are the FIPS code of the state to which the county belongs.
  - **Data:** https://transition.fcc.gov/oet/info/maps/census/fips/fips.txt

## Methodological Approach

This analysis was performed sequentially in the following six Jupyter Notebooks (see `capstone/A_data/A_analysis/...`):

1) `...air_monitors/A_air_monitors_cleanup.ipynb`
2) `...air_monitors/B_air_monitors_w_alt_data_extraction.ipynb`
3) `...air_monitors/C_air_monitors_w_alt_data_QA_check.ipynb`
4) `...air_monitors/E_air_monitors_w_alt_data_and_county_ID.ipynb`
5) `...alternative_PM25_data/D_alt_data_county_typical_daily_PM25_analysis.ipynb`
6) `...air_monitors/F_air_monitors_altvalue_county_median__altvalue_comparison.ipynb`

This analysis followed these six steps:

1. **Extract and Clean Contiguous United States PM2.5 Air Monitor Data.** I used the EPA’s Air Quality System dataset to obtain the location and daily PM2.5 observations for state and local regulatory monitors operating at least one day in the year 2019. I cleaned this dataset to ensure consistent formatting of monitor identifiers, coordinates, and daily PM2.5 measurements. I filtered the dataset to only include monitors operating within the contiguous United States to ensure comparability with the alternative PM2.5 dataset used in a later analysis.
2. **Extract and Clean Modeled PM2.5 Estimates at Monitor Locations** To evaluate the quality of modeled air quality measurements and to prepare to answer my objective, I incorporated an alternative PM2.5 dataset derived from satellite observations and machine\-learning models. This dataset provided estimated PM2.5 concentrations across the contiguous United States at 1 kilometer resolution. For each monitor location and operating day in 2019, I used the alternative PM2.5 dataset to extract the estimated PM2.5 value corresponding to the monitor’s coordinates. 
3. **Assess the Quality of Alternative and Regulatory Data** Before using the alternative PM2.5 dataset to evaluate monitor representativeness, I assessed whether the modeled values correlate with measured PM2.5 concentrations at monitor locations. This step confirmed that the alternative dataset reasonably approximates ambient PM2.5 conditions.
4. **Estimate County\-Level Daily Median Modeled PM2.5** For each day in 2019, I calculated the median modeled PM2.5 value across all raster cells located within each contiguous county boundary. I selected the median value to minimize bias introduced by extreme outliers. This analysis resulted in a dataset containing daily county\-level median PM2.5 values for all counties in the contiguous United States. I paired each daily county median estimate with a unique county code identifer for later comparison to the monitor dataset.
5. **Assign Monitors to Counties**  The assessed dataset from Step 3 did not contain unique county code identifers so I could not compare it to the daily county median estimates without additional processing. To enable comparison, I spatially associated each monitor with the county in which it is located. This allowed me to pair each daily monitor estimate with a unique county code identifer for later comparison to the daily county median estimate dataset.
6. **Compare Monitor Location Estimates to County\-Level Estimates** In this final step, I compared PM2.5 concentrations at each monitor location to the median PM2.5 value estimate for its county on the same day. For each monitor, I calculated the proportion of days during 2019 in which the monitor reported concentrations below the county median. I then categorized monitors based on the percentage of days they fell below the county median. This classification allowed me to identify monitors that may be persistently located in lower\-pollution areas relative to surrounding county conditions. I furthered this analysis by assessing the impact of the possible underreporting bias between states.

## File Organization

- `scripts/` \- GitHub control and useful code references \(not uploaded to GitHub\)
- `data/` \- Project folder \(uploaded to GitHub, sans raw\_data\)
  - `raw_data/` \- Original files
    - `air_monitors/` \- daily\_88101\_2019.csv
    - `alternative_PM25_data/` \- USHAP\_PM2.5\_D1K\_2019\_V1.zip
    - `census/` \- tl\_2019\_us\_county.zip 
    - `FCC/` \- State\_FIPS.csv
  - `processed_data/` \- Cleaned intermediate files and final analysis results
    - `air_monitors/` \- Intermediate data predominately relating to the air monitor dataset
    - `alternative_PM25_data/` \- Intermediate data predominately relating to the modeled PM2.5 dataset
    - `final_output/` \- Final data supporting findings in final report
    - `intermediate_scratch/` \- Intermediate datasets used within notebooks to obtain a final dataset at the end of those notebooks. This folder was used to bookmark analysis progress to avoid CoCalc timeout issues.
  - `analysis/` \- R scripts
    - `air_monitors/`
      - `A_air_monitors/` \- R script in a Jupyter Notebook used to explore and clean EPA's 2019 AQS dataset
      - `B_air_monitors_w_alt_data/` \- R script in a Jupyter Notebook used to combine the alternative air quality dataset with the cleaned EPA 2019 AQS dataset
      - `C_air_monitors_w_alt_data_QA_check/` \- R scripts in a Jupyter Notebook used to assess the quality of the alternative air quality dataset relative to the project objective
      - `E_air_monitors_w_alt_data_and_county_ID` \- R scripts in a Jupyter Notebook used to add county IDs to the monitor dataset for future comparison to county medians
      - `F_air_monitors_altvalue-median_altvalue_comparison` \- R scripts in a Jupyter Notebook used to compare PM2.5 values at the monitor to PM2.5 county medians
    - `alternative_PM25_data/`
      - `D_alt_data_county_typical_daily_PM25_analysis` \- R script in a Jupyter Notebook used to clean and calculate the median alternative PM2.5 data in every contiguous U.S. county for every day in 2019
  - `metadata/` \- Data documentation
    - `monitor_value_vs_county_value_metadata/` \- R markdown documenting the monitor value versus county value dataset, which is a final output of this project
  - `outputs/` \- Figures and reports
  - `archive/` \- Legacy Data
- `yale_capstone_public/` \- GitHub repository

## Requirements

- R
- Packages: dplyr, tidyr, readr, vroom, ggplot2, stringr, terra, naniar, tidyterra,   exactextractr, sf, lubridate, ggtext

## Contact

Seth Gerhart - TBD@email.com

## License

Please cite when using this data. Citations for raw data provided in relevant folder README and Jupyter Notebook.

