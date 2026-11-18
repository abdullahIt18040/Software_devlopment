# CRUD in DBMS

## 1. What is CRUD?

**CRUD** stands for:

- **C – Create**
- **R – Read**
- **U – Update**
- **D – Delete**

CRUD represents the four basic operations used to manage data in a Database Management System (DBMS).

## 2. CRUD Operations with SQL

### 1. Create (INSERT)

Create means inserting new records into a database table.

```sql
INSERT INTO employees (id, name, salary)
VALUES (1, 'Abdullah', 30000);
```

**বাংলা:** Database-এ নতুন Record বা তথ্য যোগ করাকে Create বলে।

### 2. Read (SELECT)

Read means retrieving or viewing existing records from a database.

```sql
-- Retrieve all records
SELECT * FROM employees;

-- Retrieve a specific record
SELECT * FROM employees
WHERE id = 1;
```

**বাংলা:** Database থেকে সংরক্ষিত তথ্য দেখা বা পড়াকে Read বলে।

### 3. Update (UPDATE)

Update means modifying existing records in a database.

```sql
UPDATE employees
SET salary = 35000
WHERE id = 1;
```

**বাংলা:** Database-এ আগে থেকে থাকা তথ্য পরিবর্তন করাকে Update বলে।

### 4. Delete (DELETE)

Delete means removing existing records from a database.

```sql
DELETE FROM employees
WHERE id = 1;
```

**বাংলা:** Database থেকে কোনো Record মুছে ফেলাকে Delete বলে।

## 3. CRUD Summary

| CRUD | SQL Command | Description |
|---|---|---|
| Create | INSERT | Add new records |
| Read | SELECT | Retrieve records |
| Update | UPDATE | Modify existing records |
| Delete | DELETE | Remove records |

## 4. Important Notes

- CRUD is the foundation of database operations.
- CRUD is used in almost every software application.
- SQL provides commands to perform CRUD operations.
- CRUD operations are commonly implemented in REST APIs.

## 5. CRUD in REST API

| CRUD Operation | HTTP Method | Example Endpoint |
|---|---|---|
| Create | POST | `/api/employees` |
| Read | GET | `/api/employees` |
| Update | PUT / PATCH | `/api/employees/1` |
| Delete | DELETE | `/api/employees/1` |

## 6. Important Warning

Always use a `WHERE` condition when updating or deleting a specific record.

```sql
-- Without WHERE: Updates all records
UPDATE employees
SET salary = 35000;

-- Without WHERE: Deletes all records
DELETE FROM employees;
```

## 7. Remember

**CRUD = Create + Read + Update + Delete**

CRUD is the four fundamental operations for managing records in a database.
# BETWEEN Operator in DBMS (SQL)

## 1. Definition

The `BETWEEN` operator is used to filter records within a specified range of values.

- It is a range-based operator.
- It includes both the starting and ending values (Inclusive).
- Commonly used with numbers, dates, and text.

## 2. Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

- `value1`: Starting value (inclusive).
- `value2`: Ending value (inclusive).

## 3. Example: BETWEEN Operator

**Employees Table**

| ID | Name | Salary |
|---|---|---|
| 1 | Rahim | 20000 |
| 2 | Karim | 30000 |
| 3 | Hasan | 40000 |
| 4 | Sakib | 50000 |
| 5 | Rafi | 60000 |

Find employees whose salary is between 30000 and 50000.

```sql
SELECT *
FROM employees
WHERE salary BETWEEN 30000 AND 50000;
```

**Result:**

| ID | Name | Salary |
|---|---|---|
| 2 | Karim | 30000 |
| 3 | Hasan | 40000 |
| 4 | Sakib | 50000 |

**Important:** Both 30000 and 50000 are included.

## 4. NOT BETWEEN Operator

The `NOT BETWEEN` operator returns records outside the specified range.

```sql
SELECT *
FROM employees
WHERE salary NOT BETWEEN 30000 AND 50000;
```

**Result:**

| ID | Name | Salary |
|---|---|---|
| 1 | Rahim | 20000 |
| 5 | Rafi | 60000 |

## 5. BETWEEN with Dates

Find employees who joined between January 1, 2025 and December 31, 2025.

```sql
SELECT *
FROM employees
WHERE joining_date BETWEEN '2025-01-01' AND '2025-12-31';
```

**Note:** If `joining_date` contains timestamps, the ending date may exclude records after midnight. For timestamp columns, use an exclusive upper boundary:

```sql
SELECT *
FROM employees
WHERE joining_date >= '2025-01-01'
  AND joining_date < '2026-01-01';
```

