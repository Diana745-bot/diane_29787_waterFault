# Water Points Field Mapping

## 1. Purpose

This document maps the columns from the Water For People Rwanda 2021 dataset to the proposed WATER_POINTS table in the Public Water Fault Tracking System.

The mapping will guide data preparation and import into Oracle Database 21c.

## 2. Proposed Field Mapping

| Proposed Oracle Field | Excel Source Column | Description |
|---|---|---|
| WATER_POINT_ID | Unique ID | Identifier of the water-point record |
| INSTANCE_ID | Instance Id | Original survey instance identifier |
| RECORD_DATE | Date | Date associated with the survey record |
| COUNTRY_NAME | Geo Level 1 | Country |
| DISTRICT_NAME | Geo Level 2 | District |
| SECTOR_NAME | Geo Level 3 | Sector |
| CELL_NAME | Geo Level 4 | Cell |
| VILLAGE_NAME | Geo Level 5 | Village |
| LATITUDE | Latitude | Geographic latitude |
| LONGITUDE | Longitude | Geographic longitude |
| ELEVATION | Elevation | Water-point elevation |
| TECHNOLOGY_TYPE | Tech Type Improved / Tech Type UnImproved | Recorded water-point technology |
| FUNCTIONAL_STATUS | Water point is Functional or not greater than 3 months without service | Reported functionality |
| NUMBER_OF_USERS | # of Users | Number of people using the water point |
| SERVICE_LEVEL | Level Of Service | Reported service level |
| SOURCE_PROTECTED | Water Point Source is Protected | Indicates source protection |

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
