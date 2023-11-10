# Week 6: Transactions, Concurrency and Database Security

## Transactions: Ensuring Data Consistency

**Transactions** are logical, atomic units of work involving one or more SQL statements. They guarantee that a series of operations either entirely succeed (`COMMIT`) or entirely fail (`ROLLBACK`).

### Transaction Atomicity, Consistency, Isolation, Durability (ACID)

- **Atomicity:** A transaction is atomic, meaning it is indivisible. It is treated as a single, all-or-nothing operation. If any part of the transaction fails, the entire transaction is rolled back.

- **Consistency:** A transaction should bring the database from one consistent state to another. It ensures that integrity constraints are not violated during the transaction.

- **Isolation:** Transactions should be isolated from each other. When multiple transactions occur simultaneously, they should not interfere with each other's operations until they are completed. This is often achieved using locking mechanisms.

- **Durability:** Once a transaction is committed, its changes should persist even in the face of system failures. The database system should ensure that committed data is stored permanently.

### Transaction Scope

Transactions begin with `BEGIN` and conclude with either `COMMIT` (to save changes) or `ROLLBACK` (to undo changes). **Savepoints** allow partial rollbacks, ensuring more granular control over transactions.

## Concurrency Management

**Concurrency** arises when multiple users or processes access the same data simultaneously. Managing concurrency is critical to prevent conflicts and maintain data integrity. Techniques like **locks** and **timestamps** are used to handle concurrent data access.

- **Locks:** Locks are mechanisms that prevent multiple transactions from modifying the same data simultaneously. They ensure that transactions execute in isolation, preventing data corruption.

- **Timestamps:** Timestamps are used to track the order of transactions. They help in resolving conflicts when two or more transactions attempt to modify the same data. The transaction with the earliest timestamp is typically given priority.

## User-Level Security: Grant and Revoke Privileges

### Types of Privileges

Database systems offer various types of privileges to control user access to database objects. The common types include:

1. **SELECT:** Allows users to retrieve data from a table.

2. **INSERT:** Permits users to add new rows to a table.

3. **UPDATE:** Enables users to modify existing data in a table.

4. **DELETE:** Grants the ability to remove rows from a table.

5. **EXECUTE:** Authorizes the execution of stored procedures and functions.

6. **REFERENCES:** Allows referencing a column in a foreign key constraint.

7. **ALL PRIVILEGES:** Grants all available privileges on a specific object.

8. **CREATE:** Authorizes the creation of database objects.

9. **ALTER:** Permits the modification of the structure of existing objects.

10. **DROP:** Allows the removal of database objects.

11. **GRANT OPTION:** Permits the recipient to further grant the same privilege to others.

### Granting Privileges (`GRANT`)

The `GRANT` statement gives specific privileges to a user or a role, enabling them to perform actions on specified database objects.

**Syntax:**
```sql
GRANT privilege(s) ON object_name TO user_name;
```

**Example:**
```sql
GRANT SELECT, INSERT ON employees TO user_name;
```

### Revoking Privileges (`REVOKE`)

The `REVOKE` statement removes previously granted privileges, restricting a user's access to database objects.

**Syntax:**
```sql
REVOKE privilege(s) ON object_name FROM user_name;
```

**Example:**
```sql
REVOKE SELECT ON employees FROM user_name;
```