## 6. BETWEEN vs IN

| BETWEEN | IN |
|---|---|
| Checks a range of values | Checks specific values |
| Uses `AND` | Uses comma-separated values |
| Includes both boundaries | Matches only listed values |

**BETWEEN Example:**

```sql
SELECT *
FROM employees
WHERE salary BETWEEN 20000 AND 50000;
```

**IN Example:**

```sql
SELECT *
FROM employees
WHERE salary IN (20000, 40000, 60000);
```

## 7. BETWEEN vs Comparison Operators

The following queries are equivalent:

```sql
SELECT *
FROM employees
WHERE salary BETWEEN 30000 AND 50000;
```

```sql
SELECT *
FROM employees
WHERE salary >= 30000
  AND salary <= 50000;
```

 # LIKE Operator in DBMS (SQL)

## 1. Definition
The `LIKE` operator is used to search for a specific pattern in a column using wildcard characters.

## 2. Wildcard Characters

| Wildcard | Description | Example |
|---|---|---|
| `%` | Matches zero or more characters | `'A%'` |
| `_` | Matches exactly one character | `'A_'` |

## 3. Examples

```sql
-- Names starting with A
SELECT * FROM employees
WHERE name LIKE 'A%';

-- Names ending with n
SELECT * FROM employees
WHERE name LIKE '%n';

-- Names containing "ah"
SELECT * FROM employees
WHERE name LIKE '%ah%';

-- Names with exactly 4 characters
SELECT * FROM employees
WHERE name LIKE '____';

-- Names where the second character is 'a'
SELECT * FROM employees
WHERE name LIKE '_a%';
```

## 4. NOT LIKE Operator

Used to find records that do not match a specified pattern.

```sql
SELECT * FROM employees
WHERE name NOT LIKE 'A%';
```

## 5. Important Exam Notes

- `%` = Zero or more characters.
- `_` = Exactly one character.
- `LIKE` = Pattern matching.
- `NOT LIKE` = Excludes matching patterns.
- Case sensitivity depends on the database and collation.

# LIMIT Clause in DBMS (SQL)

## 1. Definition
The `LIMIT` clause is used to restrict the number of rows returned by a query.

## 2. Syntax

```sql
SELECT column_name
FROM table_name
LIMIT number;
```

## 3. Examples

```sql
-- Get the first 5 employees
SELECT *
FROM employees
LIMIT 5;

-- Skip first 5 rows and get next 5 rows
SELECT *
FROM employees
LIMIT 5 OFFSET 5;
```

## 4. LIMIT with ORDER BY

```sql
-- Get the top 3 highest-paid employees
SELECT *
FROM employees
ORDER BY salary DESC
LIMIT 3;
```

## 5. Database Compatibility

| Database | Syntax |
|---|---|
| MySQL | `LIMIT 5` |
| PostgreSQL | `LIMIT 5` |
| SQLite | `LIMIT 5` |
| Oracle 12c+ | `FETCH FIRST 5 ROWS ONLY` |
| SQL Server | `TOP 5` or `OFFSET/FETCH` |

## 6. Important Exam Notes

- `LIMIT` restricts the number of returned rows.
- `LIMIT n` returns at most `n` rows.
- `OFFSET n` skips the first `n` rows.
- Use `ORDER BY` with `LIMIT` for predictable results.
- `LIMIT` is supported in MySQL and PostgreSQL but not standard Oracle or SQL Server syntax.

**Remember:** `LIMIT` = Restrict the number of rows returned. 
# Find Second Highest Salary Using Subquery (SQL)

## 1. SQL Query

```sql
SELECT MAX(salary)
FROM employees
WHERE salary < (
    SELECT MAX(salary)
    FROM employees
);
```

## 2. Explanation

1. **Inner Query:** Finds the highest salary using `MAX()`.
2. **Outer Query:** Finds the maximum salary that is less than the highest salary.

## 3. Example

| Employee | Salary |
|---|---:|
| Rahim | 20000 |
| Karim | 30000 |
| Hasan | 40000 |
| Sakib | 50000 |
| Rafi | 60000 |

**Output:**

```text
50000
```

## 4. Query Execution

```sql
-- Step 1: Find highest salary
SELECT MAX(salary)
FROM employees;
-- Output: 60000

-- Step 2: Find second highest salary
SELECT MAX(salary)
FROM employees
WHERE salary < 60000;
-- Output: 50000
```

## 5. Important Notes

