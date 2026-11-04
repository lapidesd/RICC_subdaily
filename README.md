# RICC_subdaily

This repository includes code and data used to process sentek moisture data for the RiCC sites in Western Australia. This document contains a file directory, description of QA/QC flags, and a description of the sentek processing workflow.

File directory for this repo:
* Code:
    * Sentek_processing.ipynb: jupyter notebook processing raw sentek soil moisture data into final timeseries
    * other_data_processing.ipynb: jupyter notebook containing code to process other related datasets that may be helpful for repurposing
    * Diel_sgnals-share.ipynb: jupyter notebook exploring subdaily sentek data (this is just to see figures, I didn't update this to run properly in this directory. I'm working on this elsewhere)
* Data:
    * raw_sentek: directory contains afsystems files downloaded from Irrimax portal. GN_sentek directory includes manually downloaded data that are processed into the S1, S2, S3, S4 afsystems files.
    * other_inputs:
         * GG1_Atmospheric_TwoYrs.csv: old processed Gingin weather
         * WP2_Sentek_TwoYrs.csv: old processed WP2 soil moisture that is missing from Irrimax
         * silo_rainfall_SITE.csv: daily rainfall data downloaded from SILO
         * ET: directory containing licor data for each site that has it
    * static_outputs:
         * SITE_weather.csv: weather data from site instrumentation
         * gwdata_finalSITE.csv: groundwater monitoring data from boreholes at each site
         * GG_manual_groundwater_levels.csv: manually measured groundwater because logging sensor is having issues
    * temp_processing: directory containing intermediate data processing files for sentek data processing
    * final_sentek:
         * VWC_final_SITE.csv: final processed and flagged 15min sentek data
         * VWC_final_daily_SITE.csv: final processed and flagged daily sentek data

QA/QC flag defitions for Quality_flags (in both daily and 15min data):
    * (0) no flag
    * (1) settling period for instrumentation, 1-2 years at select sites that don't look right at start of record
    * (2) year 2 leaf litter cover over instrumentation at GG1
    * (3) moisture increase is substantially too high relative to incoming precipitation. Specifically, daily moisture increase exceeds rainfall in surrounding 3 days by more than 20%, and moisture increase greater than 20 mm

QA/QC flag definitions for column-specific 15min data:
    * (0) data meet quality standards for subdaily data usage (no increases during daytime)
    * (1) data meet quality standards for subdaily data usage (increase during day but rained recently)
    * (2) potential issues with subdaily data, use with caution

Instructions for processing sentek data:
* clone this repo to local
* download all data for each sensor, and put the updated datasets into ../Data/raw_sentek/
* run all blocks in Sentek_processing.ipynb
