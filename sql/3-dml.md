# Week 3: DML (Data Manipulation Language)

DML or Data Manipulation Language, is a fundamental part of SQL that focuses on manipulating data within the database. CRUD (Create, Read, Update, Delete) operations are at the core of DML.

## CREATE (INSERT)

An INSERT statement is used to add new records (rows) to a table.

```sql
INSERT INTO employees (employee_id, first_name, last_name, department, salary)
VALUES (101, 'John', 'Doe', 'Sales', 55000);
```

## READ (SELECT)

A SELECT statement retrieves data from a database table.

```sql
SELECT first_name, last_name, department, salary
FROM employees
WHERE employee_id = 101;
```

## UPDATE

An UPDATE statement modifies existing data in a table.

```sql
UPDATE employees
SET salary = 60000
WHERE employee_id = 101;
```

## DELETE

A DELETE statement removes records from a table based on specified conditions.

```sql
DELETE FROM employees
WHERE employee_id = 101;
```
