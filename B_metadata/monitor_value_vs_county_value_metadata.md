# Monitor Value vs County Value

**Creator:** Seth Gerhart

**Institution:** Yale Environmental Data Science Certificate Program

## Description
This dataset all PM2.5 monitoring sites in the contiguous United States, their daily modeled PM2.5 estimates at the monitor, and their daily county-level median modeled PM2.5 value. The modeleded values were derived from research out of the Universities of Maryland and Iowa on 11/03/2025. That dataset contains 1-kilometer resolution PM2.5 estimates in the contiguous United States for every day in the year 2019 and was generated from big data (e.g., ground-based measurements, satellite remote sensing products, atmospheric reanalysis, and model simulations) using artificial intelligence. The Monitor Value vs County Value dataset also calculates the each monitors daily difference and percent difference from its county median.

## Variables
- AQS_Site_ID <chr>
  - Unique monitor identifier
- COUNTYNS <chr>
  - Unique county identifier
- date <date>
  - Date of alternative and county modeled PM2.5 reading
- Alt_PM25 <dbl>
  - Modeled PM2.5 reading at the monitor (µg/m³)
- county_daily_median <dbl>
  - The monitor's county median modeled PM2.5 reading (µg/m³)
- alt_median_difference <dbl>
  - The difference between the monitors modeled PM2.5 reading and the monitor's county median modeled PM2.5 reading (µg/m³)
- alt_percent_difference <dbl>
  - The percent difference between the monitors modeled PM2.5 reading and the monitor's county median modeled PM2.5 reading (%)

## Temporal Coverage

- **Period:** January 1, 2019 – December 31, 2019
- **Frequency**: Daily

## Spatial Coverage

- Contiguous United States (CRS: EPSG:4326)

## Limitations
Alternative PM2.5 data represent modeled estimates and may differ from
ground observations. 
  
## Data Sources:
- **daily_88101_2019.csv:** Derived from the U.S. EPA Pre-Generated Data Files webpage on 10/28/2025, this dataset contains the PM2.5 air monitor data for every day in the year 2019 for all monitors in the United States and its territories. 
  - Data Dictionary: https://www.epa.gov/aqs/aqs-data-dictionary
  - Data: https://aqs.epa.gov/aqsweb/airdata/download_files.html#Daily (see "Particulates" and "2019")
- **USHAP_PM2.5_D1K_2019_V1.zip:** Derived from research out of the Universities of Maryland and Iowa on 11/03/2025, this dataset contains 1-kilometer resolution PM2.5 estimates in the contiguous United States for every day in the year 2019. The dataset was generated from big data (e.g., ground-based measurements, satellite remote sensing products, atmospheric reanalysis, and model simulations) using artificial intelligence. The researchers show their estimates align well with physical measurements, with 0.82 cross-validated coefficients of determination.
  - Paper: https://www.thelancet.com/journals/lanplh/article/PIIS2542-5196(23)00235-8/fulltext
  - Data: https://zenodo.org/records/7884640

## Contact

Seth Gerhart \- [TBD@email.com](mailto:TBD@email.com)

## License

Please cite when using this data. 

