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
![Uploading image.png…]()

