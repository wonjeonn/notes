## PL/SQL Functions

PL/SQL functions are reusable blocks of code that perform specific tasks and return a value. They are stored in the Oracle Database for efficiency and reuse.

#### Structure of a PL/SQL Function

1. **Header**: Defines the function's name, parameters, and return type.
2. **Body**:
   - **Declarative Section**: Where variables, constants, cursors, and user-defined types are declared.
   - **Executable Section**: Contains the executable statements and at least one `RETURN` statement.
   - **Exception-Handling Section**: Handles exceptions that might occur during execution.

#### Syntax

```sql
CREATE [OR REPLACE] FUNCTION function_name
(parameter_list)
RETURN return_type
IS
[declarative_section]
BEGIN
[executable_section]
[EXCEPTION]
[exception_handling_section]
END;
```

- **[OR REPLACE]**: Allows modification of an existing function.
- **parameter_list**: List of parameters enclosed in parentheses.
- **return_type**: Data type of the returned value.

#### Example

```sql
CREATE OR REPLACE FUNCTION getwarehouse (locationno INTEGER)
RETURN NUMBER
IS
  warehouseid NUMBER := 0;
BEGIN
  SELECT Warehouse_id INTO warehouseid
  FROM warehouses
  WHERE location_id = locationno;
  RETURN warehouseid;
END;
```

#### Calling a PL/SQL Function

- **In PL/SQL Block:**
   ```sql
   DECLARE
     wareid NUMBER;
   BEGIN
     wareid := getwarehouse(13);
     DBMS_OUTPUT.PUT_LINE('Warehouse ID: ' || wareid);
   END;
   ```

- **In SQL Statement:**
   ```sql
   SELECT getwarehouse(9) FROM DUAL;
   ```

#### Removing a Function

```sql
DROP FUNCTION Getwarehouse;
```

---

## Cursors in PL/SQL

Cursors are pointers to a context area created by Oracle for processing SQL statements. They hold information about the SQL statement and the rows retrieved.

#### Types of Cursors

1. **Implicit Cursor**
   - Automatically created for every SQL DML operation.
   - Cannot be named or controlled directly.
   - Accessed through attributes like `%FOUND`, `%NOTFOUND`, `%ROWCOUNT`, and `%ISOPEN`.

2. **Explicit Cursor**
   - Created and managed by the programmer.
   - Allows explicit declaration, opening, fetching, and closing.

#### Working with Explicit Cursors

1. **Declare the Cursor**:

   ```sql
   DECLARE
     CURSOR cursor_name IS SELECT_statement;
   ```

2. **Open the Cursor**:

   ```sql
   OPEN cursor_name;
   ```

3. **Fetch Data**:

   ```sql
   FETCH cursor_name INTO variable;
   ```

4. **Close the Cursor**:

   ```sql
   CLOSE cursor_name;
   ```

#### Example of Explicit Cursor

```sql
DECLARE
  CURSOR GetEmp_cursor IS SELECT fname FROM user1;
  var_empfname user1.fname%TYPE;
BEGIN
  OPEN GetEmp_cursor;
  LOOP
    FETCH GetEmp_cursor INTO var_empfname;
    EXIT WHEN GetEmp_cursor%NOTFOUND;
    DBMS_OUTPUT.PUT_LINE('Employee Fetched: ' || var_empfname);
  END LOOP;
  DBMS_OUTPUT.PUT_LINE('Total rows fetched is ' || GetEmp_cursor%ROWCOUNT);
  CLOSE GetEmp_cursor;
END;
/
```

#### Cursor Attributes

- **`%FOUND`**: `TRUE` if the last fetch was successful; otherwise `FALSE`.
- **`%NOTFOUND`**: `TRUE` if the last fetch was unsuccessful.
- **`%ISOPEN`**: `TRUE` if the cursor is open; otherwise `FALSE`.
- **`%ROWCOUNT`**: Number of rows affected or fetched.

#### Using `%ROWTYPE`

- **`%ROWTYPE`**: Provides a record type representing a row in a database table.

Example:

```sql
DECLARE
  CURSOR user_cursor IS SELECT userid, lname, salary FROM user2 WHERE userid = 1;
  user2_temp user_cursor%ROWTYPE;
BEGIN
  OPEN user_cursor;
  FETCH user_cursor INTO user2_temp;
  DBMS_OUTPUT.PUT_LINE('User ID: ' || user2_temp.userid);
  DBMS_OUTPUT.PUT_LINE('User Last name: ' || user2_temp.lname);
  DBMS_OUTPUT.PUT_LINE('User Salary is: ' || user2_temp.salary);
  CLOSE user_cursor;
END;
/
```

#### FOR Loop with Cursor

- **`FOR LOOP`**: Manages cursor operations implicitly, simplifying cursor management.

Example:

```sql
DECLARE
  CURSOR GetEmp_cursor IS SELECT emp_name FROM emp;
BEGIN
  FOR var_empfname IN GetEmp_cursor LOOP
    DBMS_OUTPUT.PUT_LINE('Employee Fetched: ' || var_empfname.emp_name);
  END LOOP;
END;
/
```
