# Air Quality Monitor Representativeness in the Contiguous United States -> **EPA Pre-Generated Data Files**

## Description

**Project Objective:** Determine whether state and local governments site air monitors in areas that capture data that are representative of actual air quality. 

**Project Folder:** The EPA Pre-Generated Data Files contains pre-generated files of data for use by people who understand the EPA ambient air quality monitoring program and data. Each daily summary file contains data for every monitor (sampled parameter) in our database for each day. These files are separated by parameter (or parameter group) to make the sizes more manageable.

For the purposes of AQS, a monitor does not refer to a specific piece of equipment. Instead, it reflects that a given pollutant (or other parameter) is being measured at a given site.

Identified by:

- The site (state + county + site number) where the monitor is located AND

- The pollutant code AND

- POC – Parameter Occurrence Code. Used to uniquely identify a monitor if there is more than one device measuring the same pollutant at the same site.

For example monitor IDs are usually written in the following way:

|`SS-CCC-NNNN-PPPPP-Q`|
| :------------: |

<span style='font-size:small'>where SS is the State FIPS code, CCC is the County FIPS code, and NNNN is the Site Number within the county \(leading zeroes are always included for these fields\), PPPPP is the AQS 5\-digit parameter code, and Q is the POC. </span>

<span style='font-size:small'>For example:</span>

|`01-089-0014-44201-2`|
| :------------: |

is Alabama, Madison County, Site Number 14, ozone monitor, POC 2.

This file will contain a daily summary record that is:

1) The aggregate of all sub-daily measurements taken at the monitor.

2) The single sample value if the monitor takes a single, daily sample (e.g., there is only one sample with a 24-hour duration). In this case, the mean and max daily sample will have the same value.

The daily summary files contain (at least) one record for each monitor that reported data for the given day. There may be multiple records for the monitor if:

- There are calculated sample durations for the pollutant. For example, PM2.5 is sometimes reported as 1-hour samples and EPA calculates 24-hour averages.

- There are multiple standards for the pollutant (q.v. pollutant standards).

- There were exceptional events associated with some measurements that the monitoring agency has or may request be excluded from comparison to the standard.

The file is comma separated variables (CSV) with a header row.

| Field Position | Field Name | Description |
| :------------ | :------------ | :------------ |
|1|State Code|The FIPS code of the state in which the monitor resides.|
|2|County Code|The FIPS code of the county in which the monitor resides.|
|3|Site Num|A unique number within the county identifying the site.|
|4|Parameter Code|The AQS code corresponding to the parameter measured by the monitor.|
5|POC|This is the “Parameter Occurrence Code” used to distinguish different instruments that measure the same parameter at the same site.|
6|Latitude|The monitoring site’s angular distance north of the equator measured in decimal degrees.|
7|Longitude|The monitoring site’s angular distance east of the prime meridian measured in decimal degrees.|
8|Datum|The Datum associated with the Latitude and Longitude measures.|
9|Parameter Name|The name or description assigned in AQS to the parameter measured by the monitor. Parameters may be pollutants or non-pollutants.|
10|Sample Duration|The length of time that air passes through the monitoring device before it is analyzed (measured). So, it represents an averaging period in the atmosphere (for example, a 24-hour sample duration draws ambient air over a collection filter for 24 straight hours). For continuous monitors, it can represent an averaging time of many samples (for example, a 1-hour value may be the average of four one-minute samples collected during each quarter of the hour).|
11|Pollutant Standard|A description of the ambient air quality standard rules used to aggregate statistics. (See description at beginning of document.)|
12|Date Local|The calendar date for the summary. All daily summaries are for the local standard day (midnight to midnight) at the monitor.|
13|Units of Measure|The unit of measure for the parameter. QAD always returns data in the standard units for the parameter. Submitters are allowed to report data in any unit and EPA converts to a standard unit so that we may use the data in calculations.|
14|Event Type|Indicates whether data measured during exceptional events are included in the summary. A wildfire is an example of an exceptional event; it is something that affects air quality, but the local agency has no control over. No Events means no events occurred. Events Included means events occurred and the data from them is included in the summary. Events Excluded means that events occurred but data form them is excluded from the summary. Concurred Events Excluded means that events occurred but only EPA concurred exclusions are removed from the summary. If an event occurred for the parameter in question, the data will have multiple records for each monitor.|
15|Observation Count|The number of observations (samples) taken during the day.|
16|Observation Percent|The percent representing the number of observations taken with respect to the number scheduled to be taken during the day. This is only calculated for monitors where measurements are required (e.g., only certain parameters).|
17|Arithmetic Mean|The average (arithmetic mean) value for the day.|
18|1st Max Value|The highest value for the day.|
19|1st Max Hour|The hour (on a 24-hour clock) when the highest value for the day (the previous field) was taken.|
20|AQI|The Air Quality Index for the day for the pollutant, if applicable.|
21|Method Code|An internal system code indicating the method (processes, equipment, and protocols) used in gathering and measuring the sample. The method name is in the next column.|
22|Method Name|A short description of the processes, equipment, and protocols used in gathering and measuring the sample.|
23|Local Site Name|The name of the site (if any) given by the State, local, or tribal air pollution control agency that operates it.|
24|Address|The approximate street address of the monitoring site.|
25|State Name|The name of the state where the monitoring site is located.|
26|County Name|The name of the county where the monitoring site is located.|
27|City Name|The name of the city where the monitoring site is located. This represents the legal incorporated boundaries of cities and not urban areas.|
28|CBSA Name|The name of the core bases statistical area (metropolitan area) where the monitoring site is located.|
29|Date of Last Change|The date the last time any numeric values in this record were updated in the AQS data system. |

**Source Link:** https://aqs.epa.gov/aqsweb/airdata/download_files.html

**Data Dictionary Link:** https://aqs.epa.gov/aqsweb/airdata/FileFormats.html#_monitors

## Data Collection

- **Period**: January\-December 2019
- **Sites**: The United States and its Territories
- **Frequency**: Daily
- **Instruments**: State and Local PM2.5 Air Monitoring Sites

## File Organization

  - `daily_88101_2019.csv/` - EPA's PM2.5 daily data for 2019


## Requirements

- NA

## Contact

Air Quality Analysis Group

U.S. EPA Office of Air Quality Planning and Standards

Mail Code C304-04

Research Triangle Park, NC 27711

https://www.epa.gov/outdoor-air-quality-data/forms/contact-us-about-outdoor-air-quality-data

## License

Please cite the following author when using this data. 

- US Environmental Protection Agency. Air Quality System Data Mart [internet database] available via https://www.epa.gov/outdoor-air-quality-data. Accessed October 28, 2025.