- `MAX()` returns the highest value.
- A subquery is a query nested inside another query.
- `<` excludes the highest salary.
- This query finds the second-highest **distinct** salary, even if the highest salary occurs multiple times.
- If there is no second distinct salary, the result is `NULL`.

**Remember:**

Second Highest Salary = `MAX(salary)` where `salary` is less than the highest salary.
# Find Second Minimum Salary Using Subquery (SQL)

## 1. SQL Query

```sql
SELECT MIN(salary)
FROM employees
WHERE salary > (
    SELECT MIN(salary)
    FROM employees
);
```

## 2. Explanation

1. **Inner Query:** Finds the minimum salary using `MIN()`.
2. **Outer Query:** Finds the minimum salary greater than the lowest salary.

## 3. Example

| Employee | Salary |
|---|---:|
| Rahim | 20000 |
| Karim | 30000 |
| Hasan | 40000 |
| Sakib | 50000 |
| Rafi | 60000 |

**Output:**

```text
30000
```

## 4. Query Execution

```sql
-- Step 1: Find minimum salary
SELECT MIN(salary)
FROM employees;
-- Output: 20000

-- Step 2: Find second minimum salary
SELECT MIN(salary)
FROM employees
WHERE salary > 20000;
-- Output: 30000
```

## 5. Important Notes

- `MIN()` returns the lowest value.
- `>` excludes the minimum salary.
- This query finds the second-lowest **distinct salary**.
- Duplicate minimum salaries are ignored.
- If no second distinct salary exists, the result is `NULL`.

## Remember

**Second Minimum Salary = MIN(salary) greater than the minimum salary.**
# CREATE VIEW in DBMS (SQL)

## 1. Definition

A **VIEW** is a virtual table created from the result of an SQL query.

- A VIEW usually does not store data separately.
- It displays data from one or more existing tables.
- Changes in the original table are reflected in the VIEW.

## 2. Syntax

```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;
```

## 3. Example: Create a VIEW

**Employees Table**

| ID | Name | Salary | Department |
|---|---|---:|---|
| 1 | Rahim | 30000 | IT |
| 2 | Karim | 40000 | HR |
| 3 | Hasan | 50000 | IT |

Create a VIEW for IT department employees.

```sql
CREATE VIEW it_employees AS
SELECT id, name, salary
FROM employees
WHERE department = 'IT';
```

## 4. Retrieve Data from VIEW

```sql
SELECT * FROM it_employees;
```

**Output:**

| ID | Name | Salary |
|---|---|---:|
| 1 | Rahim | 30000 |
| 3 | Hasan | 50000 |

**Explanation:** `it_employees` behaves like a table, but it is a VIEW based on the original `employees` table.

## 5. CREATE OR REPLACE VIEW

Used to create a VIEW or replace its existing definition.

```sql
CREATE OR REPLACE VIEW it_employees AS
SELECT id, name, salary, department
FROM employees
WHERE department = 'IT';
```

## 6. DROP VIEW

Used to delete a VIEW.

```sql
DROP VIEW it_employees;
```

**Note:** It deletes only the VIEW definition, not the original table or its data.

## 7. Advantages of VIEW

| Advantage | Explanation |
|---|---|
| Security | Restricts access to selected rows or columns |
| Simplicity | Simplifies complex SQL queries |
| Reusability | Reuses frequently executed queries |
| Data Abstraction | Hides unnecessary table details |

## 8. VIEW vs TABLE

| VIEW | TABLE |
|---|---|
| Virtual table | Physical database table |
| Usually does not store data separately | Stores actual data |
| Based on SQL query | Stores records directly |
| Created using `CREATE VIEW` | Created using `CREATE TABLE` |

## 9. Important Exam Notes

1. VIEW is also called a Virtual Table.
2. `CREATE VIEW` is used to create a VIEW.
3. A VIEW can be created from one or multiple tables.
4. A normal VIEW stores its query definition, not a separate copy of data.
5. Changes in the original table are reflected in the VIEW.
6. Some simple views support `INSERT`, `UPDATE`, and `DELETE`, subject to database restrictions.
7. A Materialized VIEW physically stores query results.

## Remember

**VIEW = Virtual Table + SQL Query**

# Sequence in DBMS (Oracle)

## 1. What is a Sequence?

A **Sequence** is a database object used to automatically generate numeric values, commonly used for generating Primary Keys (IDs).

**Example:** Employee ID, Customer ID, Account ID, etc.

Instead of manually inserting IDs, a Sequence generates them automatically.

## 2. Create Sequence

