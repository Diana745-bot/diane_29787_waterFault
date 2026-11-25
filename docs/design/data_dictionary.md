# Data Dictionary – Public Water Fault Tracking System

## 1. Purpose

This document describes the logical database tables, their columns, primary keys, foreign keys, relationships and constraints for the Public Water Fault Tracking System.

It serves as a reference for the database structure before implementation in Oracle Database 21c.

## 2. Table Definitions

### 2.1 DISTRICTS

Stores the administrative districts where the water points are located.

| Column Name | Description | Key | Required? | Unique? |
|---|---|---|---|---|
| DISTRICT_ID | Identifies each district | PK | Yes | Yes |
| DISTRICT_NAME | Name of the district | | Yes | Yes |
| COUNTRY_NAME | Country where the district is located | | Yes | No |
### 2.2 SECTORS

Stores the sectors belonging to each district.

| Column Name | Description | Key | Required? | Unique? |
|---|---|---|---|---|
| SECTOR_ID | Identifies each sector | PK | Yes | Yes |
| DISTRICT_ID | Identifies the district to which the sector belongs | FK | Yes | No |
| SECTOR_NAME | Name of the sector | | Yes | No |
### 2.3 WATER_POINTS

Stores information about public water points, including their location, technology, functionality and service level.

| Column Name | Description | Key | Required? | Unique? |
|---|---|---|---|---|
| WATER_POINT_ID | Identifies each water point | PK | Yes | Yes |
| INSTANCE_ID | Original survey instance identifier | | No | No |
| SECTOR_ID | Sector where the water point is located | FK | Yes | No |
| CELL_NAME | Cell where the water point is located | | No | No |
| VILLAGE_NAME | Village where the water point is located | | No | No |
| GEO_LEVEL_6 | Additional geographical level from the source dataset | | No | No |
| GEO_LEVEL_7 | Additional geographical level from the source dataset | | No | No |
| RECORD_DATE | Date associated with the source observation | | No | No |
| LATITUDE | Geographic latitude | | No | No |
| LONGITUDE | Geographic longitude | | No | No |
| ELEVATION | Water-point elevation | | No | No |
| NUMBER_OF_USERS | Number of people using the water point | | No | No |
| SERVICE_LEVEL | Reported service level | | No | No |
| SERVICE_LEVEL_SCORE | Numerical service-level score | | No | No |
| SOURCE_PROTECTED | Indicates whether the water source is protected | | No | No |
| IMPROVED_WATER_POINT | Indicates whether the water point is classified as improved | | No | No |
| TECHNOLOGY_IMPROVED | Improved water-point technology | | No | No |
| TECHNOLOGY_UNIMPROVED | Unimproved water-point technology | | No | No |
| IS_FUNCTIONAL | Reported functionality status | | No | No |
| USERS_MEET_STANDARDS | Indicates whether the number of users meets the standard | | No | No |
| IS_OUT_OF_SERVICE_OR_BROKEN | Indicates whether the water point is broken or out of service | | No | No |
| BREAKAGE_FREQUENCY_MEETS_STANDARD | Indicates whether breakage frequency meets the standard | | No | No |
| BREAKAGE_DURATION_MEETS_STANDARD | Indicates whether breakage duration meets the standard | | No | No |
| OUT_OF_SERVICE_WITHIN_STANDARD | Indicates whether service interruption meets the standard | | No | No |
| WATER_AVAILABLE_ON_VISIT | Indicates whether water was available during the visit | | No | No |
| SECONDS_TO_FILL_20L | Time required to fill a 20-litre container | | No | No |
| HANDPUMP_FLOW_RATE | Flow rate for handpump water points | | No | No |
| LITERS_PER_PERSON_PER_DAY | Daily water quantity per person for piped systems | | No | No |
| QUANTITY_MEETS_STANDARD | Indicates whether available water quantity meets the standard | | No | No |
| PIPED_OR_HANDPUMP | Identifies the water-point system type | | No | No |
| ECOLI_MEETS_STANDARD | Indicates whether E. coli meets the water-quality standard | | No | No |
| RESIDUAL_CHLORINE_MEETS_STANDARD | Indicates whether residual chlorine meets the standard | | No | No |
| BACTERIA_MEETS_STANDARD | Indicates whether bacteria meets the standard | | No | No |
| OTHER_CONTAMINANT | Records another contaminant of concern | | No | No |
| OTHER_CONTAMINANT_MEETS_STANDARD | Indicates whether the other contaminant meets the standard | | No | No |
| WATER_QUALITY_MEETS_STANDARD | Overall water-quality standards indicator | | No | No |
| OVERALL_CONDITION | Indicates the overall condition and functioning of the water point | | No | No |
### 2.4 REPORTERS

