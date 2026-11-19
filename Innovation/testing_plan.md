# Innovation Testing Plan

## 1. Purpose

Testing will confirm that the Oracle APEX interface works correctly with the Public Water Fault Tracking System database.

## 2. Planned Tests

| Test | Expected Result |
|---|---|
| Register a water fault | The fault is saved in the database. |
| View fault reports | Existing fault records are displayed correctly. |
| Record an inspection | Inspection details are saved successfully. |
| Assign a maintenance team | The selected team is linked to the repair assignment. |
| Update repair status | The new repair status is recorded correctly. |
| View maintenance costs | Recorded costs are displayed accurately. |
| Enter invalid information | The system displays an appropriate error message. |

## 3. Database Verification

After performing operations through the interface, database queries will be used to confirm that records are correctly inserted, updated and retrieved.

## 4. Testing Status

Testing has not yet started. It will be performed after the Oracle database, PL/SQL components and APEX interface have been implemented.
