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

# SQL IN and NOT IN Operators (DBMS)

## 1. IN Operator

The **IN operator** is used to check whether a value matches any value in a specified list.

**বাংলায়:** IN Operator ব্যবহার করে একটি Column-এর Value নির্দিষ্ট List-এর যেকোনো Value-এর সাথে মিলে কি না তা পরীক্ষা করা হয়।

### Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name IN (value1, value2, ...);
```

### Example Table: Employees

| emp_id | name | department | salary |
|---:|---|---|---:|
| 1 | Abdullah | IT | 50000 |
| 2 | Rahim | HR | 30000 |
| 3 | Karim | IT | 60000 |
| 4 | Hasan | HR | 40000 |
| 5 | Mamun | Sales | 70000 |
| 6 | Sakib | Sales | 35000 |

### Example 1: Find employees from IT and HR departments.

```sql
SELECT *
FROM employees
WHERE department IN ('IT', 'HR');
```

**Output:** Abdullah, Rahim, Karim, Hasan.

### Example 2: Find employees having salary 30000, 50000 or 70000.

```sql
SELECT *
FROM employees
WHERE salary IN (30000, 50000, 70000);
```

**Output:** Rahim, Abdullah, Mamun.

## 2. NOT IN Operator

The **NOT IN operator** is used to retrieve records whose values do not match any value in a specified list.

**বাংলায়:** NOT IN Operator ব্যবহার করে নির্দিষ্ট List-এর Value বাদ দিয়ে বাকি Records বের করা হয়।

### Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name NOT IN (value1, value2, ...);
```

### Example 1: Find employees who are NOT from IT and HR departments.

```sql
SELECT *
FROM employees
WHERE department NOT IN ('IT', 'HR');
```

**Output:** Mamun, Sakib (Sales).

### Example 2: Find employees whose salary is NOT 30000, 50000 or 70000.

```sql
SELECT *
FROM employees
WHERE salary NOT IN (30000, 50000, 70000);
```

**Output:** Karim, Hasan, Sakib.

## 3. IN vs NOT IN

| IN | NOT IN |
|---|---|
| Matches values in a list | Excludes values in a list |
| Returns matching records | Returns non-matching records |
| Equivalent to multiple OR conditions | Equivalent to multiple AND conditions |

### IN = OR Logic

```sql
SELECT *
FROM employees
WHERE department = 'IT'
   OR department = 'HR';

-- Equivalent to:
SELECT *
FROM employees
WHERE department IN ('IT', 'HR');
```

### NOT IN = AND Logic

```sql
SELECT *
FROM employees
WHERE department != 'IT'
  AND department != 'HR';

-- Equivalent to:
SELECT *
FROM employees
WHERE department NOT IN ('IT', 'HR');
```

## 4. IN with Subquery

IN can also be used with a subquery to retrieve records based on another query's result.

**Example:** Find employees who belong to departments located in Dhaka.

```sql
SELECT *
FROM employees
WHERE department IN (
    SELECT department_name
    FROM departments
    WHERE location = 'Dhaka'
);
```

## 5. NOT IN with Subquery

**Example:** Find employees who do not belong to departments located in Dhaka.

```sql
SELECT *
FROM employees
WHERE department NOT IN (
    SELECT department_name
    FROM departments
    WHERE location = 'Dhaka'
);
```

## 6. Important NULL Concept

Be careful when using `NOT IN` with NULL values.

```sql
SELECT *
FROM employees
WHERE department NOT IN ('IT', NULL);
```

**Result:** Generally, no rows are returned because comparisons involving NULL produce UNKNOWN.

**Important:** When using `NOT IN` with a subquery, ensure the returned column does not contain NULL values. Alternatively, use `NOT EXISTS`.



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
# SQL EXISTS and NOT EXISTS

SQL-এর `EXISTS` এবং `NOT EXISTS` হলো Subquery-এর সাথে ব্যবহৃত দুটি operator। এগুলো নির্দিষ্ট শর্ত অনুযায়ী অন্য একটি query-তে matching record আছে কি না, তা পরীক্ষা করে।

## 1. EXISTS Operator

`EXISTS` subquery কমপক্ষে একটি row return করলে `TRUE` return করে।

**Example Tables**

**employees**

| id | name | department_id |
|---|---|---|
| 1 | Mamun | 10 |
| 2 | Rahim | 20 |
| 3 | Karim | 30 |

**departments**

| id | department_name |
|---|---|
| 10 | IT |
| 20 | HR |

**Query:**

