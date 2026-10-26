# RICC_subdaily

This repository includes code and data used to separate sensor artifacts from ecohydrological signatures in subdaily soil moisture data. Included in this repository is:
* Code:
    * Diel_sgnals-share.ipynb: jupyter notebook exploring subdaily sentek data
    * Sentek_processing.ipynb: jupyter notebook processing different data types, focusing on Sentek data
* Data:
    * final_processed_data: directory containing soil moisture data processed using Simone's calibration curves and weather data processed into the same format
    * all other directories contain licor or flux tower data for each site or SILO
 
* QA/QC flag defitions for Quality_flags:
    * (0) no flag
    * (1) settling period for instrumentation, 1-2 years at select sites that don't look right at start of record
    * (2) year 2 leaf litter cover over instrumentation at GG1
    * (3) moisture increase is substantially too high relative to incoming precipitation. Specifically, daily moisture increase exceeds rainfall in surrounding 3 days by more than 20%, and moisture increase greater than 20 mm
* QA/QC flag definitions for column-specific subdaily data:
    * (0) data meet quality standards for subdaily data usage (no increases during daytime hours when not raining)
    * (-1) data not evaluated--includes unacceptable subdaily data and rainy days
