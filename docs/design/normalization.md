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

- Unique ID
- Water Point Name
- Date
- Latitude
- Longitude
- District
- Functionality Status
- Tech Type Improved
- Number of Users
- Water Quality Meets Standards

The original dataset contains 2,062 rows and 39 columns. It is retained as the UNF starting point for this exercise.
### 3.1 Sample Records from the Original Dataset

The following three examples are taken from the original `Transformed Data` worksheet. They show how water-point information appears together before normalization.

| Unique ID | District | Sector | Cell | Village | Water Point Type | Functionality | Number of Users |
|---|---|---|---|---|---|---|---:|
| Gicumbisurveysgp1-3FB72Q | Gicumbi | Miyove | Mubuga | Kirwa | Protected Spring | Yes | 50 |
| Gicumbisurveysgp5-3FBBHQ | Gicumbi | Ruvune | Cyandaro | Nyankokoma | Protected Spring | Yes | 200 |
| Gicumbisurveysgp5-3FBDDC | Gicumbi | Ruvune | Rebero | Rwamiko | Protected Spring | Yes | 312 |

These examples show that identification, geographical, technology and functionality information is stored together in the original dataset.
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
## 5. Second Normal Form (2NF)

A table is in Second Normal Form when:

- It is already in First Normal Form.
- Every non-key attribute depends on the whole primary key.
- There are no partial dependencies.

In this dataset, the `Unique ID` field is intended to identify each water-point record. Because this is a single-column key rather than a composite key, partial dependencies cannot occur.

Therefore, once the 1NF structure is confirmed and the missing Unique ID record is investigated, the water-point table satisfies the 2NF requirement without requiring a split to remove partial dependencies.

**Dependency removed:** No partial dependency was identified because the intended key consists of a single attribute.
## 6. Third Normal Form (3NF)

A table is in Third Normal Form when:

- It is already in Second Normal Form.
- Every non-key attribute depends directly on the primary key.
- There are no transitive dependencies.

For the Public Water Fault Tracking System, the logical design separates the following information:

### 6.1 Administrative Locations

The proposed design uses separate DISTRICTS and SECTORS tables.

A sector belongs to a district. Therefore, the district information will be stored in the DISTRICTS table and referenced by the SECTORS table.

WATER_POINTS will reference its administrative location rather than repeatedly storing district details.

The exact mapping of the original Geo Level fields to administrative levels will be confirmed during field mapping.

### 6.2 Fault Information

Fault categories will be stored separately in FAULT_TYPES.

FAULT_REPORTS will reference a fault type instead of repeating its description in every report.

### 6.3 Maintenance Information

Maintenance team details will be stored in MAINTENANCE_TEAMS.

REPAIR_ASSIGNMENTS will reference the relevant maintenance team and fault report instead of repeating team details in every assignment.

### 6.4 Result of 3NF

The proposed design separates water-point information, administrative locations, fault reports, inspections, maintenance teams, repair assignments, repair activities and maintenance costs into related tables.

**Dependency removed:** Descriptive information that depends on another entity rather than directly on the primary key is moved into its own table and connected through foreign keys.

The final table structure and relationships will be documented in the logical ERD and data dictionary.