```sql
SELECT *
FROM employees e
WHERE EXISTS (
    SELECT 1
    FROM departments d
    WHERE d.id = e.department_id
);
```

**Result:**

| id | name | department_id |
|---|---|---|
| 1 | Mamun | 10 |
| 2 | Rahim | 20 |

**Explanation (Bangla):**

- Mamun-এর department_id = 10, departments table-এ আছে।
- Rahim-এর department_id = 20, departments table-এ আছে।
- Karim-এর department_id = 30, departments table-এ নেই।

তাই শুধু Mamun এবং Rahim return করবে।

## 2. NOT EXISTS Operator

`NOT EXISTS` subquery কোনো row return না করলে `TRUE` return করে।

**Query:**

```sql
SELECT *
FROM employees e
WHERE NOT EXISTS (
    SELECT 1
    FROM departments d
    WHERE d.id = e.department_id
);
```

**Result:**

| id | name | department_id |
|---|---|---|
| 3 | Karim | 30 |

**Explanation (Bangla):**

Karim-এর department_id = 30, কিন্তু departments table-এ এই ID নেই। তাই শুধু Karim return করবে।

## 3. EXISTS vs NOT EXISTS

| EXISTS | NOT EXISTS |
|---|---|
| Matching row থাকলে TRUE | Matching row না থাকলে TRUE |
| At least one row পাওয়া যায় | কোনো row পাওয়া যায় না |
| Matching records return করে | Non-matching records return করে |

## 4. Important Points

- `EXISTS` শুধু পরীক্ষা করে subquery কোনো row return করছে কি না।
- `SELECT 1` ব্যবহার করা হয় কারণ এখানে selected value নয়, row existence গুরুত্বপূর্ণ।
- `EXISTS` এবং `NOT EXISTS` প্রায়ই Correlated Subquery-এর সাথে ব্যবহৃত হয়।
- `NOT EXISTS`-এ `NOT IN`-এর মতো subquery-র NULL value-এর কারণে UNKNOWN সমস্যা হয় না।
- Subquery-এর ফলাফলের মধ্যে NULL থাকলেও `NOT EXISTS` সঠিকভাবে কাজ করে।

## 5. Job Exam Key Notes

```sql
-- EXISTS: Find employees having a valid department
SELECT *
FROM employees e
WHERE EXISTS (
    SELECT 1
    FROM departments d
    WHERE d.id = e.department_id
);

-- NOT EXISTS: Find employees without a valid department
SELECT *
FROM employees e
WHERE NOT EXISTS (
    SELECT 1
    FROM departments d
    WHERE d.id = e.department_id
);
```

**Remember:**

- `EXISTS` = Matching record আছে কি না?
- `NOT EXISTS` = Matching record নেই কি না?
- `EXISTS` returns TRUE if at least one row exists.
- `NOT EXISTS` returns TRUE if no row exists.

## 6. Practice MCQ

**Q1. EXISTS কখন TRUE return করে?**

- [x] Subquery কোনো row return করলে
- [ ] Subquery কোনো row return না করলে
- [ ] শুধু NULL থাকলে
- [ ] সবসময়

**Answer:** At least one row পাওয়া গেলে EXISTS TRUE হয়।

**Q2. NOT EXISTS কখন TRUE return করে?**

- [ ] একটি matching row থাকলে
- [x] কোনো row return না করলে
- [ ] সব row NULL হলে
- [ ] সবসময়

**Answer:** Subquery কোনো row return না করলে NOT EXISTS TRUE হয়।

**Q3. EXISTS-এর ক্ষেত্রে SELECT 1 কেন ব্যবহার করা হয়?**

- [ ] ১ সংখ্যাটি count করার জন্য
- [x] শুধু row existence পরীক্ষা করার জন্য
- [ ] প্রথম row delete করার জন্য
- [ ] NULL বাদ দেওয়ার জন্য

**Answer:** EXISTS-এর ক্ষেত্রে selected value নয়, row পাওয়া যাচ্ছে কি না সেটি গুরুত্বপূর্ণ।

---

# SQL JOIN

SQL-এর `JOIN` ব্যবহার করে দুই বা ততোধিক table-এর মধ্যে সম্পর্কযুক্ত column-এর ভিত্তিতে data একসাথে retrieve করা যায়।

**Definition:** JOIN is used to retrieve related data from two or more tables based on a related column between them.

## 1. Types of SQL JOIN

SQL JOIN প্রধানত চার ধরনের:

