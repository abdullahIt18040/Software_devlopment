<img width="845" height="428" alt="image" src="https://github.com/user-attachments/assets/0e4686a2-b1ca-4eb0-88ef-f4e15a4727a1" />
<img width="969" height="238" alt="image" src="https://github.com/user-attachments/assets/65f3672a-1c50-4f3e-83a2-1e3f60212dfb" />
<img width="868" height="448" alt="image" src="https://github.com/user-attachments/assets/6efb05f3-9a39-4c32-8781-6bd25fcbc15e" />
<img width="630" height="118" alt="image" src="https://github.com/user-attachments/assets/ca1b903a-cb2e-4a31-bc25-96bf4961a302" />
<img width="821" height="391" alt="image" src="https://github.com/user-attachments/assets/1a6df072-bcd2-4182-ac61-ff0ebb3322bf" />
<img width="1348" height="532" alt="image" src="https://github.com/user-attachments/assets/f1ec1896-d8b2-442f-8d29-d6efaf5ae491" />
<img width="877" height="422" alt="image" src="https://github.com/user-attachments/assets/db612ea5-307a-4859-923a-cbc81a54104b" />

```
SELECT
    Department,
    COUNT(*) AS total_students
FROM STUDENTS
WHERE Marks > 80
GROUP BY Department;

```

<img width="852" height="394" alt="image" src="https://github.com/user-attachments/assets/93322b19-ad39-4537-ae4e-3cc5637ebe65" />

```

SELECT
    HospitalName,
    PatientCount
FROM Hospital
WHERE Specialization = 'Accident Treatment'
ORDER BY PatientCount DESC
LIMIT 5;

```
<img width="1141" height="175" alt="image" src="https://github.com/user-attachments/assets/f16d6f24-ea97-4c85-810a-33d2ae64d532" />
# SQL Aggregate Function in WHERE Clause

## 1. Problem

Consider the following SQL query:

```sql
SELECT EmployeeName, Salary
FROM Employees
WHERE Salary > AVG(Salary);
```

**Question:** Why does this query generate an error?

## 2. Reason

Aggregate functions such as `AVG()`, `SUM()`, `COUNT()`, `MAX()`, and `MIN()` cannot be used directly in the `WHERE` clause.

- `WHERE` filters individual rows before aggregation.
- `AVG()` calculates an aggregate value.
- Therefore, we cannot directly use `AVG()` inside `WHERE`.

## 3. Solution: Using Subquery

```sql
SELECT EmployeeName, Salary
FROM Employees
WHERE Salary > (
    SELECT AVG(Salary)
    FROM Employees
);
```

**Explanation:**

1. The inner query calculates the average salary of all employees.
2. The outer query selects employees whose salary is greater than the average salary.

## 4. Example

**Employees Table**

| EmployeeName | Salary |
|---|---:|
| Rahim | 20000 |
| Karim | 30000 |
| Hasan | 40000 |
| Sumon | 50000 |

**Average Salary:**

```sql
SELECT AVG(Salary)
FROM Employees;
```

Output:

```text
35000
```

**Final Output**

| EmployeeName | Salary |
|---|---:|
| Hasan | 40000 |
| Sumon | 50000 |

## 5. WHERE vs HAVING

| WHERE | HAVING |
|---|---|
| Filters individual rows | Filters groups |
| Applied before GROUP BY | Applied after GROUP BY |
| Cannot directly use aggregate functions | Can use aggregate functions |

### Example: Using HAVING

```sql
SELECT DepartmentID, AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY DepartmentID
HAVING AVG(Salary) > 35000;
```

## 6. Important Exam Notes

- `WHERE` → Filters rows before grouping.
- `GROUP BY` → Groups rows based on column values.
- `HAVING` → Filters grouped results.
- `AVG()` → Calculates average value.
- `SUM()` → Calculates total value.
- `COUNT()` → Counts rows.
- `MAX()` → Finds maximum value.
- `MIN()` → Finds minimum value.
- **Subquery** → Can calculate an aggregate value for comparison in `WHERE`.

### Exam Tip

To find employees whose salary is greater than the overall average salary, use:

**Subquery + AVG() + WHERE**

```sql
WHERE Salary > (SELECT AVG(Salary) FROM Employees);
```

<img width="889" height="374" alt="image" src="https://github.com/user-attachments/assets/b36abc65-b3b1-4368-a777-dd0af40e86c3" />

