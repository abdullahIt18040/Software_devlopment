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

A VIEW provides a customized way to display data from existing database tables.