1. INNER JOIN
2. LEFT JOIN (LEFT OUTER JOIN)
3. RIGHT JOIN (RIGHT OUTER JOIN)
4. FULL OUTER JOIN

## 2. Example Tables

**employees**

| id | name | dept_id |
|---|---|---|
| 1 | Mamun | 10 |
| 2 | Rahim | 20 |
| 3 | Karim | 30 |
| 4 | Hasan | NULL |

**departments**

| id | dept_name |
|---|---|
| 10 | IT |
| 20 | HR |
| 40 | Finance |

## 3. INNER JOIN

INNER JOIN returns only matching records from both tables.

**Syntax:**

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

**Example:**

```sql
SELECT e.id, e.name, d.dept_name
FROM employees e
INNER JOIN departments d
ON e.dept_id = d.id;
```

**Result:**

| id | name | dept_name |
|---|---|---|
| 1 | Mamun | IT |
| 2 | Rahim | HR |

**Explanation (Bangla):**

শুধুমাত্র যেসব employee-এর `dept_id` এবং departments table-এর `id` match করে, তাদের দেখাবে।

## 4. LEFT JOIN (LEFT OUTER JOIN)

LEFT JOIN returns all records from the left table and matching records from the right table.

No matching record হলে right table-এর column-এ `NULL` দেখাবে।

**Example:**

```sql
SELECT e.id, e.name, d.dept_name
FROM employees e
LEFT JOIN departments d
ON e.dept_id = d.id;
```

**Result:**

| id | name | dept_name |
|---|---|---|
| 1 | Mamun | IT |
| 2 | Rahim | HR |
| 3 | Karim | NULL |
| 4 | Hasan | NULL |

**Explanation (Bangla):**

Left table অর্থাৎ `employees`-এর সব records দেখাবে। Matching department না থাকলে department name `NULL` হবে।

## 5. RIGHT JOIN (RIGHT OUTER JOIN)

RIGHT JOIN returns all records from the right table and matching records from the left table.

No matching record হলে left table-এর column-এ `NULL` দেখাবে।

**Example:**

```sql
SELECT e.id, e.name, d.dept_name
FROM employees e
RIGHT JOIN departments d
ON e.dept_id = d.id;
```

**Result:**

| id | name | dept_name |
|---|---|---|
| 1 | Mamun | IT |
| 2 | Rahim | HR |
| NULL | NULL | Finance |

**Explanation (Bangla):**

Right table অর্থাৎ `departments`-এর সব records দেখাবে। Matching employee না থাকলে employee-এর column-এ `NULL` হবে।

## 6. FULL OUTER JOIN

FULL OUTER JOIN returns all records from both tables.

Matching না থাকলে সংশ্লিষ্ট table-এর column-এ `NULL` দেখাবে।

**Example:**

```sql
SELECT e.id, e.name, d.dept_name
FROM employees e
FULL OUTER JOIN departments d
ON e.dept_id = d.id;
```

**Result:**

| id | name | dept_name |
|---|---|---|
| 1 | Mamun | IT |
| 2 | Rahim | HR |
| 3 | Karim | NULL |
| 4 | Hasan | NULL |
| NULL | NULL | Finance |

**Explanation (Bangla):**

দুই table-এর matching এবং non-matching সব records দেখাবে।

**Note:** PostgreSQL supports `FULL OUTER JOIN`, but MySQL does not directly support it. MySQL-এ `LEFT JOIN` এবং `RIGHT JOIN`-এর ফলাফল `UNION` দিয়ে combine করা যায়।

## 7. JOIN Comparison

| JOIN Type | Description |
|---|---|
| INNER JOIN | Only matching records |
| LEFT JOIN | All left + matching right records |
| RIGHT JOIN | All right + matching left records |
| FULL OUTER JOIN | All records from both tables |

## 8. Important SQL JOIN Concepts

### 8.1 JOIN and ON

- `JOIN` → কোন table-এর সাথে যুক্ত হবে।
- `ON` → কোন condition-এর ভিত্তিতে যুক্ত হবে।

### 8.2 Table Alias

```sql
SELECT e.name, d.dept_name
FROM employees e
JOIN departments d
ON e.dept_id = d.id;
```

- `e` = employees table alias
- `d` = departments table alias

### 8.3 INNER JOIN vs EXISTS

| JOIN | EXISTS |
|---|---|
| Related table-এর column থেকে data retrieve করে | Matching record আছে কি না পরীক্ষা করে |
| দুই table-এর data combine করে | Boolean condition হিসেবে কাজ করে |
| Duplicate rows হতে পারে | Outer table-এর একটি row একবারই return হয় |

