# Week 4: SQL Multiple-Table Queries (Joins) and Views

## ANSI-89 Joins
- ANSI-89 joins, known as "Simple Joins" or "Natural Joins".
- Results in a CROSS join if WHERE clause is not specified.
- May lead to ambiguous fields, necessitating explicit qualification.

```sql
SELECT <fieldlist>
FROM <table1>, <table2>
WHERE <table1.keyfield> = <table2.keyfield>;
```

## ANSI-92 Joins
**JOIN:**
```sql
SELECT <fieldlist>
FROM <table1>
<Join Type> JOIN <table2>
ON <table1.keyfield> = <table2.keyfield>;
```
**USING:**

```sql
SELECT <fieldlist>
FROM <table1>
<Join Type> JOIN <table2>
USING (<keyfield>);
```

## Inner Join
An **inner** join returns the intersection of two tables, e.g, it returns only the rows that have matching values in both tables.

```sql
SELECT * 
FROM table1
INNER JOIN table2 
ON table1.column_name = table2.column_name;
```

| playerID | firstname | lastname | teamID | teamName |
|----------|-----------|----------|--------|----------|
| 1        | John      | Smith    | 10     | Hornets  |
| 2        | Bob       | Marley   | 10     | Hornets  |
| 3        | Steven    | King     | 11     | Falcons  |

## Outer Joins
- Extend Inner joins to include unmatched rows from one or both tables.
- **LEFT** OUTER JOIN: Returns all rows from the left table and matched rows from the right table.
- **RIGHT** OUTER JOIN: Returns all rows from the right table and matched rows from the left table.
- **FULL** OUTER JOIN: Returns all rows when there is a match in one of the tables.

```sql
SELECT * 
FROM table1
LEFT JOIN table2 
ON table1.column_name = table2.column_name;
```

### Left Outer Join

| playerID | firstname | lastname | teamID | teamName |
|----------|-----------|----------|--------|----------|
| 1        | John      | Smith    | 10     | Hornets  |
| 2        | Bob       | Marley   | 10     | Hornets  |
| 3        | Steven    | King     | 11     | Falcons  |
| 4        | Jim       | Parsons  | null   | null     |

### Right Outer Join

| playerID | firstname | lastname | teamID | teamName |
|----------|-----------|----------|--------|----------|
| 1        | John      | Smith    | 10     | Hornets  |
| 2        | Bob       | Marley   | 10     | Hornets  |
| 3        | Steven    | King     | 11     | Falcons  |
| null     | null      | null     | 12     | Bloopers |

### Full Outer Join

| playerID | firstname | lastname | teamID | teamName |
|----------|-----------|----------|--------|----------|
| 1        | John      | Smith    | 10     | Hornets  |
| 2        | Bob       | Marley   | 10     | Hornets  |
| 3        | Steven    | King     | 11     | Falcons  |
| 4        | Jim       | Parsons  | null   | null     |
| null     | null      | null     | 12     | Bloopers |

## CROSS JOIN:
A CROSS JOIN produces all possible combinations between the rows of two tables.

```sql
SELECT *
FROM table1
CROSS JOIN table2;
```

| playerID | firstname | lastname | teamID | teamName |
|----------|-----------|----------|--------|----------|
| 1        | John      | Smith    | 10     | Hornets  |
| 1        | John      | Smith    | 11     | Falcons  |
| 1        | John      | Smith    | 12     | Bloopers |
| 2        | Bob       | Marley   | 10     | Hornets  |
| 2        | Bob       | Marley   | 11     | Falcons  |
| 2        | Bob       | Marley   | 12     | Bloopers |
| 3        | Steven    | King     | 10     | Hornets  |
| 3        | Steven    | King     | 11     | Falcons  |
| 3        | Steven    | King     | 12     | Bloopers |
| 4        | Jim       | Parsons  | 10     | Hornets  |
| 4        | Jim       | Parsons  | 11     | Falcons  |
| 4        | Jim       | Parsons  | 12     | Bloopers |

## Joins With More Than 2 Tables

```sql
SELECT <fields>
FROM table1
JOIN table2 ON table1.keyfield = table2.keyfield
JOIN table3 ON table2.anotherfield = table3.anotherfield;
```

## Views
- Views are named SELECT statements stored as objects in the database.
- Views do not store data; provide a way to represent complex queries.

```sql
CREATE VIEW viewname AS
SELECT <fields>
FROM <tables>
WHERE <conditions>;
```

## Modifying a View
Views can be modified without dropping them using CREATE OR REPLACE or ALTER statement.

```sql
CREATE OR REPLACE VIEW viewname AS
SELECT <modified fields>
FROM <tables>
WHERE <modified conditions>;
```
