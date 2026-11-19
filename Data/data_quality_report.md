# Data Quality Report – Water For People Rwanda 2021

## 1. Purpose

This report documents the initial data-quality inspection of the Water For People Rwanda 2021 dataset before it is imported into Oracle Database 21c.

## 2. Dataset Overview

- Dataset: Water For People_Rwanda_2021
- Worksheet inspected: Transformed Data
- Total rows: 2,062
- Total columns: 39
- Records with a Unique ID: 2,061
- Records with both latitude and longitude: 2,061

## 3. Initial Data Quality Findings

### 3.1 Missing Identification and Location Information

One row has missing values for its Unique ID, latitude, longitude, date and geographical location fields. This row also contains several "No Data" values.

This record requires investigation and should not be imported as a normal water-point record.

### 3.2 Duplicate Records

The inspection found no duplicate non-empty values in the Unique ID column.

### 3.3 Missing Values

Some columns contain missing values. Examples include:

- Technology type for unimproved water points.
- Handpump flow rate.
- Piped water quantity per person.
- Water quality measurements.
- Breakdown frequency and duration.

Some missing values may be expected because certain fields apply only to specific water-point technologies.

### 3.4 Geographical Information

The dataset contains records from three districts:

- Gicumbi: 860 records
- Rulindo: 624 records
- Kicukiro: 577 records

One additional row has no district information.

### 3.5 Date Format

The Date column contains Excel date serial values. These must be converted into proper date values before importing the records into Oracle Database 21c.

## 4. Dataset Record Count Difference

The workbook contains 2,062 rows, including one row without a Unique ID.

The WPdx catalogue describes 2,057 valid Rwanda records. Therefore, the workbook contains four more identified records than the catalogue's stated valid-record count.

The reason for this difference has not yet been established and requires further investigation.

## 5. Planned Data Cleaning Activities

Before importing the dataset, the following activities will be performed:

1. Investigate the row with missing identification and location information.
2. Check the four-record difference against the catalogue description.
3. Verify latitude and longitude values.
4. Convert Excel date values into Oracle-compatible dates.
5. Review missing values and distinguish expected blanks from problematic records.
6. Check technology and functionality values for consistency.
7. Preserve the original Excel dataset unchanged.

## 6. Conclusion

The dataset provides useful information about public water points in Rwanda. However, some records and fields require further examination before database import.

The original dataset will be preserved, and any cleaning decisions will be documented to maintain data accuracy and traceability.

**Current status:** Initial inspection completed. Data cleaning and Oracle import are pending.