### 8.4 JOIN vs UNION

| JOIN | UNION |
|---|---|
| Columns horizontally combine করে | Rows vertically combine করে |
| Related columns-এর ভিত্তিতে data combine করে | Compatible SELECT results combine করে |
| Multiple tables-এর columns দেখায় | Multiple queries-এর rows combine করে |

### 8.5 Important Exam Notes

- `JOIN` এবং `INNER JOIN` একই অর্থে ব্যবহৃত হয়।
- `LEFT JOIN` = `LEFT OUTER JOIN`
- `RIGHT JOIN` = `RIGHT OUTER JOIN`
- `FULL JOIN` = `FULL OUTER JOIN`
- `ON` specifies the join condition.
- `NULL` appears when there is no matching row in an outer join.
- `CROSS JOIN` produces a Cartesian product.
- `SELF JOIN` joins a table with itself.

## 9. Other Types of JOIN

### CROSS JOIN

Returns the Cartesian product of two tables.

```sql
SELECT *
FROM employees
CROSS JOIN departments;
```

যদি employees table-এ 4টি row এবং departments table-এ 3টি row থাকে, তাহলে result হবে `4 × 3 = 12` rows।

### SELF JOIN

A SELF JOIN joins a table with itself.

```sql
SELECT 
    e.name AS employee_name,
    m.name AS manager_name
FROM employees e
JOIN employees m
ON e.manager_id = m.id;
```
# SQL SELF JOIN

## 1. What is SELF JOIN?

SELF JOIN is a technique in SQL where a table is joined with itself to retrieve related records from the same table.

**বাংলায়:** একই table-এর দুইটি ভিন্ন row-এর মধ্যে relationship খুঁজে বের করার জন্য SELF JOIN ব্যবহার করা হয়।

**Example:** Employee এবং Manager-এর তথ্য একই table-এ থাকলে employee-এর নামের পাশাপাশি manager-এর নাম বের করতে SELF JOIN ব্যবহার করা হয়।

## 2. Example Table: employees

| id | name | manager_id |
|---|---|---|
| 1 | Mamun | NULL |
| 2 | Rahim | 1 |
| 3 | Karim | 1 |
| 4 | Hasan | 2 |
| 5 | Sakib | 2 |

**Explanation:**

- Mamun-এর কোনো manager নেই।
- Rahim-এর manager Mamun (ID: 1)।
- Karim-এর manager Mamun (ID: 1)।
- Hasan-এর manager Rahim (ID: 2)।
- Sakib-এর manager Rahim (ID: 2)।

## 3. SELF JOIN Query

```sql
SELECT
    e.name AS employee_name,
    m.name AS manager_name
FROM employees e
LEFT JOIN employees m
ON e.manager_id = m.id;
```

**Result:**

| employee_name | manager_name |
|---|---|
| Mamun | NULL |
| Rahim | Mamun |
| Karim | Mamun |
| Hasan | Rahim |
| Sakib | Rahim |

## 4. Explanation (Bangla)

এই query-তে একই `employees` table-কে দুইবার ব্যবহার করা হয়েছে।

- `employees e` → Employee হিসেবে table ব্যবহার করা হয়েছে।
- `employees m` → Manager হিসেবে একই table ব্যবহার করা হয়েছে।
- `e.manager_id = m.id` → Employee-এর manager_id এবং manager-এর id match করা হয়েছে।

**How it works:**

1. `e` alias দিয়ে employee-এর information নেওয়া হয়।
2. `m` alias দিয়ে manager-এর information নেওয়া হয়।
3. `ON` condition দিয়ে employee-এর manager_id এবং manager-এর id match করা হয়।
4. `LEFT JOIN` ব্যবহার করায় manager না থাকলেও employee result-এ থাকবে।

## 5. INNER JOIN vs LEFT SELF JOIN

### INNER SELF JOIN

Only employees having a matching manager are returned.

```sql
SELECT
    e.name AS employee_name,
    m.name AS manager_name
FROM employees e
INNER JOIN employees m
ON e.manager_id = m.id;
```

### LEFT SELF JOIN

All employees are returned, including employees who do not have a manager.

```sql
SELECT
    e.name AS employee_name,
    m.name AS manager_name
FROM employees e
LEFT JOIN employees m
ON e.manager_id = m.id;
```

## 6. Real-Life Use Cases

SELF JOIN is commonly used for:

