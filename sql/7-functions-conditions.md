# Week 7: SQL Functions and Conditions

### Extracting Year from Date
```sql
SELECT
    first_name,
    last_name,
    EXTRACT(YEAR FROM hire_date) AS hire_year
FROM employees;
```

### Formatting Dates
```sql
SELECT
    first_name,
    last_name,
    TO_CHAR(hire_date, 'DD-MON-YYYY') AS formatted_hire_date
FROM employees;
```

### Date Arithmetic
```sql
SELECT
    first_name,
    last_name,
    hire_date + INTERVAL '5' YEAR AS completion_date
FROM employees;
```

### Calculate the Age of Employees
```sql
SELECT
    first_name,
    last_name,
    TRUNC(MONTHS_BETWEEN(SYSDATE, birth_date) / 12) AS age
FROM employees;
```

### Combining Conditions with AND
```sql
SELECT
    first_name,
    last_name,
    salary
FROM employees
WHERE department = 'Marketing' AND salary > 40000;
```

### Combining Conditions with OR
```sql
SELECT
    first_name,
    last_name,
    department
FROM employees
WHERE department IN ('HR', 'Finance');
```

### Conditional Statements with CASE
```sql
SELECT
    first_name,
    last_name,
    salary,
    CASE
        WHEN salary < 30000 THEN 'Low Salary'
        WHEN salary >= 30000 AND salary < 60000 THEN 'Medium Salary'
        ELSE 'High Salary'
    END AS salary_group
FROM employees;
```

### Rounding Numbers to the Nearest Hundred
```sql
SELECT
    first_name,
    last_name,
    ROUND(salary, -2) AS rounded_salary
FROM employees;
```

### Subquery in the SELECT Clause
```sql
SELECT
    first_name,
    last_name,
    salary,
    (SELECT MAX(salary) FROM employees) AS max_salary
FROM employees;
```

### Subquery with EXISTS
```sql
SELECT
    first_name,
    last_name
FROM employees
WHERE EXISTS (SELECT 1 FROM dependents WHERE employees.employee_id = dependents.employee_id);
```

### Data Aggregation Using HAVING
```sql
SELECT
    department,
    AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 45000;
```

### Case-Insensitive Search
```sql
SELECT
    first_name,
    last_name
FROM employees
WHERE REGEXP_LIKE(last_name, 'smith', 'i');
```

### Recursive Queries (Common Table Expressions)
```sql
WITH RECURSIVE EmployeeHierarchy (employee_id, first_name, last_name, manager_id, level) AS (
  SELECT
    employee_id,
    first_name,
    last_name,
    manager_id,
    1
  FROM employees
  WHERE manager_id IS NULL
  UNION ALL
  SELECT
    e.employee_id,
    e.first_name,
    e.last_name,
    e.manager_id,
    eh.level + 1
  FROM employees e
  INNER JOIN EmployeeHierarchy eh ON e.manager_id = eh.employee_id
)
SELECT
  LPAD(' ', (level - 1) * 4) || first_name || ' ' || last_name AS hierarchy
FROM EmployeeHierarchy
ORDER BY level, employee_id;
```