```
SELECT
    Department,
    COUNT(EmployeeID) AS TotalEmployees,
    AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department;

```

<img width="880" height="159" alt="image" src="https://github.com/user-attachments/assets/b42071b6-f09f-46f3-b2f6-07d3d1cf3d4b" />

# SQL CREATE TABLE – STUDENT

## 1. SQL Query

```sql
CREATE TABLE STUDENT (
    RollNumber INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Department VARCHAR(50),
    Email VARCHAR(100) UNIQUE,
    AdmissionDate DATE
);
```

## 2. Data Types

| Column | Data Type | Purpose |
|---|---|---|
| RollNumber | INT | Numeric roll number |
| Name | VARCHAR(100) | Student name |
| Department | VARCHAR(50) | Department name |
| Email | VARCHAR(100) | Email address |
| AdmissionDate | DATE | Admission date |

## 3. Primary Key

**RollNumber** is the Primary Key because:

- Uniquely identifies each student.
- Cannot contain NULL.
- Does not allow duplicate values.

<img width="878" height="379" alt="image" src="https://github.com/user-attachments/assets/f588ce91-8d3e-431f-8afd-3f767f891d68" />

# SQL – Find Students Enrolled in at Least Two Courses

## 1. Problem

Find the Student IDs (`S_id`) who are enrolled in at least two courses.

## 2. Student Table

| S_id | C_id | Year |
|---|---|---|
| S1 | C1 | 2026 |
| S2 | C2 | 2025 |
| S1 | C2 | 2024 |

## 3. SQL Query

```sql
SELECT S_id
FROM Student
GROUP BY S_id
HAVING COUNT(DISTINCT C_id) >= 2;
```

## 4. Explanation

- `GROUP BY S_id` → Groups records by student ID.
- `COUNT(DISTINCT C_id)` → Counts unique courses for each student.
- `HAVING COUNT(DISTINCT C_id) >= 2` → Returns students enrolled in at least two different courses.

## 5. Expected Output

| S_id |
|---|
| S1 |

**Reason:**
- S1 → C1, C2 = 2 courses.
- S2 → C2 = 1 course.

## 6. Important Exam Notes

| SQL | Purpose |
|---|---|
| GROUP BY | Groups records |
| COUNT() | Counts records |
| COUNT(DISTINCT) | Counts unique values |
| HAVING | Filters grouped results |

### Remember

To find students enrolled in at least N different courses:

```sql
SELECT S_id
FROM Student
GROUP BY S_id
HAVING COUNT(DISTINCT C_id) >= N;
```
<img width="878" height="298" alt="image" src="https://github.com/user-attachments/assets/2e3b07cf-16db-40a6-9885-afb226d2a322" />

```
SELECT EmpName, COUNT(*) AS DuplicateCount
FROM Employee
GROUP BY EmpName
HAVING COUNT(*) > 1;

```
<img width="858" height="353" alt="image" src="https://github.com/user-attachments/assets/595a42e1-225b-4279-8091-4f4ec6bedf7c" />

# SQL – Self Join and Department-wise Total Salary

## 1. Find Manager Names for Each Employee

**Concept: SELF JOIN**

```sql
SELECT
    E.Ename AS EmployeeName,
    M.Ename AS ManagerName
FROM Employee E
LEFT JOIN Employee M
    ON E.M_ID = M.E_ID;
```

### Expected Output

| EmployeeName | ManagerName |
|---|---|
| Rahim | Hasan |
| Karim | Hasan |
| Sakib | Nabil |
| Hasan | NULL |
| Nabil | NULL |

### Explanation

- `E` → Employee table alias.
- `M` → Manager table alias.
- `E.M_ID = M.E_ID` → Matches manager ID with employee ID.
- `LEFT JOIN` → Includes employees without managers.

---

## 2. Calculate Total Salary of Each Department

**Concept: JOIN + GROUP BY + SUM() + ORDER BY**

```sql
SELECT
    D.Dept_Name,
    SUM(D.Salary) AS TotalSalary
FROM Employee E
JOIN Department D
    ON E.E_ID = D.E_ID
GROUP BY D.Dept_Name
ORDER BY TotalSalary DESC;
```

### Expected Output

| Dept_Name | TotalSalary |
|---|---:|
| IT | 150000 |
| HR | 80000 |

### Explanation

