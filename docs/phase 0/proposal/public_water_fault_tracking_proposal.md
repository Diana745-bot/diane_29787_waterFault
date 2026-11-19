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
