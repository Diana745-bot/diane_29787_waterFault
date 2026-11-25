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