- `JOIN` → Combines Employee and Department records.
- `SUM(D.Salary)` → Calculates total salary.
- `GROUP BY D.Dept_Name` → Groups records by department.
- `ORDER BY TotalSalary DESC` → Sorts highest to lowest.

---

## 3. Important Exam Notes

| Concept | SQL |
|---|---|
| Self Join | Joins a table with itself |
| Manager Name | `E.M_ID = M.E_ID` |
| Total Salary | `SUM(Salary)` |
| Department-wise calculation | `GROUP BY Dept_Name` |
| Highest to Lowest | `ORDER BY Salary DESC` |
| Lowest to Highest | `ORDER BY Salary ASC` |

## 4. Remember

```sql
-- Employee and Manager
SELF JOIN + ON

-- Department-wise total salary
JOIN + GROUP BY + SUM()

-- Descending order
ORDER BY TotalSalary DESC
```

<img width="905" height="484" alt="image" src="https://github.com/user-attachments/assets/fdb21624-c0ad-440c-8ca0-abd9df98c8fc" />
<img width="785" height="405" alt="image" src="https://github.com/user-attachments/assets/2a927d04-4f8c-4845-a18b-6dd12b561cbf" />

# SQL JOIN (DBMS) – Job Exam Notes

## 1. Introduction

**JOIN** is used to combine rows from two or more tables based on a related column.

### Given Tables

**Customers**

| id | firstName |
|---|---|
| 1 | Rahim |
| 2 | Karim |
| 3 | Belal |
| 4 | Rony |
| 5 | Helal |

**Orders**

| Order_id | amount | Customer_id |
|---|---:|---:|
| 1 | 200 | 10 |
| 2 | 500 | 3 |
| 3 | 300 | 6 |
| 4 | 800 | 5 |
| 5 | 150 | 8 |

**Join Condition:**

```sql
ON Customers.id = Orders.Customer_id
```

---

## 2. INNER JOIN

**Definition:** Returns only matching records from both tables.

```sql
SELECT C.id, C.firstName, O.Order_id, O.amount
FROM Customers C
INNER JOIN Orders O
ON C.id = O.Customer_id;
```

**Output:**

| id | firstName | Order_id | amount |
|---|---|---:|---:|
| 3 | Belal | 2 | 500 |
| 5 | Helal | 4 | 800 |

**Key Point:** Only matching records are returned.

---

## 3. LEFT JOIN (LEFT OUTER JOIN)

**Definition:** Returns all records from the left table and matching records from the right table. If no match exists, right table columns contain NULL.

```sql
SELECT C.id, C.firstName, O.Order_id, O.amount
FROM Customers C
LEFT JOIN Orders O
ON C.id = O.Customer_id;
```

**Output:**

| id | firstName | Order_id | amount |
|---|---|---:|---:|
| 1 | Rahim | NULL | NULL |
| 2 | Karim | NULL | NULL |
| 3 | Belal | 2 | 500 |
| 4 | Rony | NULL | NULL |
| 5 | Helal | 4 | 800 |

**Key Point:** All rows from the LEFT table are returned.

---

## 4. RIGHT JOIN (RIGHT OUTER JOIN)

**Definition:** Returns all records from the right table and matching records from the left table. If no match exists, left table columns contain NULL.

```sql
SELECT C.id, C.firstName, O.Order_id, O.amount, O.Customer_id
FROM Customers C
RIGHT JOIN Orders O
ON C.id = O.Customer_id;
```

**Output:**

| id | firstName | Order_id | amount | Customer_id |
|---|---|---:|---:|---:|
| NULL | NULL | 1 | 200 | 10 |
| 3 | Belal | 2 | 500 | 3 |
| NULL | NULL | 3 | 300 | 6 |
| 5 | Helal | 4 | 800 | 5 |
| NULL | NULL | 5 | 150 | 8 |

**Key Point:** All rows from the RIGHT table are returned.

---

## 5. FULL OUTER JOIN

**Definition:** Returns all records from both tables. Matching records are combined, and non-matching records contain NULL.

```sql
SELECT C.id, C.firstName, O.Order_id, O.amount, O.Customer_id
FROM Customers C
FULL OUTER JOIN Orders O
ON C.id = O.Customer_id;
```

**Output:**

