Gulf of Alaska
-------------------------------

**Source:** [NOAA Alaska Fisheries Science Center Groundfish Assessment Program surveys](https://apps-afsc.fisheries.noaa.gov/RACE/groundfish/survey_data/default.htm)

**Related papers:** 
- [Data Report: 2009 Gulf of Alaska Bottom Trawl Survey](https://archive.fisheries.noaa.gov/afsc/Publications/AFSC-TM/NOAA-TM-AFSC-208.pdf)
- [Groundfish Bottom Trawl Survey Protocols](https://www.fisheries.noaa.gov/resource/document/noaa-protocols-groundfish-bottom-trawl-surveys)

**How we process the data:**
- Some of the files contain extra headers in the data rows, so we remove any data rows that contain the word “LATITUDE” in the LATITUDE column.
- We create a haulid by combining a 3 digit leading zero vessel number with a 3 digit leading zero cruise number and a 3 digit leading zero haul number, separated by “-”, for example: (vessel-cruise-haul) 354-067-001.
- If wtcpue is recorded as “-9999”, we change the value to NA.
- We remove any SCIENTIFIC spp values that contain the word “egg” or where the only value in the SCIENTIFIC field is white space.
- Any values SCIENTIFIC values that contain the word “Lepidopsetta” are changed to “Lepidopsetta sp.” because more than one genus/spp combo was used to describe the same organism over time. This also holds true for Myoxocephalus sp. excluding scorpius and Bathyraja sp. excluding panthera.
- We group the data by haulid, stratum, stratumarea, year, lat, lon, depth, and spp and then sum up all of the wtcpue values for each group and reassign that as the wtcpue.

**What the raw data includes:**
The current files of raw data for the Gulf of Alaska are goa_strata.csv, goa1984_1987.csv, goa1990_1999.csv, goa2001_2005.csv, goa2007_2013.csv, goa2015_2019.csv.

**goa_strata.csv is constant through the years with the column definitions:**
| attributeName                  | attributeDefinition   | col_classes             | unit |       
|--------------------------|----------------|----------------------------|-----------------------------------------------------------|
|NPFMCArea	|North Pacific Fisheries Management Council (NPFMC) area name |	character	|dimensionless
|SubareaDesription | NPFMC subarea name |	character	|dimensionless
|StratumCode |	a numeric character code asigned to each unique stratum, matches STRATUM column in bio dataset |	character	|dimensionless
|DepthIntervalm |	The depth interval of the stratum in 100 meter increments |	character	| meter
|Areakm2 |	The area of the stratum in square kilometers |	numeric | square kilometer

**The remaining files are trawl data files, data added annually, with the column definitions:**

| attributeName                  | attributeDefinition   | col_classes             | unit |       
|--------------------------|----------------|----------------------------|-----------------------------------------------------------|
|LATITUDE	|The latitude (decimal degrees) at the start of the haul|	numeric	|degree
|LONGITUDE |	The longitude (decimal degrees) at the start of the haul|	numeric	|degree
|STATION|Unique sequential order in which stations have been completed. Hangups and short tows each receive a non-repeated consecutive number.|character |dimensionless
|STRATUM	|NA	|character	|dimensionless
|YEAR	|a 4 digit string containing the year of the survey	|character	|dimensionless
|DATETIME	|This is the date and time at the beginning of the haul; This is the date and time at the beginning of the haul; For groundfish trawl data, this is the on-bottom time which is determined after we have looked at the bottom-contact sensor and net-mensuration plots.	|character	|dimensionless
|WTCPUE	|Catch weight per area the net swept in KG/HA.|	numeric	|kilogramsPerHectare
|NUMCPUE	|Catch number per area the net swept in number/HA.	|numeric	|dimensionless
|COMMON |	The common name of the marine organism associated with the SCIENTIFIC_NAME	|character|	dimensionless
|SCIENTIFIC	|The scientific name of the organism associated with the COMMON_NAME.	|character	|dimensionless
|SID	|Domain: [RACE Species Codebook](http://www.afsc.noaa.gov/RACE/groundfish/species_codebook.pdf)	|numeric	|dimensionless
|BOT_DEPTH	|Weighted average depth (m) and is calculated by adding GEAR_DEPTH to NET_HEIGHT. Prior to (year), before NET_HEIGHT was regularly measured, this value was obtained using either echosounder or bathythermograph.	|numeric	|meter
|BOT_TEMP	|Weighted average temperature (in tenths of a degree Celsius) measured at the maximum depth of the headrope of the trawl. Null values indicate temperature not recoreded.	|numeric	|celsius
|SURF_TEMP	|Weighted average temperature (in tenths of a degree Celsius) measured at the sea surface of the trawl. Null values indicate temperature not recoreded.	|numeric	|celsius
|CRUISE	|This is a six-digit number identifying the Cruise number. It is of the form: YYYY99 (where YYYY = year of the cruise; 99 = 2-digit number and is sequential; 01 denotes the first cruise that vessel made in this year, 02 is the second, etc.)|	character	|dimensionless
|HAUL	|This number uniquely identifies a haul within a cruise. It is a sequential number, in chronological order of occurrence.	|numeric	|dimensionless

The Ecological Metadata Language file can be accessed [here](https://github.com/pinskylab/OceanAdapt/blob/new_canada_2019/metaData/goa/goa.xml)