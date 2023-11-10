# Week 9: Normalization

## Normalization

**Definition**: Normalization is a step-by-step process used to reduce data inconsistency, anomalies and redundancy in database tables.

**Purposes**:
  - Eliminate redundant data by splitting tables to remove redundancy.
  - Ensure data within a table are related and maintain consistency.

## Dependency Diagram

- **1NF (First Normal Form)**: Eliminate multi-valued dependencies and repeating groups in a table.

- **2NF (Second Normal Form)**: Eliminate partial dependencies, ensuring that all non-key columns are fully dependent on the entire primary key. Achieved when a table has **at least two candidate keys**.

- **3NF (Third Normal Form)**: Remove transitive dependencies, with **at least two non-key** attributes depending on other non-key attributes.

- **BCNF (Boyce-Codd Normal Form):** Require that every determinant in the table should be a candidate key.

- **4NF (Fourth Normal Form):** Ensure there are no multivalued dependencies.

## Functional Dependency

- **Functional Dependency:** It occurs when one or more attributes in a table uniquely determine another attribute.

- **Partial Dependency:** A non-key column depends on a part of the primary key but not the entire primary key.

## Normalization Process

### UDF (User-Defined Function)

```
Project [PROJ_NUM, PROJ_NAME, (EMP_NUM, EMP_NAME, JOB_CLASS, CHG_HOURS, HOURS)]
```

### 1NF

Remove repeating groups and ensure each cell contains a single value.

**Project_Employee_Assignment**: Project[`PROJ_NUM`, `EMP_NUM`, PROJ_NAME, EMP_NAME, JOB_CLASS, CHG_HOURS, HOURS]

| `PROJ_NUM` | `EMP_NUM` | PROJ_NAME | EMP_NAME | JOB_CLASS | CHG_HOURS | HOURS |
|----------|---------|-----------|----------|----------|-----------|-------|
| 1        | 101     | Project A | Alice    | Manager  | 40        | 160   |
| 1        | 102     | Project A | Bob      | Analyst  | 30        | 160   |
| 1        | 103     | Project A | Carol    | Designer | 25        | 160   |
| 2        | 101     | Project B | Alice    | Manager  | 40        | 120   |
| 2        | 104     | Project B | Dave     | Developer| 35        | 120   |
| 2        | 105     | Project B | Eve      | Tester   | 20        | 120   |


### 2NF: Partial Dependencies

Remove partial dependencies by creating new tables and reassigning dependent attributes.

**Project Table**: Project [`PROJ_NUM`, PROJ_NAME]

| `PROJ_NUM` | PROJ_NAME |
|----------|-----------|
| 1        | Project A |
| 2        | Project B |

**Employee Table**: Employee [`EMP_NUM`, EMP_NAME, JOB_CLASS, CHG_HOURS]

| `EMP_NUM` | EMP_NAME | JOB_CLASS| CHG_HOURS |
|---------|----------|----------|-----------|
| 101     | Alice    | Manager  | 40        |
| 102     | Bob      | Analyst  | 30        |
| 103     | Carol    | Designer | 25        |
| 104     | Dave     | Developer| 35        |
| 105     | Eve      | Tester   | 20        |

**Assignment Table**: Assignment [`PROJ_NUM`, `EMP_NUM`, HOURS]

| `PROJ_NUM` | `EMP_NUM` | HOURS |
|----------|---------|-------|
| 1        | 101     | 160   |
| 1        | 102     | 160   |
| 1        | 103     | 160   |
| 2        | 101     | 120   |
| 2        | 104     | 120   |
| 2        | 105     | 120   |

### 3NF: Transitive Dependency

Eliminate transitive dependencies by creating new tables and reassigning dependent attributes.

**Job Table**: Job [`JOB_CLASS`, CHG_HOURS]

| `JOB_CLASS` | CHG_HOURS |
|----------|-----------|
| Manager  | 40        |
| Analyst  | 30        |
| Designer | 25        |
| Developer| 35        |
| Tester   | 20        |

## A Table That is in 3NF and not in BCNF

- A table can be in 3NF but not in BCNF, particularly when it contains multiple candidate keys.

## Surrogate Key Considerations

- Surrogate keys are system-generated attributes used when the primary key is unsuitable. They have a numeric value that increments automatically for each new row.

## The Boyce-Codd Normal Form (BCNF)

- BCNF mandates that every determinant in the table must be a candidate key. It is a special case of 3NF and aims to ensure data integrity.

## Fourth Normal Form (4NF)

- A table is in 4NF when it meets 3NF requirements and has no multivalued dependencies. It focuses on eliminating multivalued facts in the database.

## Importance of Normalization

- **Data Consistency:** Normalization helps maintain data consistency and integrity by minimizing anomalies in data operations (updates, inserts, deletes).

- **Reduced Data Redundancy:** By eliminating redundant data, it optimizes storage and ensures efficient data storage.

- **Improved Query Performance:** Well-normalized databases often lead to faster query performance due to logical data organization.

- **Simpler Updates:** It simplifies data updates by minimizing the need to update the same information in multiple locations.

## Denormalization Considerations

- **Performance:** Denormalization can boost query performance, particularly for read-heavy workloads by reducing the number of joins.

- **Data Integrity:** It can introduce data integrity challenges, as redundant data may go out of sync if not managed properly.

- **Balancing Act:** The decision to denormalize should consider the trade-off between query performance and data integrity based on specific application requirements.

- **Indexing:** Proper indexing is crucial in denormalized databases to maintain good performance and support query patterns.
