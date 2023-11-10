# Week 2: SQL Fundamentals

## Sub-Languages of SQL
- SQL (Structured Query Language):
  - **DDL (Data Definition Language):** Used for defining and managing the structure of a database, including CREATE, ALTER and DROP tables.
  - **DML (Data Manipulation Language):** Focuses on manipulating data within the database, including SELECT, INSERT, UPDATE and DELETE operations.
  - **DCL (Data Control Language):** Manages permissions, access control and security through commands like GRANT and REVOKE.
  - **TCL (Transaction Control Language):** Handles transactions and ensures data integrity with commands like COMMIT, ROLLBACK and SAVEPOINT.

## The Basics of SELECT, Order of Execution and the Dual Table
- **SELECT:** The SQL statement used to retrieve data from a database table.
  - **FROM:** Specifies the data source (table).
  - **WHERE:** Filters rows based on specified conditions.
  - **SELECT:** Specifies the columns to be included in the result set.
- **DUAL** Table: A special, one-row, one-column table often used to evaluate SQL expressions or perform ad hoc calculations.
- **DISTINCT**: Retrieve unique or distinct values from a specified column, eliminating duplicate entries from the result set.

```sql
SELECT DISTINCT department FROM employees;
```

## Aliases (Field and Table Aliases)
**Aliases:** Aliases are used to provide alternative names for tables or columns in SQL queries.

```sql
SELECT
    first_name AS "First Name",
    last_name AS "Last Name"
FROM employees;
```

## Calculated Values and Single-Line Functions
- Mathematical functions (e.g., +, -, *, /).
- String functions (e.g., CONCAT for string concatenation).
- Date functions (e.g., NOW() for the current date and time).

```sql
SELECT salary * 1.1 AS "10% Raise" FROM employees;
```

## Filtering Data (WHERE)
**WHERE:** The WHERE clause is used to filter rows in the result set based on a specified condition.

```sql
SELECT * FROM products WHERE price > 100;
```

### Wildcards
- **Wildcards:** Wildcards are used to match patterns in text data.
- Common wildcards:
  - `%` matches any sequence of characters.
  - `_` matches any single character.

```sql
SELECT * FROM customers WHERE last_name LIKE 'S%';
```

## Sorting Data (ORDER BY)
**ORDER BY:** The ORDER BY clause is used to sort query results in ascending (ASC) or descending (DESC) order based on one or more columns.

```sql
SELECT * FROM products ORDER BY price DESC;
```

## Limiting Results (FETCH)
**FETCH:** The FETCH clause is used to limit the number of rows returned in the result set.

```sql
SELECT * FROM orders FETCH FIRST 10 ROWS ONLY;
```

## Aggregating Data
**GROUP BY:**
```sql
SELECT
    department,
    SUM(salary) AS total_salary_expense
FROM employees
GROUP BY department;
```