1. Employee – Manager relationship
2. Student – Mentor relationship
3. Category – Parent Category relationship
4. Organization hierarchy
5. Employee – Supervisor relationship

## 7. Important Points

- SELF JOIN is not a separate JOIN keyword; it is a technique.
- A table is joined with itself.
- Different table aliases are required to distinguish the two references.
- `ON` defines the relationship between the two references.
- SELF JOIN can be used with INNER JOIN, LEFT JOIN and other JOIN types.



একই table থেকে employee এবং তার manager-এর তথ্য বের করতে SELF JOIN ব্যবহার করা যায়।

## 10. Job Exam Quick Revision

| Question | Answer |
|---|---|
| Only matching records? | INNER JOIN |
| All records from left table? | LEFT JOIN |
| All records from right table? | RIGHT JOIN |
| All records from both tables? | FULL OUTER JOIN |
| Cartesian product? | CROSS JOIN |
| Join a table with itself? | SELF JOIN |
| Join condition keyword? | ON |

## 11. Practice Questions

1. Which JOIN returns only matching records?
2. Which JOIN returns all records from the left table?
3. Which JOIN returns all records from both tables?
4. Which JOIN produces a Cartesian product?
5. What is the difference between INNER JOIN and EXISTS?
6. What is the difference between JOIN and UNION?
7. What is SELF JOIN?
8. What happens when there is no matching record in LEFT JOIN?

---

**Remember:**

- INNER JOIN = Matching records
- LEFT JOIN = All Left records
- RIGHT JOIN = All Right records
- FULL OUTER JOIN = All records from Both tables
- CROSS JOIN = Cartesian Product
- SELF JOIN = Same table joined with itself
# SQL Query Execution Order

## 1. What is SQL Query Execution Order?

SQL Query Execution Order হলো একটি SQL query-এর বিভিন্ন clause database engine কোন logical order-এ process করে তার নিয়ম।

**Important:** SQL query আমরা যেভাবে লিখি, database engine সাধারণত logical processing-এর ক্ষেত্রে সেভাবে execute করে না।
<img width="874" height="462" alt="image" src="https://github.com/user-attachments/assets/512e1abe-64a5-483e-b51b-f12e6c44b13e" />

## 2. SQL Logical Execution Order

| Order | Clause | Description |
|---|---|---|
| 1 | FROM | কোন table থেকে data আসবে |
| 2 | JOIN / ON | একাধিক table-এর data combine এবং matching condition |
| 3 | WHERE | Individual rows filter করে |
| 4 | GROUP BY | একই value অনুযায়ী rows group করে |
| 5 | HAVING | Group-level filtering করে |
| 6 | SELECT | কোন column বা expression return করবে |
| 7 | DISTINCT | Duplicate rows remove করে |
| 8 | ORDER BY | Result sort করে |
| 9 | LIMIT / OFFSET | Result-এর row সংখ্যা সীমিত করে এবং starting position নির্ধারণ করে |

**Execution Flow:**

```text
FROM
  |
JOIN / ON
  |
WHERE
  |
GROUP BY
  |
HAVING
  |
SELECT
  |
DISTINCT
  |
ORDER BY
  |
LIMIT / OFFSET
```

## 3. Example SQL Query

```sql
SELECT department_id, COUNT(*) AS total_employee
FROM employees
WHERE salary > 20000
GROUP BY department_id
HAVING COUNT(*) > 2
ORDER BY total_employee DESC
LIMIT 5;
```

### Execution Explanation (Bangla)

**Step 1: FROM**

প্রথমে employees table থেকে data নেয়।

**Step 2: WHERE**

যেসব employee-এর salary 20000-এর বেশি, শুধু তাদের রাখে।

**Step 3: GROUP BY**

`department_id` অনুযায়ী employee-দের group তৈরি করে।

**Step 4: HAVING**

যেসব department-এ employee সংখ্যা 2-এর বেশি, শুধু সেগুলো রাখে।

**Step 5: SELECT**

`department_id` এবং employee count select করে।

**Step 6: ORDER BY**

Employee count descending order-এ সাজায়।

**Step 7: LIMIT**

প্রথম 5টি result দেখায়।

## 4. SQL Writing Order vs Execution Order

| Writing Order | Execution Order |
|---|---|
| SELECT | 6 |
| FROM | 1 |
| JOIN / ON | 2 |
| WHERE | 3 |
| GROUP BY | 4 |
| HAVING | 5 |
| DISTINCT | 7 |
| ORDER BY | 8 |
| LIMIT / OFFSET | 9 |