Stores information about people who report faults at public water points.

| Column Name | Description | Key | Required? | Unique? |
|---|---|---|---|---|
| REPORTER_ID | Identifies each reporter | PK | Yes | Yes |
| REPORTER_NAME | Full name of the reporter | | Yes | No |
| PHONE_NUMBER | Reporter's contact number | | No | No |
| EMAIL | Reporter's email address | | No | Yes |
| REPORTER_TYPE | Type of reporter, such as community member or staff | | No | No |
### 2.5 FAULT_TYPES

Stores the different categories of faults that can affect public water points.

| Column Name | Description | Key | Required? | Unique? |
|---|---|---|---|---|
| FAULT_TYPE_ID | Identifies each fault type | PK | Yes | Yes |
| FAULT_TYPE_NAME | Name of the fault category | | Yes | Yes |
| DESCRIPTION | Explanation of the fault type | | No | No |
### 2.6 FAULT_REPORTS

Stores fault reports submitted by reporters about public water points.

| Column Name | Description | Key | Required? | Unique? |
|---|---|---|---|---|
| FAULT_REPORT_ID | Identifies each fault report | PK | Yes | Yes |
| WATER_POINT_ID | Water point where the fault occurred | FK | Yes | No |
| REPORTER_ID | Person who submitted the report | FK | Yes | No |
| FAULT_TYPE_ID | Category of the reported fault | FK | Yes | No |
| REPORT_DATE | Date the fault was reported | | Yes | No |
| FAULT_DESCRIPTION | Details about the reported fault | | No | No |
| PRIORITY_LEVEL | Urgency level of the fault | | Yes | No |
| REPORT_STATUS | Current status of the report | | Yes | No |
### 2.7 INSPECTIONS

Stores inspection records created when a water point is checked to assess its condition or investigate a reported fault.

| Column Name | Description | Key | Required? | Unique? |
|---|---|---|---|---|
| INSPECTION_ID | Identifies each inspection | PK | Yes | Yes |
| WATER_POINT_ID | Water point being inspected | FK | Yes | No |
| FAULT_REPORT_ID | Related fault report, if applicable | FK | No | No |
| INSPECTION_DATE | Date of the inspection | | Yes | No |
| INSPECTOR_NAME | Name of the person conducting the inspection | | Yes | No |
| FINDINGS | Observations made during the inspection | | No | No |
| RECOMMENDATIONS | Suggested actions after inspection | | No | No |
### 2.8 MAINTENANCE_TEAMS

Stores information about teams responsible for repairing and maintaining public water points.

| Column Name | Description | Key | Required? | Unique? |
|---|---|---|---|---|
| TEAM_ID | Identifies each maintenance team | PK | Yes | Yes |
| TEAM_NAME | Name of the maintenance team | | Yes | Yes |
| CONTACT_NUMBER | Team contact number | | No | No |
| TEAM_DESCRIPTION | Description of the team's responsibilities | | No | No |
### 2.9 TEAM_MEMBERS

Stores information about individuals belonging to maintenance teams.

| Column Name | Description | Key | Required? | Unique? |
|---|---|---|---|---|
| TEAM_MEMBER_ID | Identifies each team member | PK | Yes | Yes |
| TEAM_ID | Identifies the maintenance team | FK | Yes | No |
| MEMBER_NAME | Full name of the team member | | Yes | No |
| PHONE_NUMBER | Contact number of the member | | No | No |
| ROLE | Responsibility of the member within the team | | No | No |
### 2.10 REPAIR_ASSIGNMENTS

Stores records of maintenance teams assigned to handle reported water-point faults.

| Column Name | Description | Key | Required? | Unique? |
|---|---|---|---|---|
| ASSIGNMENT_ID | Identifies each repair assignment | PK | Yes | Yes |
| FAULT_REPORT_ID | Fault report being handled | FK | Yes | No |
| TEAM_ID | Maintenance team assigned | FK | Yes | No |
| ASSIGNMENT_DATE | Date the team was assigned | | Yes | No |
| EXPECTED_COMPLETION_DATE | Expected repair completion date | | No | No |
| ASSIGNMENT_STATUS | Current status of the assignment | | Yes | No |
### 2.11 REPAIR_ACTIVITIES

Stores details of repair and maintenance work performed on public water points.

