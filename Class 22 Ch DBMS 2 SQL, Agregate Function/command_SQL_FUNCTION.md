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


