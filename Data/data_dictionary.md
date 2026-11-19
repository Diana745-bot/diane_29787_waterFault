# Data Dictionary – Public Water Fault Tracking System

## 1. Dataset Overview

- **Dataset name:** Water For People Rwanda 2021
- **Source:** Water Point Data Exchange (WPdx)
- **Original file:** `water_for_people_rwanda_2021.xlsx`
- **Cleaned file:** `water_for_people_rwanda_2021_cleaned.xlsx`
- **Main worksheet:** `Transformed Data`
- **Original data rows:** 2,062
- **Incomplete records excluded:** 1
- **Cleaned data rows:** 2,061
- **Total columns:** 39

The dataset contains information about water-point identification, geographical location, technology, functionality, water availability, service levels and water quality.

## 2. Column Descriptions

### A. Identification and Geographical Information

| Excel Column | Description |
|---|---|
| Instance Id | Original survey instance identifier |
| Date | Date associated with the survey record |
| Unique ID | Unique identifier assigned to the water point |
| Latitude | Geographic latitude of the water point |
| Longitude | Geographic longitude of the water point |
| Elevation | Elevation of the water point |
| Geo Level 1 | Country-level geographical information |
| Geo Level 2 | District-level geographical information |
| Geo Level 3 | Sector-level geographical information |
| Geo Level 4 | Cell-level geographical information |
| Geo Level 5 | Village-level geographical information |
| Geo Level 6 | Additional geographical information |
| Geo Level 7 | Additional geographical information |

### B. Service Level, Technology and Functionality

| Excel Column | Description |
|---|---|
| Level Of Service Score | Numerical service-level score |
| Level Of Service | Reported level of service |
| Has Improved Water Point (1) | Indicates whether the water point is classified as improved |
| Tech Type Improved | Recorded improved water technology |
| Tech Type UnImproved | Recorded unimproved water technology |
| Water point is Functional or not greater than 3 months without service | Reported functionality status |
| Water Point Source is Protected | Indicates whether the water source is protected |
| # of Users | Number of people using the water point |
| # of Users Meets Standards (1) | Indicates whether the number of users meets the applicable standard |

### C. Breakdowns and Water Availability

| Excel Column | Description |
|---|---|
| Water Point/System Out Of Service Or Broken? | Indicates whether the water point or system is broken or out of service |
| Water Point/System Number Of Times Broken Is Equal to Oncer Per Month or Less | Records whether breakdown frequency meets the stated condition |
| Water Point/System Number Of Days Broken Is One Day Or Less | Records whether the breakdown duration meets the stated condition |
| Water Point/ System Out Of Service For One Day Or Less Per Month In The Last Year | Records the reported duration of service interruptions |
| Water Is Available On The Day Of The Visit (1) | Indicates whether water was available during the visit |
| Seconds to fill 20 liters | Time required to fill 20 litres of water |
| Piped or handpump? | Identifies the water delivery type |
| FOR HANDPUMPS ONLY – Handpump flow rate in L/s | Recorded flow rate for handpumps |
| FOR PIPED ONLY – Liters per person per day | Recorded water quantity per person per day for piped systems |
| Quantity