| id | firstName | Order_id | amount | Customer_id |
|---|---|---:|---:|---:|
| 1 | Rahim | NULL | NULL | NULL |
| 2 | Karim | NULL | NULL | NULL |
| 3 | Belal | 2 | 500 | 3 |
| 4 | Rony | NULL | NULL | NULL |
| 5 | Helal | 4 | 800 | 5 |
| NULL | NULL | 1 | 200 | 10 |
| NULL | NULL | 3 | 300 | 6 |
| NULL | NULL | 5 | 150 | 8 |



---


<img width="929" height="262" alt="image" src="https://github.com/user-attachments/assets/6985b0a2-b52e-41a3-b866-88a054657af2" />
<img width="667" height="435" alt="image" src="https://github.com/user-attachments/assets/65098200-90e5-4eac-9dfc-2ff76a6acab4" />

<img width="977" height="522" alt="image" src="https://github.com/user-attachments/assets/877e6c76-76b6-49b2-bddb-dba41b210cd1" />
# SQL JOIN, GROUP BY, HAVING & Aggregate Functions – Job Exam Notes

## 1. Given Tables

### Students

| StudentId | StudentName |
|---|---|
| 1 | Mr. A |
| 2 | Mr. B |
| 3 | Mr. C |
| 4 | Mr. D |

### Marks

| StudentId | Subject | Mark |
|---|---|---:|
| 1 | Math | 70 |
| 2 | Math | 90 |
| 3 | Math | 30 |
| 1 | Bangali | 50 |
| 2 | Bangali | 60 |
| 3 | Bangali | 70 |
| 1 | Physics | 80 |
| 2 | Physics | 70 |
| 3 | Physics | 60 |

---

## i) Count the Total Rows Using LEFT JOIN

### SQL Query

```sql
SELECT COUNT(*)
FROM Students S
LEFT JOIN Marks M
    ON S.StudentId = M.StudentId;
```

### Output

| COUNT(*) |
|---:|
| 10 |

### Explanation

- Mr. A has 3 subjects.
- Mr. B has 3 subjects.
- Mr. C has 3 subjects.
- Mr. D has no subject but is included because of LEFT JOIN.

**Total = 3 + 3 + 3 + 1 = 10**

**Important:** The original question appears to omit the `ON` condition. Without `ON` or `USING`, this LEFT JOIN syntax is invalid in standard SQL.

---

## ii) Find Students Whose Total Marks Are Greater Than or Equal to 200

### SQL Query

```sql
SELECT S.StudentName
FROM Students S
JOIN Marks M
    ON S.StudentId = M.StudentId
GROUP BY S.StudentId, S.StudentName
HAVING SUM(Mark) >= 200;
```

### Step 1: Calculate Total Marks

| StudentName | Total Marks |
|---|---:|
| Mr. A | 200 |
| Mr. B | 220 |
| Mr. C | 160 |

### Step 2: Apply HAVING Condition

```sql
HAVING SUM(Mark) >= 200;
```

### Output

| StudentName |
|---|
| Mr. A |
| Mr. B |

**Explanation:**
- `GROUP BY` groups marks student-wise.
- `SUM()` calculates the total marks.
- `HAVING` filters groups based on aggregate conditions.

---

## iii) List All Student Names and Number of Subjects They Have Completed

### SQL Query

```sql
SELECT
    S.StudentName,
    COUNT(M.Subject) AS TotalSubjects
FROM Students S
LEFT JOIN Marks M
    ON S.StudentId = M.StudentId
GROUP BY S.StudentId, S.StudentName;
```

### Output

| StudentName | TotalSubjects |
|---|---:|
| Mr. A | 3 |
| Mr. B | 3 |
| Mr. C | 3 |
| Mr. D | 0 |

### Explanation

- `LEFT JOIN` includes all students.
- `COUNT(M.Subject)` counts completed subjects.
- `COUNT(column)` ignores NULL values.
- Mr. D has no matching subject, so the count is 0.

**Important Exam Trick:**

Use `COUNT(M.Subject)` instead of `COUNT(*)` when counting matching records after a LEFT JOIN.

---

## iv) List All Students Who Have Not Completed Any Subject

### Method 1: Using LEFT JOIN

```sql
SELECT S.StudentName
FROM Students S
LEFT JOIN Marks M
    ON S.StudentId = M.StudentId
WHERE M.StudentId IS NULL;
```

### Output

| StudentName |
|---|
| Mr. D |

### Explanation

1. LEFT JOIN returns all students.
2. Unmatched students get NULL in Marks columns.
3. `IS NULL` identifies students without any matching subject.

