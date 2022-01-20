# Social Mobility Data Specification

This file describes the necessary data speciffication in order to build the Social Mobility database. It describes the necessary variables that need to be populated in the master dataset and gives examples of valid input values. 

The information in this file is a work-in-progress. If you have a suggestion or if you find a mistake, please raise an issue in the repo.

## 1. Remains file (`remains.csv`)
This data file stores biological information for any individual found at a location site. It should only store strictly biological information that relate to the physical remains of any individual body found and studied.

Variable type | Variable name | Description | Example 
--------------| ------------- | ------------| ---------- 
String        | `individual_id`  | Unique ID that identifies the remains of an individual | `VLIT-0057`
String        | `gender` | The gender of an individual | `F`
String       | `age`   | The estimated age of an individual at the time of death | `30-50`
String      | `bones`  | Name analyzed bone(s) of the individual | `rib (L)`
String      | `teeth`  | Name analyzed tooth/teeth of the individual | `canine (L)`



Notes:

- The `gender` variable is not always available with certainty. This data field should only be populated with the values `F` for female, `M` for male and `LF` for likely female, `LM` for likely male and `U` for unidentified.
- The `age` variable is not always available with certainty. In the cases where only descriptive information is available, the information from the age breakdown table should be used. For example, if only given the value of `young adult` the `age` value should be `20-35`.
 

## 2. Objects file (`objects.csv`)
This data file stores non-biological information for any individual found at a location site. It should only store information about objects found with the individual or other relevant information that can indicate any social-economic information about the individual studied.
Variable type | Variable name | Description | Example 
--------------| ------------- | ------------| ---------- 
String        | `individual_id`  | Unique ID that identifies the remains of an individual | `VLIT-0057`
Integer        | `object_id`  | Number of object for individual | `1`
String        | `object_name` | Name of the object | `knife`

Notes:

- The `object_id` variable should be different for each object found with the individual body. For example, if an individual was found with a `fork` and a `knife`, there should be two rows in the dataset with the same `individual_id` but different `object_id` (in this case `1` and `2`) and different object names. 

## 3. Location file (`location.csv`)
This data file stores information about the location of where the individual remains were found.

Variable type | Variable name | Description | Example 
--------------| ------------- | ------------| ---------- 
String        | `location_id`  | Unique ID that identifies the location | `ITA-1233`
String        | `country_code`  | ISO3 country code of the location | `ITA`
String        | `location_name` | Name of the location the remains were discovered | `Velia`
String       | `site_name`   | Name of the site of where the remains were discovered | `Necropoli di Porta Marina Sud`
Float       | `location_bb_ur_lat`   | Upper-right latitude of location bounding box | `10.111`
Float       | `location_bb_ur_lon`   | Upper-right longitude of location bounding box | `10.111`
Float       | `location_bb_ll_lat`   | Lower-left latitude of location bounding box | `10.111`
Float       | `location_bb_ll_lon`   | Lower-left longitude of location bounding box | `10.111`
Float       | `site_lat`   | Latitude of archeological site | `10.111`
Float       | `site_lon`   | Longitude of archeological site | `10.111`


## 4. Date file (```date.csv```)
This data file stores information about time-related information on the individual. The most relevant information in this file is the estimated time an individual lived. Other important information is the time the remains were found.

Variable type | Variable name | Description | Example 
--------------| ------------- | ------------| ---------- 
String        | `date_id`  | Unique ID that identifies the date | `EUR7C`
String        | `date_string`  | The string of the date | `7th century CE`
Integer        | `date_start` | Start year of the date string | `601`
Integer       | `date_end`   | End year of the date string | `700`

## 5. Master file (`master.csv`)
This data file combines all the information from the files above and stores it as a master data file. This is the main database of the project. All the information in this file should be directly fed from the `object.csv`, `location.csv` and `date.csv` files.