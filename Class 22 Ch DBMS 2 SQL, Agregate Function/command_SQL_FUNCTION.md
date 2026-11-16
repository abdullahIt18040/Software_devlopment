## function in sql
<img width="542" height="257" alt="image" src="https://github.com/user-attachments/assets/055aa2c7-40be-4148-b949-f56d630f1043" />
# SQL Commands in RDBMS

## What is SQL?
**SQL (Structured Query Language)** is used to create, manage, manipulate, and retrieve data from a Relational Database Management System (RDBMS).

## Types of SQL Commands

SQL commands are divided into **5 categories**:

### 1. DDL (Data Definition Language)
Used to define or modify database structures.

| Command | Description |
|---|---|
| CREATE | Creates database or table |
| ALTER | Modifies table structure |
| DROP | Deletes database or table |
| TRUNCATE | Deletes all records from a table |
| RENAME | Renames a table |

```sql
CREATE TABLE Student (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT
);

ALTER TABLE Student ADD email VARCHAR(100);
Alter table student Drop column eamil varchar(200); 
TRUNCATE TABLE Student;

DROP TABLE Student;
```

### 2. DML (Data Manipulation Language)
Used to insert, update, and delete records.

| Command | Description |
|---|---|
| INSERT | Inserts new records |
| UPDATE | Updates existing records |
| DELETE | Deletes records |

```sql
INSERT INTO Student VALUES (1, 'Mamun', 27);

UPDATE Student
SET age = 28
WHERE id = 1;

DELETE FROM Student
WHERE id = 1;
```

### 3. DQL (Data Query Language)
Used to retrieve data from database tables.

| Command | Description |
|---|---|
| SELECT | Retrieves records |

```sql
SELECT * FROM Student;

SELECT name, age
FROM Student
WHERE age > 20;
```
# DQL (Data Query Language) – DBMS

## 1. What is DQL?

**DQL (Data Query Language)** is a subset of SQL used to retrieve or fetch data from database tables.

**বাংলায়:** DQL ব্যবহার করে Database থেকে প্রয়োজনীয় তথ্য খুঁজে বের করা এবং প্রদর্শন করা হয়।

**Main DQL Command:** `SELECT`

## 2. SELECT Statement

The `SELECT` statement is used to retrieve data from one or more database tables.

### Syntax

```sql
SELECT column1, column2, ...
FROM table_name;
```

### Example

Suppose we have the following `students` table:

| id | name | age | department |
|---:|---|---:|---|
| 1 | Abdullah | 27 | ICT |
| 2 | Rahim | 22 | CSE |
| 3 | Karim | 24 | ICT |
| 4 | Hasan | 21 | SWE |

```sql
-- Retrieve all columns and rows
SELECT * FROM students;

-- Retrieve specific columns
SELECT name, age FROM students;
```

## 3. SELECT with WHERE

The `WHERE` clause filters records based on a specified condition.

```sql
-- Find students older than 22
SELECT *
FROM students
WHERE age > 22;
```

**Output:**

| id | name | age | department |
|---:|---|---:|---|
| 1 | Abdullah | 27 | ICT |
| 3 | Karim | 24 | ICT |

## 4. SELECT with DISTINCT

`DISTINCT` removes duplicate values from the query result.

```sql
SELECT DISTINCT department
FROM students;
```

**Output:**

| department |
|---|
| ICT |
| CSE |
| SWE |

## 5. SELECT with ORDER BY

`ORDER BY` sorts query results in ascending or descending order.

```sql
-- Ascending order
SELECT * FROM students
ORDER BY age ASC;

-- Descending order
SELECT * FROM students
ORDER BY age DESC;
```

- `ASC` = Ascending (Default)
- `DESC` = Descending

## 6. SELECT with GROUP BY

`GROUP BY` groups rows that have the same values in specified columns. It is commonly used with aggregate functions.

```sql
SELECT department, COUNT(*) AS total_students
FROM students
GROUP BY department;
```

**Output:**

| department | total_students |
|---|---:|
| ICT | 2 |
| CSE | 1 |
| SWE | 1 |

## 7. SELECT with HAVING

`HAVING` filters grouped results, usually after applying `GROUP BY`.

```sql
SELECT department, COUNT(*) AS total_students
FROM students
GROUP BY department
HAVING COUNT(*) > 1;
```

**Output:**

| department | total_students |
|---|---:|
| ICT | 2 |

**Remember:**
- `WHERE` filters rows before grouping.
- `HAVING` filters groups after grouping.

## 8. SELECT with Aggregate Functions

Aggregate functions perform calculations on multiple rows and return a single result per group or query.

| Function | Description |
|---|---|
| COUNT() | Counts rows or non-NULL values |
| SUM() | Calculates total |
| AVG() | Calculates average |
| MAX() | Returns maximum value |
| MIN() | Returns minimum value |

### Examples

