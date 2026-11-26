# Data Normalization – Public Water Fault Tracking System

## 1. Purpose

This document explains how the original Water For People Rwanda 2021 dataset is examined and organized into relational tables for the Public Water Fault Tracking System.

The normalization process will show the transformation from Unnormalized Form (UNF) to First Normal Form (1NF), Second Normal Form (2NF), and Third Normal Form (3NF).

The objective is to reduce unnecessary data duplication, improve data consistency, and establish a logical database structure before implementation in Oracle Database 21c.

## 2. Source Dataset

The normalization exercise uses the original Water For People Rwanda 2021 dataset.

- **Source:** Water Point Data Exchange (WPdx)
- **Dataset:** Water For People_Rwanda_2021
- **Format:** Excel (.xlsx)
- **Original records:** 2,062
- **Columns:** 39
- **Record meaning:** One water-point observation.

The original dataset is preserved in the `data/raw/` folder. No records have been removed or modified during the initial inspection.
## 3. Unnormalized Form (UNF)

The original Excel dataset is treated as the starting point for the normalization process. Each row represents one water-point observation and contains identification, geographical, technology, functionality and water-quality information.

At this stage, the original columns are kept together in one dataset without separating them into related database tables.

Examples of fields in the original dataset include:

- `Unique ID`
- `Instance Id`
- `Date`
- `Latitude`
- `Longitude`
- `Geo Level 1`
- `Geo Level 2`
- `Geo Level 3`
- `Tech Type Improved`
- `Water point is Functional or not greater than 3 months without service`
- `# of Users`
- `Water Quality Meets Standards (1) (E-Coli, Bacteria, Residual`

The original dataset contains 2,062 rows and 39 columns. It is retained as the UNF starting point for this exercise.
### 3.1 Sample Records from the Original Dataset

The following three examples are taken from the original `Transformed Data` worksheet. They show how water-point information appears together before normalization.

| Unique ID | District | Sector | Cell | Village | Water Point Type | Functionality | Number of Users |
|---|---|---|---|---|---|---|---:|
| Gicumbisurveysgp1-3FB72Q | Gicumbi | Miyove | Mubuga | Kirwa | Protected Spring | Yes | 50 |
| Gicumbisurveysgp5-3FBBHQ | Gicumbi | Ruvune | Cyandaro | Nyankokoma | Protected Spring | Yes | 200 |
| Gicumbisurveysgp5-3FBDDC | Gicumbi | Ruvune | Rebero | Rwamiko | Protected Spring | Yes | 312 |

These examples show that identification, geographical, technology and functionality information is stored together in the original dataset.
### 3.1 Sample Records in UNF

The following are three sample records taken from the original Excel dataset before normalization.

| Unique ID | Geo Level 2 | Geo Level 3 | Geo Level 4 | Geo Level 5 | Tech Type Improved | # of Users |
|---|---|---|---|---|---|---:|
| Gicumbisurveysgp1-3FB72Q | Gicumbi | Miyove | Mubuga | Kirwa | Protected Spring | 50 |
| Gicumbisurveysgp5-3FBBHQ | Gicumbi | Ruvune | Cyandaro | Nyankokoma | Protected Spring | 200 |
| Gicumbisurveysgp5-3FBDDC | Gicumbi | Ruvune | Rebero | Rwamiko | Protected Spring | 312 |

These records remain together in the original source dataset at the starting stage of normalization.
## 4. First Normal Form (1NF)

A table is in First Normal Form when:

- Each column contains a single value.
- Each row represents one record.
- There are no repeating groups or lists stored in a single field.
- Each record can be uniquely identified.

For this project, each row represents one water-point observation. The `Unique ID` field is intended to identify each water-point record.

During the initial inspection, 2,061 records had a non-empty Unique ID, while one record had a missing Unique ID. No duplicate non-empty Unique IDs were found.

The original dataset will be checked for fields containing multiple values or repeating groups. Any necessary separation will be documented before the final 1NF structure is confirmed.

**Dependency removed:** Repeating groups or multiple values within a single field must be separated so that each field stores one value.
### 4.1 Sample Records in 1NF