```sql
CREATE SEQUENCE emp_seq
START WITH 1
INCREMENT BY 1
MINVALUE 1
MAXVALUE 100
NOCYCLE;
```

### Explanation

| Keyword | Description |
|---|---|
| START WITH | Starting value |
| INCREMENT BY | Value increase per execution |
| MINVALUE | Minimum allowed value |
| MAXVALUE | Maximum allowed value |
| CACHE | Stores sequence values in memory |
| NOCACHE | Does not cache sequence values |
| CYCLE | Restarts after reaching the maximum |
| NOCYCLE | Does not restart after reaching the maximum |

## 3. NEXTVAL

`NEXTVAL` generates and returns the next sequence value.

```sql
SELECT emp_seq.NEXTVAL FROM dual;
```

**Output (successive executions):**

```text
1
2
3
4
5
```

Each execution generates a new value.

## 4. CURRVAL

`CURRVAL` returns the last generated sequence value in the current session.

```sql
SELECT emp_seq.CURRVAL FROM dual;
```

**Example:**

If the last `NEXTVAL` returned `5`, then:

```text
CURRVAL = 5
```

**Note:** You must execute `NEXTVAL` before using `CURRVAL` in the same session.

## 5. Practical Example: Employee Table

### Step 1: Create Table

```sql
CREATE TABLE employees (
    emp_id NUMBER PRIMARY KEY,
    emp_name VARCHAR2(50),
    salary NUMBER
);
```

### Step 2: Create Sequence

```sql
CREATE SEQUENCE emp_seq
START WITH 1
INCREMENT BY 1;
```

### Step 3: Insert Data Using Sequence

```sql
INSERT INTO employees (emp_id, emp_name, salary)
VALUES (emp_seq.NEXTVAL, 'Mamun', 30000);

INSERT INTO employees (emp_id, emp_name, salary)
VALUES (emp_seq.NEXTVAL, 'Rahim', 35000);

INSERT INTO employees (emp_id, emp_name, salary)
VALUES (emp_seq.NEXTVAL, 'Karim', 40000);
```

### Step 4: View Data

```sql
SELECT * FROM employees;
```

**Expected Output:**

| EMP_ID | EMP_NAME | SALARY |
|---:|---|---:|
| 1 | Mamun | 30000 |
| 2 | Rahim | 35000 |
| 3 | Karim | 40000 |

The Sequence automatically generates employee IDs.

## 6. ALTER SEQUENCE

Used to modify sequence properties.

```sql
ALTER SEQUENCE emp_seq
INCREMENT BY 2;
```

If the last generated value was `3`, subsequent values will be:

```text
5, 7, 9, 11...
```

## 7. DROP SEQUENCE

Used to delete a Sequence.

```sql
DROP SEQUENCE emp_seq;
```

**Note:** Dropping a Sequence does not delete existing table records.

## 8. NEXTVAL vs CURRVAL

| NEXTVAL | CURRVAL |
|---|---|
| Generates the next value | Returns the current value |
| Changes sequence value | Does not change sequence value |
| Used to generate new IDs | Used to retrieve the last generated ID |

## 9. Important Interview Questions

**Q1. What is a Sequence?**

An object used to generate numeric values automatically.

**Q2. What is NEXTVAL?**

Generates and returns the next sequence value.

**Q3. What is CURRVAL?**

Returns the last generated sequence value in the current session.

**Q4. Can multiple users use the same Sequence?**

Yes, multiple users can access the same Sequence.

**Q5. Are Sequence values rolled back after ROLLBACK?**

No. Sequence values are not transactional.

**Q6. Does a Sequence guarantee gap-free numbers?**

No. Gaps may occur due to rollbacks, caching, or unused values.

**Q7. Is a Sequence automatically associated with a Primary Key?**

No. It must be explicitly used in an INSERT statement or configured as a column default.

## 10. Quick Revision

| Command | Purpose |
|---|---|
| `CREATE SEQUENCE` | Create a Sequence |
| `NEXTVAL` | Generate next value |
| `CURRVAL` | Get current session value |
| `ALTER SEQUENCE` | Modify Sequence |
| `DROP SEQUENCE` | Delete Sequence |

# Trigger in DBMS (Oracle)

## 1. What is a Trigger?

A **Trigger** is a database object that automatically executes when a specific database event occurs.

**Common Uses:**
- Automatically maintain audit logs.
- Track INSERT, UPDATE and DELETE operations.
- Validate data before insertion.
- Maintain data consistency.

## 2. Types of Triggers

### Based on Execution Time