## 5. WHERE vs HAVING

| WHERE | HAVING |
|---|---|
| Individual rows filter করে | Groups filter করে |
| GROUP BY-এর আগে process হয় | GROUP BY-এর পরে process হয় |
| সাধারণত aggregate function সরাসরি ব্যবহার করা যায় না | Aggregate function ব্যবহার করা যায় |
| Row-level filtering | Group-level filtering |

**Example:**

```sql
-- WHERE: Filter individual rows
SELECT *
FROM employees
WHERE salary > 20000;

-- HAVING: Filter groups
SELECT department_id, COUNT(*) AS total_employee
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 2;
```

## 6. Important SQL Concepts

### 6.1 SELECT Alias

SELECT-এর alias সাধারণত ORDER BY-তে ব্যবহার করা যায়, কিন্তু একই query level-এর WHERE clause-এ ব্যবহার করা যায় না।

```sql
-- Correct
SELECT salary * 12 AS annual_salary
FROM employees
ORDER BY annual_salary DESC;

-- Incorrect
SELECT salary * 12 AS annual_salary
FROM employees
WHERE annual_salary > 200000;
```

**Reason:** Logical processing order অনুযায়ী WHERE আগে এবং SELECT পরে process হয়।

### 6.2 Aggregate Functions

Common aggregate functions:

- `COUNT()` – Counts rows
- `SUM()` – Calculates total
- `AVG()` – Calculates average
- `MAX()` – Finds maximum value
- `MIN()` – Finds minimum value

### 6.3 DISTINCT

`DISTINCT` duplicate result rows remove করে।

```sql
SELECT DISTINCT department_id
FROM employees;
```

### 6.4 ORDER BY

`ORDER BY` result sort করে।

```sql
-- Ascending order
SELECT *
FROM employees
ORDER BY salary ASC;

-- Descending order
SELECT *
FROM employees
ORDER BY salary DESC;
```

## 7. Job Exam Quick Revision

| Question | Answer |
|---|---|
| Which clause executes first? | FROM |
| Which clause filters rows? | WHERE |
| Which clause groups rows? | GROUP BY |
| Which clause filters groups? | HAVING |
| Which clause selects columns? | SELECT |
| Which clause removes duplicates? | DISTINCT |
| Which clause sorts records? | ORDER BY |
| Which clause limits rows? | LIMIT |

## 8. Practice MCQ

**Q1. Which clause is processed first in a SELECT query?**

- [ ] SELECT
- [ ] WHERE
- [x] FROM
- [ ] ORDER BY

**Answer:** FROM

**Q2. Which clause filters records before GROUP BY?**

- [ ] HAVING
- [x] WHERE
- [ ] ORDER BY
- [ ] DISTINCT

**Answer:** WHERE

**Q3. Which clause filters grouped records?**

- [ ] WHERE
- [ ] FROM
- [x] HAVING
- [ ] LIMIT

**Answer:** HAVING

**Q4. Which clause is used to sort query results?**

- [ ] GROUP BY
- [x] ORDER BY
- [ ] HAVING
- [ ] WHERE

**Answer:** ORDER BY

**Q5. Which clause removes duplicate rows?**

- [ ] GROUP BY
- [ ] ORDER BY
- [x] DISTINCT
- [ ] WHERE

**Answer:** DISTINCT

---

## 9. Final Remembering Note

```sql
FROM
JOIN / ON
WHERE
GROUP BY
HAVING
SELECT
DISTINCT
ORDER BY
LIMIT / OFFSET
```

**Easy Memory Tips:**

- FROM → Data কোথা থেকে আসবে?
- WHERE → কোন rows থাকবে?
- GROUP BY → কীভাবে group হবে?
- HAVING → কোন groups থাকবে?
- SELECT → কী দেখাবে?
- DISTINCT → Duplicate বাদ দেবে?
- ORDER BY → কীভাবে সাজাবে?
- LIMIT → কয়টি দেখাবে?

**Important Note:** This is the general logical query processing order, not necessarily the database engine's physical execution order. The optimizer may execute operations differently for performance. Advanced SQL features such as window functions and set operators have additional processing rules.
<img width="809" height="187" alt="image" src="https://github.com/user-attachments/assets/0517564b-fb87-42a3-9b4b-fddc2defa5cd" />
<img width="832" height="460" alt="image" src="https://github.com/user-attachments/assets/b798b4c6-da5a-4476-87de-ff559788f2cf" />