### Method 2: Using NOT EXISTS

```sql
SELECT S.StudentName
FROM Students S
WHERE NOT EXISTS (
    SELECT 1
    FROM Marks M
    WHERE M.StudentId = S.StudentId
);
```

**Output:** Mr. D

---

## v) List All Subject Names

### SQL Query

```sql
SELECT DISTINCT Subject
FROM Marks;
```

### Output

| Subject |
|---|
| Math |
| Bangali |
| Physics |

### Explanation

`DISTINCT` removes duplicate values and returns unique subject names.

---

## 2. Important SQL Concepts for Job Exams

| SQL Concept | Purpose |
|---|---|
| `COUNT(*)` | Counts all rows |
| `COUNT(column)` | Counts non-NULL values |
| `SUM(column)` | Calculates total |
| `AVG(column)` | Calculates average |
| `MAX(column)` | Finds maximum value |
| `MIN(column)` | Finds minimum value |
| `GROUP BY` | Groups records |
| `HAVING` | Filters grouped records |
| `WHERE` | Filters individual rows |
| `DISTINCT` | Removes duplicate values |
| `IS NULL` | Checks NULL values |
| `NOT EXISTS` | Finds records without matching records |
| `LEFT JOIN` | Returns all left table records |

---

## 3. Important Job Exam Tricks

### COUNT(*) vs COUNT(column)

```sql
SELECT COUNT(*) FROM Marks;
```

Counts all rows, including rows containing NULL values.

```sql
SELECT COUNT(Subject) FROM Marks;
```

Counts only non-NULL Subject values.

### WHERE vs HAVING

| WHERE | HAVING |
|---|---|
| Filters individual rows | Filters groups |
| Applied before GROUP BY | Applied after GROUP BY |
| Cannot directly use aggregate conditions | Can use aggregate functions |
| Example: `WHERE Mark > 50` | Example: `HAVING SUM(Mark) >= 200` |

### DISTINCT vs GROUP BY

- `DISTINCT` removes duplicate values.
- `GROUP BY` groups rows and is commonly used with aggregate functions.

### LEFT JOIN + IS NULL

Used to find records in the left table that have no matching records in the right table.

```sql
SELECT S.StudentName
FROM Students S
LEFT JOIN Marks M
    ON S.StudentId = M.StudentId
WHERE M.StudentId IS NULL;
```

---

<img width="999" height="518" alt="image" src="https://github.com/user-attachments/assets/7ff8f7f7-c73c-401e-b0f5-7fadcf5abc0a" />


# ON DELETE CASCADE – DBMS Job Exam Notes

## 1. What is ON DELETE CASCADE?

**Definition:** `ON DELETE CASCADE` is a referential integrity constraint. When a parent record is deleted, all related child records are automatically deleted.

**In simple Bangla:**

Parent table থেকে কোনো record delete করলে, তার সঙ্গে সম্পর্কিত Child table-এর record-গুলোও automatically delete হয়ে যায়।

---

## 2. Given Tables

### Managers (Parent Table)

| ManagerID (PK) | ManagerName |
|---|---|
| 101 | Rahim |
| 102 | Karim |
| 103 | Hasan |

### Employees (Child Table)

| EmployeeID (PK) | EmployeeName | ManagerID (FK) |
|---|---|---|
| 1 | Sakib | 101 |
| 2 | Rakib | 101 |
| 3 | Fahim | 102 |

**Relationship:**

- `Managers.ManagerID` → Primary Key (PK)
- `Employees.ManagerID` → Foreign Key (FK)

---

## 3. SQL Implementation

### Create Parent Table

```sql
CREATE TABLE Managers (
    ManagerID INT PRIMARY KEY,
    ManagerName VARCHAR(100)
);
```