The following records demonstrate the atomic values in the original dataset after checking the 1NF requirements.

| Unique ID | Geo Level 2 | Geo Level 3 | Geo Level 4 | Geo Level 5 | Tech Type Improved | Water point is Functional or not greater than 3 months without service | # of Users |
|---|---|---|---|---|---|---|---:|
| Gicumbisurveysgp1-3FB72Q | Gicumbi | Miyove | Mubuga | Kirwa | Protected Spring | Yes | 50 |
| Gicumbisurveysgp5-3FBBHQ | Gicumbi | Ruvune | Cyandaro | Nyankokoma | Protected Spring | Yes | 200 |
| Gicumbisurveysgp5-3FBDDC | Gicumbi | Ruvune | Rebero | Rwamiko | Protected Spring | Yes | 312 |

Each row represents one water-point observation. The selected fields contain individual values rather than lists or repeating groups.

The original dataset therefore requires no split for these fields to satisfy 1NF. The incomplete record with a missing Unique ID remains flagged for investigation; it has not been deleted.

**Result:** The selected records satisfy the atomic-value and one-record-per-row requirements of 1NF.
## 5. Second Normal Form (2NF)

A table is in Second Normal Form when:

- It is already in First Normal Form.
- Every non-key attribute depends on the whole primary key.
- There are no partial dependencies.

In this dataset, the `Unique ID` field is intended to identify each water-point record. Because this is a single-column key rather than a composite key, partial dependencies cannot occur.

Because `Unique ID` is a single-column key, there are no partial dependencies to remove. Therefore, no table split is required to achieve 2NF at this stage. The water-point attributes remain associated with their identifying record.

**Dependency removed:** No partial dependency was identified because the intended primary key consists of a single attribute. No decomposition was necessary for this step.


The following records show the water-point information using `Unique ID` as the intended primary key.

| Unique ID | Geo Level 2 | Geo Level 3 | Geo Level 4 | Geo Level 5 | Tech Type Improved | Water point is Functional or not greater than 3 months without service | # of Users |
|---|---|---|---|---|---|---|---:|
| Gicumbisurveysgp1-3FB72Q | Gicumbi | Miyove | Mubuga | Kirwa | Protected Spring | Yes | 50 |
| Gicumbisurveysgp5-3FBBHQ | Gicumbi | Ruvune | Cyandaro | Nyankokoma | Protected Spring | Yes | 200 |
| Gicumbisurveysgp5-3FBDDC | Gicumbi | Ruvune | Rebero | Rwamiko | Protected Spring | Yes | 312 |

The selected records use a single-column key, `Unique ID`. Therefore, there are no partial dependencies to remove because partial dependencies occur when a table has a composite key and a non-key attribute depends on only part of that key.

**Result:** No additional table split is required to remove partial dependencies at this stage.
## 6. Third Normal Form (3NF)

A table is in Third Normal Form when:

- It is already in Second Normal Form.
- Every non-key attribute depends directly on the primary key.
- There are no transitive dependencies.

For the Public Water Fault Tracking System, the logical design separates the following information:

### 6.1 Administrative Locations

### 6.1 Administrative Locations

The original dataset contains geographical information in the columns `Geo Level 1` through `Geo Level 7`.

For the proposed logical design, the geographical information is organized into separate DISTRICTS and SECTORS tables.

- DISTRICTS stores district names and country information.
- SECTORS stores sector names and references the district to which each sector belongs.
- WATER_POINTS references SECTORS through `SECTOR_ID`.

For example, the original dataset contains water points in the Gicumbi district, including Miyove and Ruvune sectors.

This structure avoids repeatedly storing district information for every water point.

**Dependency removed:** District information is separated from water-point records because it can be determined through the associated sector. This removes the transitive dependency from the proposed water-point structure.
### 6.2 Fault Information

The original Water For People Rwanda 2021 dataset does not contain a complete fault-reporting history or a fault-category management structure.

The proposed system introduces two related tables:

- FAULT_TYPES stores fault categories and their descriptions.
- FAULT_REPORTS stores individual fault reports and references the relevant fault type through `FAULT_TYPE_ID`.

This prevents fault-category descriptions from being repeated in every fault report.

**Dependency removed:** Fault-type descriptions are stored in FAULT_TYPES and referenced by FAULT_REPORTS, rather than being repeatedly stored in fault-report records.
### 6.3 Maintenance Information

The original dataset does not contain maintenance-team records, repair assignments, repair activities or maintenance-cost transactions.

These are additional tables proposed for the Public Water Fault Tracking System:

- MAINTENANCE_TEAMS stores maintenance-team information.
- TEAM_MEMBERS stores individual members and references their team.
- REPAIR_ASSIGNMENTS connects fault reports to maintenance teams.
- REPAIR_ACTIVITIES records work performed under each assignment.
- MAINTENANCE_COSTS records expenses associated with repair assignments.

Separating these records makes it easier to track teams, assignments, repair progress and maintenance expenses.

**Dependency removed:** Team information is stored once in MAINTENANCE_TEAMS and referenced by TEAM_MEMBERS and REPAIR_ASSIGNMENTS, avoiding repeated team details.

### 6.4 Result of 3NF

The proposed logical database design separates information into related tables to reduce unnecessary duplication and improve data consistency.

The geographical tables organize district, sector and water-point information. The fault-reporting tables organize reporters, fault types, reports and inspections. The maintenance tables organize teams, team members, repair assignments, activities and costs.

The original Excel dataset provides the baseline water-point information, while the additional tables support the new reporting and maintenance functions of the proposed system.

The logical design uses primary keys to identify records and foreign keys to connect related tables.

**Dependency removed:** Descriptive information that depends on another entity is stored in its own table and referenced through a foreign key.

### 6.5 Sample Records in 3NF

The following examples demonstrate how geographical and water-point information from the original dataset can be organized into related tables.

**DISTRICTS**

| DISTRICT_ID (PK) | DISTRICT_NAME | COUNTRY_NAME |
|---:|---|---|
| 1 | Gicumbi | Rwanda |

**SECTORS**

| SECTOR_ID (PK) | DISTRICT_ID (FK) | SECTOR_NAME |
|---:|---:|---|
| 101 | 1 | Miyove |
| 102 | 1 | Ruvune |

**WATER_POINTS**

| WATER_POINT_ID (PK) | SECTOR_ID (FK) | CELL_NAME | VILLAGE_NAME | TECHNOLOGY_IMPROVED | IS_FUNCTIONAL | NUMBER_OF_USERS |
|---|---:|---|---|---|---|---:|
| Gicumbisurveysgp1-3FB72Q | 101 | Mubuga | Kirwa | Protected Spring | Yes | 50 |
| Gicumbisurveysgp5-3FBBHQ | 102 | Cyandaro | Nyankokoma | Protected Spring | Yes | 200 |
| Gicumbisurveysgp5-3FBDDC | 102 | Rebero | Rwamiko | Protected Spring | Yes | 312 |

The water-point values are taken from the original dataset. The district and sector identifiers shown above are illustrative generated identifiers used to demonstrate the proposed relationships.

The geographical labels are interpreted from the corresponding Geo Level columns and will be confirmed during field mapping.

**Dependency removed:** District information is stored once in DISTRICTS, and each sector references its district using DISTRICT_ID. Each water point references its sector using SECTOR_ID, reducing repeated geographical information.
### 6.6 Source Data and Proposed System Tables

The original Water For People Rwanda 2021 dataset provides water-point observations, including geographical location, technology, functionality and water-quality information.

The tables DISTRICTS, SECTORS and WATER_POINTS organize information derived from the source dataset.

The remaining tables, including FAULT_REPORTS, INSPECTIONS, MAINTENANCE_TEAMS, REPAIR_ASSIGNMENTS, REPAIR_ACTIVITIES and MAINTENANCE_COSTS, are proposed system tables. Their records will be created when users report faults and maintenance activities are managed.

These proposed tables extend the original dataset to support the objectives of the Public Water Fault Tracking System.
