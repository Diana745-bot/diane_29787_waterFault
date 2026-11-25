# Dataset Card – Public Water Fault Tracking System

## 1. Dataset Information

- **Dataset name:** Water For People_Rwanda_2021
- **Source organisation:** Water For People
- **Publisher:** Water Point Data Exchange (WPdx)
- **Source link:** https://catalog.waterpointdata.org/datasets/wfp-rwanda-621f8339/index.html
- **Geographical coverage:** Rwanda
- **Data collection period:** 3 January 2015 – 19 June 2021
- **File format:** Microsoft Excel (.xlsx)
- **Number of columns:** 39
- **Number of data rows:** 2,062
- **Licence:** The specific licence for this downloaded dataset has not been confirmed in the catalogue. It should be verified with WPdx before redistribution.
- **Date downloaded:** [Enter the actual date you downloaded the file]
- **File size:** [Enter the file size from your computer]
- **Date downloaded:** 19 November 2026
- **File size:** 498 KB

## 2. What One Record Represents

Each record represents an individual water-point observation. It contains information such as the water point's location, technology, functionality, service level and other reported characteristics.

## 3. Dataset Purpose

This dataset will provide baseline information about public water points in Rwanda for the Public Water Fault Tracking System. It will help populate the water-point records in the proposed database.

The dataset does not provide the complete history of fault reports, repair assignments or maintenance activities. Those records will be managed separately by the proposed system.

## 4. Data Quality Findings

The downloaded workbook contains 2,062 data rows and 39 columns.

Initial observations include:

- 2,061 records have a non-empty Unique ID.
- 1 record has a missing Unique ID.
- 2,061 records have latitude and longitude values.
- 1 record has missing location coordinates and date information.
- No duplicate non-empty Unique IDs were identified.
- Functionality values include:
  - Yes: 1,958
  - N/A: 77
  - No Data: 27

The WPdx catalogue reports 2,057 valid rows out of 2,062 processed rows. It also reports 4 records with missing water technology or source information and 77 validation issues involving N/A values in two boolean fields.

These findings are recorded for the later cleaning stage. The original dataset has not been modified.

## 5. Limitations

- The dataset covers observations collected between 2015 and 2021.
- It does not provide a complete history of water-point faults and repairs.
- Some records contain missing or incomplete information.
- The dataset represents reported observations and may not reflect the current condition of every water point.

## 6. Intended Use

The dataset will be used as the initial source for identifying water points and designing the relational database tables. Data cleaning and transformation will be documented during Phase IV.
