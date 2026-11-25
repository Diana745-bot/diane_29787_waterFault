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
