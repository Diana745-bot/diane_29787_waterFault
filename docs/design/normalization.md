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
