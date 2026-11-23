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

# ACID Properties in DBMS

## 1. What are ACID Properties?

**ACID** is a set of four properties that ensure database transactions are processed reliably, accurately, and securely.

ACID stands for:

- **A** – Atomicity
- **C** – Consistency
- **I** – Isolation
- **D** – Durability

## 2. Atomicity (A)

**Definition:** All operations in a transaction must be completed successfully, or none of them should be performed.

**বাংলায়:** একটি Transaction-এর সবগুলো operation সফল হবে, অন্যথায় কোনো operation কার্যকর থাকবে না।

**Example: Bank Money Transfer**

Suppose Account A transfers ৳1,000 to Account B.

1. Deduct ৳1,000 from Account A.
2. Add ৳1,000 to Account B.

If money is deducted from Account A but adding money to Account B fails, the entire transaction will be rolled back.

**Remember:** All or Nothing.

## 3. Consistency (C)

**Definition:** A transaction must maintain database integrity and move the database from one valid state to another valid state and follow all database rules before and after execution.
Database Integrity মানে হলো Database-এর data যেন সবসময় সঠিক (Accurate), নির্ভরযোগ্য (Reliable) এবং নিয়ম অনুযায়ী (Consistent) থাকে।
**বাংলায়:** Transaction সম্পন্ন হওয়ার আগে ও পরে Database-এর সকল নিয়ম, constraint এবং integrity বজায় থাকতে হবে।

**Example:**

Suppose:
- Account A = ৳5,000
- Account B = ৳3,000
- Total balance = ৳8,000

After transferring ৳1,000:

- Account A = ৳4,000
- Account B = ৳4,000
- Total balance = ৳8,000

The total balance remains unchanged.

**Remember:** Database rules must always be maintained.

## 4. Isolation (I)

**Definition:** Multiple transactions executing simultaneously should not interfere with each other.

**বাংলায়:** একাধিক Transaction একই সময়ে execute হলেও প্রত্যেকটি Transaction এমনভাবে কাজ করবে যেন অন্য Transaction-এর অনাকাঙ্ক্ষিত প্রভাব না পড়ে।

**Example:**

Suppose two users access the same bank account simultaneously.

- Transaction T1 withdraws ৳1,000.
- Transaction T2 withdraws ৳2,000.

Isolation ensures that concurrent transactions do not produce incorrect or inconsistent results.

**Remember:** Transactions execute independently without unwanted interference.

## 5. Durability (D)

**Definition:** Once a transaction is committed, its changes must remain permanent, even if a system failure or power outage occurs.

**বাংলায়:** একবার Transaction COMMIT হলে system crash বা power failure হলেও committed data সংরক্ষিত থাকবে।

**Example:**

1. Account A transfers ৳1,000 to Account B.
2. Database executes `COMMIT`.
3. Suddenly, the server crashes.
4. After restarting, the committed changes remain saved.

**Remember:** Committed data is permanent.

## 6. ACID Summary Table

| Property | Meaning | Key Concept |
|---|---|---|
| Atomicity | All or Nothing | Complete or Rollback |
| Consistency | Maintain validity | Database Integrity |
| Isolation | No unwanted interference | Concurrent Transactions |
| Durability | Permanent changes | After COMMIT |

## 7. Important SQL Commands

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

If an error occurs before committing:

```sql
ROLLBACK;
```

## 8. Important Points for Job Exams

- ACID ensures reliable database transactions.
- Atomicity = All or Nothing.
- Consistency = Valid database state.
- Isolation = Independent execution of concurrent transactions.
- Durability = Permanent committed data.
- COMMIT is related to Durability.
- ROLLBACK is related to Atomicity.
- Isolation helps prevent concurrency problems.
- Consistency maintains database constraints and integrity.

## 9. Easy Way to Remember

**A – Atomicity:** All or Nothing.

**C – Consistency:** Correct Database State.

**I – Isolation:** Independent Transactions.

**D – Durability:** Data is Permanent.

**Exam Tip:** ACID is one of the most important concepts in DBMS and is frequently asked in IT job examinations.
