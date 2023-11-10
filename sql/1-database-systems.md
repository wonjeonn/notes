# Week 1: Database Systems and Relational Database

## Data vs. Information
- **Data:** Raw, unprocessed facts (e.g., strings, numbers, dates).
- **Information:** Meaningful output derived from processing data; vital for decision-making.

## Data Redundancy
- Storing data in multiple places causes problems.
- Updates require changes in every location, e.g., updating a customer's phone number in multiple tables.

## Data Repetition
- Storing data once but repeating it leads to errors during updates, e.g., a customer placing multiple orders with repetitive data.

## Data Anomalies
- **Modification Anomalies:** Updating data leads to changes in multiple records.
- **Insertion Anomalies:** Foreign key reference required before inserting data.
- **Deletion Anomalies:** Removing a record results in the loss of related data.

## Databases
- Centralized structure with logically related data.
- Prevents disorganization, offers real-time access, supports manipulation, integration and sharing.

## Database Management Systems (DBMS)
- Collection of programs managing database structure and access.
- Key components: data sharing, consistency, ad hoc querying.

## Relational Model
- **Data Modeling:** Describing data, including storage structure, operations and constraints.
- **Relational Data Model:** Defines relationships between data points, eliminating inefficiencies and dependencies.
- **Tables (Relations):** Two-dimensional representation; rows represent instances, columns represent attributes.

  Example: Departments
  | Department_ID | Department_Name | Manager_ID | Location_ID |
  |---------------|-----------------|------------|-------------|
  | 10            | Administration  | 200        | 1700        |
  | 20            | Marketing       | 201        | 1800        |
  | 50            | Shipping        | 124        | 1500        |

## Keys
- **Candidate Key:** Potential attribute(s) for unique identification.
- **Primary Key:** Chosen attribute(s) for unique identification.
- **Composite Key:** Multiple attributes form uniqueness.
- **Surrogate Key:** Artificially added field for simplicity.
- **Foreign Key:** Establishes relationships between tables.

## Relationships
- **1-to-Many (1-∞) Relationship:** One value in the parent table relates to many in the child table.
- **1-to-1 (1-1) Relationship:** One value in each table uniquely relates to the other.
- **Many-to-Many (∞-∞) Relationship:** Many values in each table relate to many in the other table.
- **Junction/Bridge Table:** Handles many-to-many relationships.

## Referential Integrity
- Enforces data accuracy by ensuring values exist in parent table before insertion.
- Prevents orphan records and maintains data consistency.
- **Cascading:** Automates updates and deletes between related tables.
  - **Cascade Updates:** Child records updated when parent primary key changes.
  - **Cascade Deletes:** Child records deleted when parent record is deleted.

## Table Types
- **Data Table:** Stores raw data for querying and analysis.
- **Lookup Table:** Centralizes data to avoid redundancy; often used for dropdown lists.
- **Junction/Bridge Table:** Facilitates many-to-many relationships through two 1-to-many relationships.
- **Temporary Table:** Short-lived, used for data migration or query optimization.