| Type | Description |
|---|---|
| BEFORE | Executes before a database operation |
| AFTER | Executes after a database operation |
| INSTEAD OF | Executes instead of an operation, commonly on views |

### Based on Execution Level

| Type | Description |
|---|---|
| Row-Level | Executes for each affected row |
| Statement-Level | Executes once per SQL statement |

## 3. Create Table

```sql
CREATE TABLE employees (
    emp_id NUMBER PRIMARY KEY,
    emp_name VARCHAR2(50),
    salary NUMBER
);
```

## 4. BEFORE INSERT Trigger

Executes before inserting a new record.

```sql
CREATE OR REPLACE TRIGGER before_emp_insert
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
    DBMS_OUTPUT.PUT_LINE('Before inserting employee');
END;
/
```

**Example:**

```sql
INSERT INTO employees
VALUES (1, 'Mamun', 30000);
```

**Output:**
```text
Before inserting employee
```

## 5. AFTER INSERT Trigger

Executes after inserting a new record.

```sql
CREATE OR REPLACE TRIGGER after_emp_insert
AFTER INSERT ON employees
FOR EACH ROW
BEGIN
    DBMS_OUTPUT.PUT_LINE('Employee inserted successfully');
END;
/
```

## 6. BEFORE UPDATE Trigger

Executes before updating a record.

```sql
CREATE OR REPLACE TRIGGER before_emp_update
BEFORE UPDATE ON employees
FOR EACH ROW
BEGIN
    DBMS_OUTPUT.PUT_LINE('Employee data is being updated');
END;
/
```

**Example:**

```sql
UPDATE employees
SET salary = 40000
WHERE emp_id = 1;
```

## 7. OLD and NEW Keywords

Oracle provides two special references in row-level triggers.

| Keyword | Description |
|---|---|
| `:OLD` | Previous column value |
| `:NEW` | New column value |

**Example:**

```sql
CREATE OR REPLACE TRIGGER check_salary_update
BEFORE UPDATE OF salary ON employees
FOR EACH ROW
BEGIN
    DBMS_OUTPUT.PUT_LINE('Old Salary: ' || :OLD.salary);
    DBMS_OUTPUT.PUT_LINE('New Salary: ' || :NEW.salary);
END;
/
```

**Execute:**

```sql
UPDATE employees
SET salary = 45000
WHERE emp_id = 1;
```

**Output:**
```text
Old Salary: 30000
New Salary: 45000
```

**Remember:**
- `:OLD` = Previous value
- `:NEW` = New value

## 8. Practical Example: Salary Audit Trigger

Whenever an employee's salary changes, automatically store the old and new salary in an audit table.

### Step 1: Create Audit Table

```sql
CREATE TABLE salary_audit (
    emp_id NUMBER,
    old_salary NUMBER,
    new_salary NUMBER,
    changed_date DATE
);
```

### Step 2: Create Trigger

```sql
CREATE OR REPLACE TRIGGER salary_audit_trigger
AFTER UPDATE OF salary ON employees
FOR EACH ROW
BEGIN
    INSERT INTO salary_audit
    VALUES (
        :OLD.emp_id,
        :OLD.salary,
        :NEW.salary,
        SYSDATE
    );
END;
/
```

### Step 3: Update Salary

```sql
UPDATE employees
SET salary = 50000
WHERE emp_id = 1;
```

### Step 4: Check Audit Table

```sql
SELECT * FROM salary_audit;
```

**Expected Output:**

| EMP_ID | OLD_SALARY | NEW_SALARY |
|---|---:|---:|
| 1 | 30000 | 50000 |

**Explanation:** The trigger automatically inserts salary-change information into the audit table.

## 9. DELETE Trigger

Executes after deleting a record.

```sql
CREATE OR REPLACE TRIGGER after_emp_delete
AFTER DELETE ON employees
FOR EACH ROW
BEGIN
    DBMS_OUTPUT.PUT_LINE(
        'Deleted Employee: ' || :OLD.emp_name
    );
END;
/
```

**Example:**

```sql
DELETE FROM employees
WHERE emp_id = 1;
```

For DELETE operations:
- `:OLD` contains the deleted row's previous values.
- `:NEW` is not available.

## 10. Enable, Disable and Drop Trigger

**Disable Trigger:**

```sql
ALTER TRIGGER salary_audit_trigger DISABLE;
```

**Enable Trigger:**

```sql
ALTER TRIGGER salary_audit_trigger ENABLE;
```

**Drop Trigger:**

```sql
DROP TRIGGER salary_audit_trigger;
```

