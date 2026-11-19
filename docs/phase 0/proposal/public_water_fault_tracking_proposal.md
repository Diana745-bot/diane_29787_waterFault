# Public Water Fault Tracking System

**Student Name:** UMUTONIWASE Diane  
**Student ID:** 29787  
**Course:** INSY 8311 – Database Development with PL/SQL  
**Instructor:** Eric Maniraguha
**Group:** I

## 1. Problem Statement

Public water points are important sources of drinking water for many communities in Rwanda. However, when a water point breaks down, reporting the problem, arranging inspections, assigning repair teams and monitoring maintenance progress can be difficult without an organized tracking system.

The lack of a centralized record of faults and repair activities can make it harder for responsible teams to follow up on reported problems and maintain accurate maintenance records.
## 2. Proposed Solution

The proposed system will provide a centralized database for recording public water points and managing their maintenance activities. It will allow authorized users to register reported faults, record inspection results, assign maintenance teams, monitor repair progress and keep records of maintenance costs.

The system will help responsible personnel follow up on reported faults and maintain organized records of water-point maintenance.

## 3. Data Source

The project will use the **Water For People_Rwanda_2021** dataset from the Water Point Data Exchange (WPdx) catalogue.

Dataset link: https://catalog.waterpointdata.org/datasets/wfp-rwanda-621f8339/index.html

The dataset contains information about individual water points in Rwanda, including their locations, technology types and functionality status. These records will provide the initial water-point information for the database. Fault reports, inspections and repair activities will be recorded separately as the system is developed.
## 4. Planned Database Tables

The system is expected to use the following tables:

1. DISTRICTS – stores district information.
2. SECTORS – stores sector information and links sectors to districts.
3. WATER_POINTS – stores water-point details and locations.
4. REPORTERS – stores information about people reporting faults.
5. FAULT_TYPES – stores categories of water-point faults.
6. FAULT_REPORTS – records faults reported at water points.
7. INSPECTIONS – stores inspection dates, findings and results.
8. MAINTENANCE_TEAMS – stores maintenance team information.
9. TEAM_MEMBERS – stores members belonging to maintenance teams.
10. REPAIR_ASSIGNMENTS – records teams assigned to repair reported faults.
11. REPAIR_ACTIVITIES – tracks repair work and progress.
12. MAINTENANCE_COSTS – records costs associated with maintenance activities.
## 5. Planned PL/SQL Features

The project will use the following PL/SQL features:

- **Procedures:** To register water-point faults, record inspections and assign repair teams.
- **Functions:** To calculate repair costs and determine the duration of maintenance activities.
- **Cursors:** To retrieve and process lists of reported faults and pending repairs.
- **Triggers:** To automatically record important changes, such as updates to repair status.
- **Packages:** To organize related procedures and functions for water-point maintenance.
- **Exception Handling:** To manage errors such as invalid water-point IDs, missing records and duplicate fault reports.
  ## 6. Innovation

The project will include an interactive web-based interface developed using Oracle APEX and connected to the Oracle database. Authorized users will be able to register water-point faults, view reported problems, monitor repair progress and access maintenance records.

PL/SQL will handle the database operations and business rules, while the interface will make the system easier to use and demonstrate.
## 7. Expected Benefits

The system is expected to:

- Improve the organization of public water-point fault records.
- Make it easier to monitor inspections and repair progress.
- Support maintenance teams in following up on reported faults.
- Provide useful records for reviewing maintenance activities and costs.

## 8. References

1. Murray, A. L., et al. (2024). *Rural water point functionality estimates and associations: Evidence from nine countries in Sub-Saharan Africa and South Asia*. Water Resources Research. https://doi.org/10.1029/2023WR034679

2. Klug, T., Cronk, R., Shields, K. F., & Bartram, J. (2018). *A categorization of water system breakdowns: Evidence from Liberia, Nigeria, Tanzania, and Uganda*. Science of the Total Environment. https://doi.org/10.1016/j.scitotenv.2017.11.183

3. National Institute of Statistics of Rwanda. (2025). *EICV7: Thematic report – Utilities and amenities 2023/24*. https://www.gis.statistics.gov.rw/statistical-publications/ict-water-sanitation-energy-tourism-and-transport/eicv7-thematic-report-utilities-and-amenities-202324

4. mWater. (n.d.). *Platform*. https://www.mwater.co/platform

5. Water Point Data Exchange. (2022). *Water For People_Rwanda_2021* [Dataset]. https://catalog.waterpointdata.org/datasets/wfp-rwanda-621f8339/index.html

6. Oracle. (2024). *Oracle Database PL/SQL Language Reference, 21c*. https://docs.oracle.com/en/database/oracle/oracle-database/21/lnpls/
