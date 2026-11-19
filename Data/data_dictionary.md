# Data Dictionary – Water For People Rwanda 2021

## 1. Dataset Overview

- **Dataset:** Water For People_Rwanda_2021
- **Source:** Water Point Data Exchange (WPdx)
- **Main worksheet:** Transformed Data
- **Total records:** 2,062 data rows
- **Total columns:** 39
- **File:** water_for_people_rwanda_2021.xlsx

The dataset contains information about water-point identification, geographical location, technology, functionality, water availability and service quality.

## 2. Column Descriptions

### A. Identification and Location

| Column | Description |
|---|---|
| Instance Id | Survey record identifier |
| Date | Date associated with the record |
| Unique ID | Unique identifier assigned to the water-point record |
| Latitude | Geographic latitude |
| Longitude | Geographic longitude |
| Elevation | Elevation of the water point |
| Geo Level 1–7 | Administrative or geographical location levels |

### B. Water Point and Technology

| Column | Description |
|---|---|
| Level Of Service Score | Numerical service-level score |
| Level Of Service | Description of the service level |
| Has Improved Water Point | Indicates whether the water point is classified as improved |
| Tech Type Improved | Type of improved water technology |
| Tech Type UnImproved | Type of unimproved water technology |
| Water point is Functional | Indicates reported functionality |
| Water Point Source is Protected | Indicates whether the source is protected |
| # of Users | Number of people using the water point |
| # of Users Meets Standards | Indicates whether the number of users meets standards |

### C. Breakdown and Availability

| Column | Description |
|---|---|
| Water Point/System Out Of Service Or Broken? | Indicates whether the system is out of service or broken |
| Number Of Times Broken | Records breakdown frequency |
| Number Of Days Broken | Records breakdown duration |
| Out Of Service For One Day Or Less | Indicates the reported service interruption period |
| Water Is Available On The Day Of The Visit | Indicates water availability during the visit |
| Seconds to fill 20 liters | Time recorded to fill 20 litres |
| Piped or handpump? | Identifies the water delivery technology |
| Handpump flow rate | Recorded handpump flow information |
| Liters per person per day | Recorded water quantity per person |
| Quantity Of Water Available Meets Standards | Indicates whether water quantity meets standards |

### D. Water Quality and Overall Condition

| Column | Description |
|---|---|
| E Coli Meets Standard | Indicates whether E. coli meets the standard |
| Residual Chlorine Meets Standard | Indicates whether residual chlorine meets the standard |
| Bacteria Meets Standard | Indicates whether bacteria meets the standard |
| Other contaminant of concern | Records other possible contaminants |
| Other Contaminant of Concern Meets Standard | Indicates whether other contaminants meet standards |
| Water Quality Meets Standards | Overall water-quality assessment |
| Water Point/System In Good Overall Condition and Functioning | Indicates the overall condition and functioning status |

## 3. Initial Data Quality Observations

The initial inspection identified:

- 2,062 data rows in the main worksheet.
- 39 columns.
- 2,061 non-empty Unique IDs.
- No duplicate non-empty Unique IDs.
- 2,061 records with both latitude and longitude.
- Some fields contain missing values.

The dataset includes records from Gicumbi, Rulindo and Kicukiro.

## 4. Planned Use in the Project

The dataset will provide initial information for the WATER_POINTS table, including:

- Water-point identifiers.
- Geographic coordinates.
- Administrative locations.
- Technology types.
- Functionality information.
- Number of users.

Fault reports, inspections, maintenance assignments, repair activities and costs will be maintained separately in the project database.

## 5. Data Preparation

Before importing the records into Oracle Database 21c, the dataset will be checked for:

1. Missing identifiers and important fields.
2. Invalid geographical coordinates.
3. Inconsistent technology and functionality values.
4. Appropriate date and numeric formats.
5. Duplicate records.

The original Excel file will be preserved as the source dataset.
