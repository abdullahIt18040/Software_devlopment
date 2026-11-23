# Transaction in DBMS

## 1. Definition

A **Transaction** is a set of database operations performed as a single logical unit to execute  a specific task.

**বাংলায়:** Database-এ কোনো নির্দিষ্ট কাজ সম্পন্ন করার জন্য একাধিক operation-কে একক logical unit হিসেবে execute করাকে Transaction বলে।

## 2. Example: Bank Money Transfer

Suppose Account A transfers ৳1,000 to Account B.

**Operations:**
1. Deduct ৳1,000 from Account A.
2. Add ৳1,000 to Account B.

Both operations together form one transaction.

```sql
BEGIN;

UPDATE Accounts
SET balance = balance - 1000
WHERE account_id = 101;

UPDATE Accounts
SET balance = balance + 1000
WHERE account_id = 102;

COMMIT;
```

If an error occurs:

```sql
ROLLBACK;
```

## 3. Transaction Commands

| Command | Description |
|---|---|
| `BEGIN` | Starts a transaction |
| `COMMIT` | Permanently saves changes |
| `ROLLBACK` | Undoes uncommitted changes |
| `SAVEPOINT` | Creates a rollback point |
| `ROLLBACK TO` | Rolls back to a savepoint |

## 4. ACID Properties

A transaction follows four important properties called ACID.

| Property | Description |
|---|---|
| **Atomicity** | All operations succeed or none succeed. |
| **Consistency** | Database remains valid before and after a transaction. |
| **Isolation** | Concurrent transactions do not interfere with each other. |
| **Durability** | Committed changes remain permanent, even after system failure. |

## 5. Important Points for Job Exams

- Transaction = Set of database operations.
- Transaction = Single logical unit of work.
- `COMMIT` = Permanently save changes.
- `ROLLBACK` = Undo uncommitted changes.
- ACID = Atomicity, Consistency, Isolation, Durability.
- Bank money transfer is a common example of a transaction.

**Remember:** A transaction must be completed entirely or not performed at all (Atomicity).