### Create Child Table with ON DELETE CASCADE

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    EmployeeName VARCHAR(100),
    ManagerID INT,
    FOREIGN KEY (ManagerID)
        REFERENCES Managers(ManagerID)
        ON DELETE CASCADE
);
```

---

## 4. What Happens When a Manager Is Deleted?

### Delete Manager 101

```sql
DELETE FROM Managers
WHERE ManagerID = 101;
```

Because of `ON DELETE CASCADE`, all employees associated with Manager 101 will automatically be deleted.

### Employees Table After Deletion

| EmployeeID | EmployeeName | ManagerID |
|---|---|---|
| 3 | Fahim | 102 |

**Automatically deleted:**
- Manager Rahim (101)
- Employee Sakib (1)
- Employee Rakib (2)

**Fahim remains** because his manager (102) still exists.

---

## 5. Why Is ON DELETE CASCADE Dangerous in Banking Systems?

In a real banking system, employee and manager information is important.

Suppose:
- One manager supervises 50 employees.
- The manager has 50 associated employee records.
- An administrator accidentally deletes the manager.

With `ON DELETE CASCADE`, all 50 employee records will automatically be deleted.

### Potential Problems

1. Loss of employee records.
2. Loss of important organizational information.
3. Disruption of banking operations.
4. Audit and compliance problems.
5. Accidental deletion of important business data.

---

## 6. Best Practices to Prevent Accidental Data Loss

### A. ON DELETE RESTRICT

Prevents deleting a parent record while related child records exist.

```sql
FOREIGN KEY (ManagerID)
REFERENCES Managers(ManagerID)
ON DELETE RESTRICT;
```

### B. Soft Delete

Instead of permanently deleting records, mark them as inactive.

```sql
UPDATE Managers
SET Status = 'INACTIVE'
WHERE ManagerID = 101;
```

**Benefit:** Records remain in the database for future reference.

### C. Maintain Audit Logs

Record:
- Who deleted or modified the data.
- When the operation happened.
- Which records were affected.

### D. Use Database Transactions

Transactions help ensure controlled operations and allow rollback before committing changes.

```sql
BEGIN;

DELETE FROM Managers
WHERE ManagerID = 101;

ROLLBACK;
```

`ROLLBACK` cancels the uncommitted deletion, including cascading deletions.

---

## 7. Comparison of ON DELETE Actions

| Action | Behavior |
|---|---|
| CASCADE | Automatically deletes related child records |
| RESTRICT | Prevents parent deletion if child records exist |
| SET NULL | Sets the child foreign key to NULL |
| NO ACTION | Rejects deletion if referential integrity would be violated |

**Note:** RESTRICT and NO ACTION enforcement timing can vary by database.

---

# SQL ON DELETE Actions – DBMS Notes

When a Foreign Key references a Primary Key in another table, `ON DELETE` defines what happens to related child records when a parent record is deleted.

There are four important concepts:

1. ON DELETE CASCADE
2. ON DELETE RESTRICT
3. ON DELETE SET NULL
4. SOFT DELETE

---

## 1. ON DELETE CASCADE

**Definition:** When a parent record is deleted, all related child records are automatically deleted.

**Example:**

Suppose we have two tables:

**Managers (Parent Table)**

| ManagerID (PK) | ManagerName |
|---|---|
| 101 | Rahim |
| 102 | Karim |

**Employees (Child Table)**

| EmployeeID (PK) | EmployeeName | ManagerID (FK) |
|---|---|---|
| 1 | Sakib | 101 |
| 2 | Rakib | 101 |
| 3 | Fahim | 102 |

### SQL Implementation

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    EmployeeName VARCHAR(100),
    ManagerID INT,
    FOREIGN KEY (ManagerID)
        REFERENCES Managers(ManagerID)
        ON DELETE CASCADE
);
```

### Delete a Manager

```sql
DELETE FROM Managers
WHERE ManagerID = 101;
```

### Result

- Manager Rahim (101) will be deleted.
- Employee Sakib (1) will automatically be deleted.
- Employee Rakib (2) will automatically be deleted.
- Employee Fahim (3) will remain.

**Real-life Example:**
If a customer account is permanently deleted, all dependent records configured with CASCADE, such as certain account-related child records, may also be deleted.

**Advantages:**
- Automatically maintains referential integrity.
- Avoids manually deleting dependent records.
- Useful when child records have no independent meaning.

**Disadvantages:**
- Accidental deletion of a parent can delete many child records.
- May cause significant data loss.
- Risky for important business and banking records.

---

## 2. ON DELETE RESTRICT

**Definition:** Prevents deleting a parent record if related child records exist.

**Example:**

A manager has multiple employees. We should not delete the manager while employees are still assigned to that manager.

