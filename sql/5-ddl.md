# Week 5: SQL Data Definition Language (DDL) and Temporary Tables

## Data Types in Database Design
### Numeric Data Types
- **Integer:** For whole numbers. Examples: `INT`, `TINYINT`, `SMALLINT`, `BIGINT`.
- **Decimal:** For fixed or floating-point numbers. Examples: `DECIMAL(p, s)`, `FLOAT(n)`.

### String Data Types
- **Fixed-Length Strings:** For fields with consistent lengths (e.g., codes). Example: `CHAR(n)`.
- **Variable-Length Strings:** For variable-length data (e.g., names). Examples: `VARCHAR(n)`, `VARCHAR(MAX)` (for large texts).
- **Unicode Strings:** For international characters. Example: `NVARCHAR(n)`.

### Date and Time Data Types
- **Date:** For date values. Examples: `DATE`, `DATETIME`, `TIMESTAMP`.

### Boolean Data Type
- **Boolean:** For true/false values. Example: `BIT`.

## Constraints in Databases

Constraints are rules and limitations applied to data stored in database tables, ensuring data integrity, security and consistency.

- **Primary Key:** Ensures each record has a unique identifier.
- **Foreign Key:** Enforces referential integrity between tables.
- **NOT NULL:** Requires a field to always have a value.
- **Unique:** Ensures all values in a column are unique.
- **Default Value:** Provides a default value for a column.
- **Check:** Enforces specific conditions on column values.
- **Index:** Improves data retrieval performance.

## Creating Tables with DDL

### Creating Tables
```sql
CREATE TABLE tablename (
    column1 datatype constraints,
    column2 datatype constraints,
    ...
    CONSTRAINT constraint_name constraint_type (column_name)
);
```

### Adding Constraints
```sql
ALTER TABLE tablename
ADD CONSTRAINT constraint_name constraint_type (column_name);
```

### Adding Columns
```sql
ALTER TABLE tablename
ADD column_name datatype constraints;
```

### Dropping Columns or Constraints
```sql
ALTER TABLE tablename
DROP COLUMN column_name;

ALTER TABLE tablename
DROP CONSTRAINT constraint_name;
```

## Dropping Tables
```sql
DROP TABLE tablename;
```

## Temporary Tables
Temporary tables are used for various purposes, such as data migration, import/export and complex calculations. They exist for a specific session or transaction and are then automatically removed.

### Creating Temporary Tables
```sql
CREATE TEMPORARY TABLE temp_table (
    column1 datatype constraints,
    column2 datatype constraints,
    ...
);
```
