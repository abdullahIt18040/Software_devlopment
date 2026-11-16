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


