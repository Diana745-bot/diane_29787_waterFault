# Water Points Field Mapping

## 1. Purpose

This document maps the columns from the Water For People Rwanda 2021 dataset to the proposed WATER_POINTS table in the Public Water Fault Tracking System.

The mapping will guide data preparation and import into Oracle Database 21c.

## 2. Proposed Field Mapping

The following table maps the main identification, geographical and measurement fields from the original Excel dataset to the proposed normalized database structure.

| Proposed Target Table | Proposed Field | Exact Excel Source Column | Description |
|---|---|---|---|
| WATER_POINTS | WATER_POINT_ID | Unique ID | Identifier of the water-point record |
| WATER_POINTS | INSTANCE_ID | Instance Id | Original survey instance identifier |
| WATER_POINTS | RECORD_DATE | Date | Date associated with the survey record |
| DISTRICTS | COUNTRY_NAME | Geo Level 1 | Country name |
| DISTRICTS | DISTRICT_NAME | Geo Level 2 | District name |
| SECTORS | SECTOR_NAME | Geo Level 3 | Sector name |
| WATER_POINTS | CELL_NAME | Geo Level 4 | Cell name |
| WATER_POINTS | VILLAGE_NAME | Geo Level 5 | Village name |
| WATER_POINTS | GEO_LEVEL_6 | Geo Level 6 | Additional geographical level; meaning to be confirmed |
| WATER_POINTS | GEO_LEVEL_7 | Geo Level 7 | Additional geographical level; meaning to be confirmed |
| WATER_POINTS | LATITUDE | Latitude | Geographic latitude |
| WATER_POINTS | LONGITUDE | Longitude | Geographic longitude |
| WATER_POINTS | ELEVATION | Elevation | Water-point elevation |
| WATER_POINTS | NUMBER_OF_USERS | # of Users | Number of people using the water point |
| WATER_POINTS | SERVICE_LEVEL | Level Of Service  | Reported service level |
| WATER_POINTS | SERVICE_LEVEL_SCORE | Level Of Service Score | Numerical service-level score |
| WATER_POINTS | SOURCE_PROTECTED | Water Point Source is Protected | Indicates source protection |
| WATER_POINTS | IMPROVED_WATER_POINT | Has Improved Water Point (1)\n1 = improved\nN/A = not improved\n(Do this manually by water point type) | Indicates whether the water point is classified as improved |
| WATER_POINTS | TECHNOLOGY_IMPROVED | Tech Type Improved | Improved water-point technology |
| WATER_POINTS | TECHNOLOGY_UNIMPROVED | Tech Type UnImproved | Unimproved water-point technology |
| WATER_POINTS | IS_FUNCTIONAL | Water point is Functional or not greater than 3 months without service | Indicates reported functionality |
| WATER_POINTS | USERS_MEET_STANDARDS | # of Users Meets Standards (1) | Indicates whether the number of users meets the standard |
| WATER_POINTS | IS_OUT_OF_SERVICE_OR_BROKEN | Water Point/System Out Of Service Or Broken? | Indicates whether the water point is broken or out of service |
| WATER_POINTS | BREAKAGE_FREQUENCY_MEETS_STANDARD | Water Point/System Number Of Times Broken Is Equal to Oncer Per Month or Less  | Indicates whether breakage frequency meets the stated standard |
| WATER_POINTS | BREAKAGE_DURATION_MEETS_STANDARD | Water Point/System Number  Of Days Broken Is One Day Or Less | Indicates whether the number of days broken meets the stated standard |
| WATER_POINTS | OUT_OF_SERVICE_WITHIN_STANDARD | Water Point/ System Out Of Service For One Day Or Less Per Month In The Last Year | Indicates whether the water point meets the stated service interruption standard |
| WATER_POINTS | WATER_AVAILABLE_ON_VISIT | Water Is Available On The Day Of The Visit (1) | Indicates whether water was available during the visit |
| WATER_POINTS | SECONDS_TO_FILL_20L | Seconds to fill 20 liters | Time required to fill a 20-litre container |
| WATER_POINTS | HANDPUMP_FLOW_RATE | FOR HANDPUMPS ONLY \nHandpump flow rate in L/s | Flow rate for handpump water points |
| WATER_POINTS | LITERS_PER_PERSON_PER_DAY | FOR PIPED ONLY \nLiters per person per day | Daily water quantity per person for piped systems |
| WATER_POINTS | QUANTITY_MEETS_STANDARD | Quantity Of Water Available Meets Standards (1) | Indicates whether available water quantity meets the standard |
| WATER_POINTS | PIPED_OR_HANDPUMP | Piped or handpump? | Identifies the water-point system type |
| WATER_POINTS | ECOLI_MEETS_STANDARD | E Coli Meets Standard | Indicates whether E. coli meets the water-quality standard |
| WATER_POINTS | RESIDUAL_CHLORINE_MEETS_STANDARD | Residual Chlorine Meets Standard | Indicates whether residual chlorine meets the standard |
| WATER_POINTS | BACTERIA_MEETS_STANDARD | Bacteria Meets Standard | Indicates whether bacteria meets the standard |
| WATER_POINTS | OTHER_CONTAMINANT | Other contaminant of concern at Water Point? \nThis may be blank if there are no contaminants of concern, or may indicate turbidity, iron, arsenic, or fluoride | Records another contaminant of concern |
| WATER_POINTS | OTHER_CONTAMINANT_MEETS_STANDARD | Other Contaminant of Concern Meets Standard | Indicates whether the other contaminant meets the standard |
| WATER_POINTS | WATER_QUALITY_MEETS_STANDARD | Water Quality Meets Standards (1) (E-Coli, Bacteria, Residual  | Overall water-quality standards indicator |
| WATER_POINTS | OVERALL_CONDITION | Water Point/System In Good Overall Condition and Functioning | Indicates the overall condition and functionality of the water point |

## 3. Important Mapping Notes

- Geo Level 1 represents Rwanda.
- Geo Level 2 represents the district.
- Geo Level 3 represents the sector.
- Geo Level 4 represents the cell.
- Geo Level 5 represents the village.
- Technology information may appear in either the improved or unimproved technology column.
- Functionality values include Yes, N/A and No Data. These values must be handled carefully rather than automatically treating every value other than Yes as No.
- Some records contain missing values.

## 4. Data Transformation Rules

Before importing:

1. Use Unique ID as the proposed water-point identifier.
2. Check that identifiers are not missing or duplicated.
3. Convert the Excel Date values into valid Oracle DATE values.
4. Verify geographical coordinates.
5. Combine the improved and unimproved technology fields appropriately.
6. Preserve unknown functionality values instead of assuming they mean non-functional.
7. Review missing district and location information.

## 5. Import Status

The field mapping is a proposed design. The final Oracle table structure and data types will be confirmed during database design.

**Current status:** Mapping documented; data transformation and Oracle import are pending.