### SQL Implementation

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    EmployeeName VARCHAR(100),
    ManagerID INT,
    FOREIGN KEY (ManagerID)
        REFERENCES Managers(ManagerID)
        ON DELETE RESTRICT
);
```

### Try to Delete a Manager

```sql
DELETE FROM Managers
WHERE ManagerID = 101;
```

**Result:** The DELETE operation will fail because employees are still associated with Manager 101.

### How to Delete Successfully?

First, reassign the employees to another manager.

```sql
UPDATE Employees
SET ManagerID = 102
WHERE ManagerID = 101;
```

Then delete the old manager.

```sql
DELETE FROM Managers
WHERE ManagerID = 101;
```

**Real-life Example:**
In a banking system, a manager should not be permanently deleted while employees are still assigned to that manager.

**Advantages:**
- Prevents accidental deletion of parent records.
- Protects related business data.
- Maintains referential integrity.

**Disadvantages:**
- Requires handling dependent records before deletion.
- May require additional UPDATE or DELETE operations.

---

## 3. ON DELETE SET NULL

**Definition:** When a parent record is deleted, the foreign key values of related child records are automatically set to NULL instead of deleting the child records.

**Example:**

Suppose Manager Rahim manages two employees.

### SQL Implementation

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    EmployeeName VARCHAR(100),
    ManagerID INT NULL,
    FOREIGN KEY (ManagerID)
        REFERENCES Managers(ManagerID)
        ON DELETE SET NULL
);
```

**Important:** The foreign key column must allow NULL values.

### Delete a Manager

```sql
DELETE FROM Managers
WHERE ManagerID = 101;
```

### Employees Table After Deletion

| EmployeeID | EmployeeName | ManagerID |
|---|---|---|
| 1 | Sakib | NULL |
| 2 | Rakib | NULL |
| 3 | Fahim | 102 |

**What happened?**

- Manager Rahim was deleted.
- Sakib and Rakib were not deleted.
- Their ManagerID values became NULL.
- Fahim remains assigned to Manager 102.

**Real-life Example:**
If a manager leaves an organization, employees may remain in the system but temporarily have no assigned manager.

**Advantages:**
- Preserves child records.
- Avoids deleting important information.
- Removes invalid foreign key references.

**Disadvantages:**
- Child records may become temporarily unassigned.
- Applications must handle NULL values properly.

---

## 4. SOFT DELETE

**Definition:** Soft Delete means marking a record as inactive or deleted without permanently removing it from the database.

Unlike CASCADE, RESTRICT and SET NULL, Soft Delete is an application/database design approach, not a Foreign Key ON DELETE action.

**Example:**

Suppose we have a Managers table with an additional Status column.

### Managers Table

| ManagerID | ManagerName | Status |
|---|---|---|
| 101 | Rahim | ACTIVE |
| 102 | Karim | ACTIVE |

### SQL Implementation

```sql
ALTER TABLE Managers
ADD Status VARCHAR(20) DEFAULT 'ACTIVE';
```

### Perform Soft Delete

```sql
UPDATE Managers
SET Status = 'INACTIVE'
WHERE ManagerID = 101;
```

### Result

| ManagerID | ManagerName | Status |
|---|---|---|
| 101 | Rahim | INACTIVE |
| 102 | Karim | ACTIVE |

**What happened?**

- The manager record was not physically deleted.
- The manager was marked as INACTIVE.
- The record remains available in the database.
- Related employee records remain unchanged.

### Retrieve Only Active Managers

```sql
SELECT *
FROM Managers
WHERE Status = 'ACTIVE';
```

### Restore a Soft-Deleted Manager

```sql
UPDATE Managers
SET Status = 'ACTIVE'
WHERE ManagerID = 101;
```

**Real-life Example:**
Banking systems often need to retain historical records for audit, compliance and reporting. Soft Delete helps preserve those records.

**Advantages:**
- Prevents permanent data loss.
- Supports audit and historical reporting.
- Allows records to be restored.
- Useful for business applications.

**Disadvantages:**
- Requires filtering inactive records in queries.
- Increases database storage.
- Requires proper handling of deleted records in applications.

---

## 5. Comparison of ON DELETE Actions

| Feature | CASCADE | RESTRICT | SET NULL | SOFT DELETE |
|---|---|---|---|---|
| Parent record | Deleted | Deletion blocked if children exist | Deleted | Marked inactive |
| Child record | Deleted | Unchanged | Preserved | Unchanged |
| Foreign key | Child row removed | Unchanged | Set to NULL | Unchanged |
| Permanent deletion | Yes | No, if blocked | Parent only | No |
| Requires nullable FK | No | No | Yes | No |
| Data preservation | Low | High | High | High |

---



![Uploading image.png…]()