```sql
-- Total number of students
SELECT COUNT(*) FROM students;

-- Average age
SELECT AVG(age) FROM students;

-- Maximum age
SELECT MAX(age) FROM students;

-- Minimum age
SELECT MIN(age) FROM students;
```

## 9. SELECT with LIMIT

`LIMIT` restricts the number of rows returned. It is supported by PostgreSQL and MySQL.

```sql
-- Retrieve only 2 students
SELECT *
FROM students
LIMIT 2;
```

## 10. Important DQL Clauses

| Clause | Purpose |
|---|---|
| SELECT | Specifies columns to retrieve |
| FROM | Specifies the source table |
| WHERE | Filters rows |
| DISTINCT | Removes duplicate result rows |
| GROUP BY | Groups rows |
| HAVING | Filters grouped results |
| ORDER BY | Sorts results |
| LIMIT | Restricts returned rows |

# Aggregate Functions in SQL (DBMS)

## 1. What is an Aggregate Function?

An **Aggregate Function** is a SQL function that performs calculations on a set of rows and returns a single result.

**বাংলায়:** Aggregate Function হলো SQL-এর এমন একটি Function, যা একাধিক Row-এর Data নিয়ে হিসাব করে একটি Summary Result প্রদান করে।

## 2. Types of Aggregate Functions

| Function | Description | Example |
|---|---|---|
| `COUNT()` | Counts rows or non-NULL values | Total employees |
| `SUM()` | Calculates the total sum | Total salary |
| `AVG()` | Calculates the average | Average salary |
| `MAX()` | Returns the maximum value | Highest salary |
| `MIN()` | Returns the minimum value | Lowest salary |

## 3. Example Table: Employees

| emp_id | name | department | salary |
|---:|---|---|---:|
| 1 | Abdullah | IT | 50000 |
| 2 | Rahim | HR | 30000 |
| 3 | Karim | IT | 60000 |
| 4 | Hasan | HR | 40000 |
| 5 | Mamun | IT | 70000 |

## 4. COUNT() Function

`COUNT()` counts the number of rows or non-NULL values.
IF COLUMN value is null , then it will ignore .
**Syntax:**

```sql
SELECT COUNT(column_name)
FROM table_name;
```

**Examples:**

```sql
-- Count all employees
SELECT COUNT(*)
FROM employees;

-- Count non-NULL salary values
SELECT COUNT(salary)
FROM employees;
```

**Output:** `5`

## 5. SUM() Function

`SUM()` calculates the total sum of a numeric column.

```sql
SELECT SUM(salary) AS total_salary
FROM employees;
```

**Output:** `250000`

## 6. AVG() Function

`AVG()` calculates the average value of a numeric column.

```sql
SELECT AVG(salary) AS average_salary
FROM employees;
```

**Output:** `50000`

## 7. MAX() Function

`MAX()` returns the maximum value from a column.

```sql
SELECT MAX(salary) AS highest_salary
FROM employees;
```

**Output:** `70000`

## 8. MIN() Function

`MIN()` returns the minimum value from a column.

```sql
SELECT MIN(salary) AS lowest_salary
FROM employees;
```

**Output:** `30000`

## 9. Aggregate Functions with GROUP BY

`GROUP BY` groups rows based on common column values and applies aggregate functions to each group.

**Example: Calculate total salary by department.**

```sql
SELECT
    department,
    SUM(salary) AS total_salary
FROM employees
GROUP BY department;
```

**Output:**

| department | total_salary |
|---|---:|
| IT | 180000 |
| HR | 70000 |

## 10. Aggregate Functions with HAVING

`HAVING` filters grouped results based on aggregate conditions.

**Example: Find departments whose average salary is greater than 40000.**

```sql
SELECT
    department,
    AVG(salary) AS average_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 40000;
```

**Output:**

| department | average_salary |
|---|---:|
| IT | 60000 |

## 11. All Aggregate Functions in One Query

```sql
SELECT
    COUNT(*) AS total_employees,
    SUM(salary) AS total_salary,
    AVG(salary) AS average_salary,
    MAX(salary) AS highest_salary,
    MIN(salary) AS lowest_salary
FROM employees;
```

**Output:**

| total_employees | total_salary | average_salary | highest_salary | lowest_salary |
|---:|---:|---:|---:|---:|
| 5 | 250000 | 50000 | 70000 | 30000 |



### 4. DCL (Data Control Language)
Used to control database access and permissions.

| Command | Description |
|---|---|
| GRANT | Gives privileges |
| REVOKE | Removes privileges |

```sql
GRANT SELECT, INSERT ON Student TO user1;

REVOKE INSERT ON Student FROM user1;
```

### 5. TCL (Transaction Control Language)
Used to manage database transactions.
Database Transaction হলো এক বা একাধিক SQL operation-এর সমষ্টি, যা একটি নির্দিষ্ট কাজ সম্পন্ন করে। Transaction সফল হলে সব পরিবর্তন কার্যকর হবে, আর ব্যর্থ হলে কোনো পরিবর্তন কার্যকর হবে না।
# Database Transaction (DBMS)