| Column Name | Description | Key | Required? | Unique? |
|---|---|---|---|---|
| ACTIVITY_ID | Identifies each repair activity | PK | Yes | Yes |
| ASSIGNMENT_ID | Related repair assignment | FK | Yes | No |
| ACTIVITY_DATE | Date the repair activity was performed | | Yes | No |
| ACTIVITY_DESCRIPTION | Details of the work performed | | Yes | No |
| ACTIVITY_STATUS | Current status of the activity | | Yes | No |
| REMARKS | Additional information about the activity | | No | No |
### 2.12 MAINTENANCE_COSTS

Stores costs associated with repair and maintenance activities.

| Column Name | Description | Key | Required? | Unique? |
|---|---|---|---|---|
| COST_ID | Identifies each maintenance cost record | PK | Yes | Yes |
| ASSIGNMENT_ID | Related repair assignment | FK | Yes | No |
| COST_DATE | Date the cost was recorded | | Yes | No |
| COST_DESCRIPTION | Description of the expense | | Yes | No |
| AMOUNT | Amount spent on the maintenance activity | | Yes | No |
| RECORDED_BY | Name of the person who recorded the cost | | No | No |
## 3. Relationship Summary

| Parent Table | Child Table | Relationship | Description |
|---|---|---|---|
| DISTRICTS | SECTORS | One-to-Many | One district contains many sectors |
| SECTORS | WATER_POINTS | One-to-Many | One sector can contain many water points |
| WATER_POINTS | FAULT_REPORTS | One-to-Many | One water point can have many fault reports |
| REPORTERS | FAULT_REPORTS | One-to-Many | One reporter can submit many fault reports |
| FAULT_TYPES | FAULT_REPORTS | One-to-Many | One fault type can appear in many reports |
| WATER_POINTS | INSPECTIONS | One-to-Many | One water point can have many inspections |
| FAULT_REPORTS | INSPECTIONS | One-to-Many | One fault report can be linked to many inspections |
| MAINTENANCE_TEAMS | TEAM_MEMBERS | One-to-Many | One team can have many members |
| FAULT_REPORTS | REPAIR_ASSIGNMENTS | One-to-Many | One fault report can have multiple assignments |
| MAINTENANCE_TEAMS | REPAIR_ASSIGNMENTS | One-to-Many | One team can receive multiple assignments |
| REPAIR_ASSIGNMENTS | REPAIR_ACTIVITIES | One-to-Many | One assignment can have many repair activities |
| REPAIR_ASSIGNMENTS | MAINTENANCE_COSTS | One-to-Many | One assignment can have many cost records |
## 4. Relationship Cardinality and Optionality

The following relationships use crow's-foot notation:

| Relationship | Cardinality and Optionality |
|---|---|
| DISTRICTS – SECTORS | A district may have zero or many sectors. Each sector belongs to exactly one district. |
| SECTORS – WATER_POINTS | A sector may have zero or many water points. Each water point belongs to exactly one sector. |
| WATER_POINTS – FAULT_REPORTS | A water point may have zero or many fault reports. Each fault report refers to exactly one water point. |
| REPORTERS – FAULT_REPORTS | A reporter may submit zero or many reports. Each report has exactly one reporter. |
| FAULT_TYPES – FAULT_REPORTS | A fault type may appear in zero or many reports. Each report has exactly one fault type. |
| WATER_POINTS – INSPECTIONS | A water point may have zero or many inspections. Each inspection concerns exactly one water point. |
| FAULT_REPORTS – INSPECTIONS | A fault report may have zero or many inspections. An inspection may be linked to zero or one fault report. |
| MAINTENANCE_TEAMS – TEAM_MEMBERS | A team may have zero or many members. Each member belongs to exactly one team. |
| FAULT_REPORTS – REPAIR_ASSIGNMENTS | A fault report may have zero or many assignments. Each assignment refers to exactly one fault report. |
| MAINTENANCE_TEAMS – REPAIR_ASSIGNMENTS | A team may receive zero or many assignments. Each assignment belongs to exactly one team. |
| REPAIR_ASSIGNMENTS – REPAIR_ACTIVITIES | An assignment may have zero or many activities. Each activity belongs to exactly one assignment. |
| REPAIR_ASSIGNMENTS – MAINTENANCE_COSTS | An assignment may have zero or many cost records. Each cost record belongs to exactly one assignment. |
**Unique constraint:** The combination of `DISTRICT_ID` and `SECTOR_NAME` must be unique. This allows different districts to have sectors with the same name without creating duplicate sectors within one district.

