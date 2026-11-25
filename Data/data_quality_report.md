# Data Quality Report – Water For People Rwanda 2021

## 1. Purpose

This report documents the initial data-quality inspection of the Water For People Rwanda 2021 dataset before it is imported into Oracle Database 21c.

## 2. Dataset Overview


- Original dataset: Water For People Rwanda 2021.
- Original data rows: 2,062.
- Number of columns: 39.
- Records with non-empty Unique IDs: 2,061.
- Records with missing Unique IDs: 1.
- Duplicate non-empty Unique IDs: 0.
- Records with latitude and longitude: 2,061.
- Records with missing latitude and longitude: 1.

All figures describe the original dataset before cleaning. No records have been removed from the original workbook.

## 3. Initial Data Quality Findings

### 3.1 Missing Identification and Location Information

The initial inspection identified one row with missing values in the following fields:

- Unique ID
- Latitude
- Longitude
- Date
- Geographical location fields

The row also contains several "No Data" values.

This record has been flagged for further investigation. It remains in the original dataset and will be handled during the data-cleaning stage in Phase IV.
### 3.2 Duplicate Records

The original dataset was checked for duplicate records using two methods:

- Duplicate non-empty Unique IDs: 0.
- Completely duplicated rows across all columns: 0.

No duplicate records were identified during the initial inspection.

### 3.3 Missing Values

The original workbook was inspected for blank cells across its 39 columns and 2,062 records.

The following columns contain blank values:

| Column | Blank values |
|---|---:|
| Tech Type UnImproved | 2,057 |
| Handpump flow rate | 1,690 |
| Number of times broken | 1,488 |
| Number of days broken | 1,488 |
| Liters per person per day | 781 |
| Seconds to fill 20 liters | 409 |
| E. Coli Meets Standard | 382 |
| Bacteria Meets Standard | 382 |
| Residual Chlorine Meets Standard | 382 |
| Other Contaminant Meets Standard | 382 |
| Water available on visit day | 81 |
| Users meet standards | 81 |
| Water source protected | 81 |
| Water quality meets standards | 81 |
| Out of service for one day or less | 81 |
| Water quantity meets standards | 81 |
| Overall condition and functioning | 81 |
| Functionality status | 77 |
| Other contaminant description | 38 |
| Elevation | 15 |
| Out of service or broken | 6 |
| Piped or handpump | 5 |
| Tech Type Improved | 5 |
| Improved water point indicator | 4 |

The following fields each contain one blank value: Instance ID, Date, Unique ID, Latitude, Longitude, # of Users, and Geo Level 1 through Geo Level 7.

Some blank values may be expected because certain fields apply only to particular water-point technologies or assessment conditions. For example, handpump flow rate does not apply to every water point.

The blank-value counts describe the original workbook. No missing values have been filled or corrected.

### 3.4 Geographical Information

The original dataset contains water-point records from three districts:

| District | Number of records |
|---|---:|
| Gicumbi | 860 |
| Rulindo | 624 |
| Kicukiro | 577 |
| Missing district information | 1 |
| **Total** | **2,062** |

The geographical counts are initial observations from the original dataset. No geographical information has been modified.
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
## Functionality Status

The original dataset contained the following functionality values:

| Functionality Status | Number of Records |
|---|---:|
| Yes | 1,958 |
| N/A | 77 |
| No Data | 27 |
| **Total** | **2,062** |

These counts are from the original dataset before excluding the one incomplete record.
## 6. Conclusion

The dataset provides useful information about public water points in Rwanda. However, some records and fields require further examination before database import.

The original dataset will be preserved, and any cleaning decisions will be documented to maintain data accuracy and traceability.

## Cleaning Summary

The original dataset was inspected in Microsoft Excel. One incomplete record was identified with missing identification, date and geographical information.

No records have been removed or modified in the original workbook. A separate working copy was previously created for future cleaning activities.

The original dataset contains 2,062 rows, including the incomplete record.

**Current status:** Initial data-quality inspection completed. Data cleaning and Oracle import are pending Phase IV.