## 1. What is a Transaction?

A **Transaction** is set of  SQL operations (INSERT, UPDATE, DELETE, SELECT) that perform a specific task.


**বাংলায়:** Transaction হলো এক বা একাধিক SQL operation-এর সমষ্টি, যা একটি নির্দিষ্ট কাজ সম্পন্ন করে। সব operation সফল হবে অথবা কোনো পরিবর্তনই কার্যকর হবে না।

## 2. Example of Database Transaction

**Scenario:** Transfer 1000 টাকা from Account A to Account B.

```sql
BEGIN TRANSACTION;

UPDATE accounts
SET balance = balance - 1000
WHERE account_id = 101;

UPDATE accounts
SET balance = balance + 1000
WHERE account_id = 102;

COMMIT;
```

If any operation fails:

```sql
ROLLBACK;
```

## 3. ACID Properties of Transaction

ACID represents four important properties of database transactions.

### A. Atomicity (অখণ্ডতা)
- All operations succeed or none.
- Either the entire transaction is completed or nothing happens.
- Example: Money transfer must debit and credit successfully.

### C. Consistency (সামঞ্জস্যতা)
- Database must remain valid before and after a transaction.
- All database constraints and rules must be maintained.

### I. Isolation (স্বতন্ত্রতা)
- Concurrent transactions should not interfere with each other.
- Each transaction should execute independently.

### D. Durability (স্থায়িত্ব)
- Once a transaction is committed, changes are permanent.
- Data remains saved even after a system crash.

## 4. Transaction Control Commands (TCL)

| Command | Description |
|---|---|
| `BEGIN` | Starts a transaction |
| `START TRANSACTION` | Starts a transaction |
| `COMMIT` | Permanently saves changes |
| `ROLLBACK` | Cancels uncommitted changes |
| `SAVEPOINT` | Creates a rollback point |
| `ROLLBACK TO` | Rolls back to a specific savepoint |

## 5. SAVEPOINT Example

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 500
WHERE account_id = 101;

SAVEPOINT sp1;

UPDATE accounts
SET balance = balance + 500
WHERE account_id = 102;

ROLLBACK TO sp1;

COMMIT;
```

**Explanation:**
- `SAVEPOINT sp1` creates a temporary rollback point.
- `ROLLBACK TO sp1` cancels operations performed after that savepoint.
- `COMMIT` saves the remaining transaction changes.

## 6. Types of Transaction

1. **Read-only Transaction:** Only retrieves data.
2. **Read-write Transaction:** Reads and modifies data.
3. **Distributed Transaction:** Executes operations across multiple databases or systems.

## 7. Real-Life Examples

- Bank Money Transfer
- Money Deposit
- Money Withdrawal
- Online Shopping Order
- Payment Processing

## 8. Important Exam Notes

- ACID = Atomicity + Consistency + Isolation + Durability.
- Atomicity = All or Nothing.
- COMMIT = Permanently save changes.
- ROLLBACK = Cancel uncommitted changes.
- SAVEPOINT = Creates an intermediate rollback point.
- Isolation = Prevents unwanted interference between concurrent transactions.
- Durability = Committed changes are permanent.
- TCL = Transaction Control Language.

## 9. Quick Revision

| Property | Meaning |
|---|---|
| Atomicity | All or Nothing |
| Consistency | Maintains Database Rules |
| Isolation | Independent Execution |
| Durability | Permanent Changes |

**Remember:** Database Transaction ensures data integrity, consistency, and reliability.
# Transaction is set of operation that performs a sprcific task.

| Command | Description |
|---|---|
| COMMIT | Permanently saves changes |
| ROLLBACK | Undoes uncommitted changes |
| SAVEPOINT | Creates a transaction checkpoint |
| SET TRANSACTION | Sets transaction properties |

```sql
UPDATE Student
SET age = 30
WHERE id = 1;

SAVEPOINT sp1;

DELETE FROM Student WHERE id = 1;

ROLLBACK TO sp1;

COMMIT;
```

---
# Database Schema (DBMS)

## 1. What is a Schema?

A **Database Schema** is the logical structure or blueprint of a database that defines how data is organized, stored, and related.

**বাংলায়:** Database Schema হলো Database-এর কাঠামো বা নকশা, যেখানে Table, Column, Data Type, Relationship এবং Constraints নির্ধারণ করা হয়।

## 2. Example of Database Schema

Suppose we have a Student Database.

### Student Table

| Column | Data Type |
|---|---|
| student_id | INT (Primary Key) |
| name | VARCHAR(100) |
| email | VARCHAR(100) |
| age | INT |
| department_id | INT (Foreign Key) |

### SQL Example

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    age INT,
    department_id INT
);
```

The table structure represents a part of the database schema.



## 4. Schema vs Instance


- Schema = Database Blueprint.
- Instance = Actual data stored in the database at a particular time.


