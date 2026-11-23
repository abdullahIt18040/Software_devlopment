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

<img width="496" height="268" alt="image" src="https://github.com/user-attachments/assets/56c1a912-5623-47e0-8a4c-7fdabde0d132" />

# Transaction States in DBMS

## Definition
A **Transaction State** represents the current status of a transaction during its execution in a database.

## 1. Types of Transaction States

There are **6 transaction states** in DBMS.

### 1. Active State
- The transaction is currently executing.
- Read and Write operations are performed.

**Example:** Reading the sender's account balance.

### 2. Partially Committed State
- The last statement of the transaction has been executed.
- Changes are waiting to be permanently stored.

**Example:** All SQL statements have executed, but permanent storage is not yet confirmed.

### 3. Committed State
- The transaction has successfully completed.
- All changes are permanently stored in the database.

**Example:** Money is successfully transferred from Account A to Account B.

### 4. Failed State
- The transaction cannot continue due to an error or system failure.

**Example:** A database crash or constraint violation occurs.

### 5. Aborted State
- The transaction is rolled back.
- All changes made by the transaction are undone.

**Example:** Deducted money is restored to Account A using ROLLBACK.

### 6. Terminated State
- The transaction finishes its execution.
- It leaves the transaction processing system.
- It can be reached after either a committed or aborted state.

---

<img width="706" height="415" alt="image" src="https://github.com/user-attachments/assets/ebd197d1-bbaa-4f90-bc42-0985f66564e0" />

# Types of Schedules in DBMS

## 1. What is a Schedule?

A **Schedule** is the sequence or order in which operations of multiple transactions are executed in a database.

In simple words, a schedule determines the execution order of Read and Write operations of multiple transactions.

## 2. Types of Schedules

There are two main types of schedules:

1. Serial Schedule
2. Non-Serial Schedule

### A. Serial Schedule

When one transaction completes entirely before another transaction starts, it is called a Serial Schedule.

**Example:**

```text
T1: Read(A)
T1: Write(A)
T1: Commit

T2: Read(B)
T2: Write(B)
T2: Commit
```

**Key Point:**
- One transaction executes at a time.
- No interleaving of transaction operations.
- Always Serializable.

### B. Non-Serial Schedule

When operations of multiple transactions are interleaved, it is called a Non-Serial Schedule.

**Example:**

```text
T1: Read(A)
T2: Read(B)
T1: Write(A)
T2: Write(B)
T1: Commit
T2: Commit
```

**Key Point:**
- Multiple transactions execute in an interleaved order.
- May be Serializable or Non-Serializable.

---

## 3. Serializable Schedule

A Non-Serial Schedule is called Serializable if its result is equivalent to some Serial Schedule.

There are two types:

### A. Conflict Serializable

A schedule is Conflict Serializable if it can be transformed into a Serial Schedule by swapping non-conflicting operations.

**Conflict Operations:**

Two operations conflict if:
1. They belong to different transactions.
2. They operate on the same data item.
3. At least one operation is a Write operation.

**Types of Conflicting Operations:**

| Operation 1 | Operation 2 | Conflict? |
|---|---|---|
| Read(A) | Read(A) | No |
| Read(A) | Write(A) | Yes |
| Write(A) | Read(A) | Yes |
| Write(A) | Write(A) | Yes |

### B. View Serializable

A schedule is View Serializable if it is view-equivalent to a Serial Schedule.

Three conditions must be satisfied:

1. Initial Read: Both schedules read the initial value of a data item.
2. Read-from Relationship: Both schedules read data written by the same transaction.
3. Final Write: Both schedules have the same final writer for each data item.

**Key Point:** Every Conflict Serializable Schedule is View Serializable, but every View Serializable Schedule is not necessarily Conflict Serializable.

---

## 4. Non-Serializable Schedule

A schedule is Non-Serializable if it is not equivalent to any Serial Schedule.

**Key Point:**
- Its result cannot be represented by an equivalent Serial Schedule.
- May produce inconsistent results.

---

## 5. Recoverable Schedule

A schedule is Recoverable if a transaction reads data written by another transaction, the writer must commit before the reader commits.

**Example:**

```text
T1: Write(A)
T2: Read(A)
T1: Commit
T2: Commit
```

Here, T2 reads data written by T1. T1 commits before T2.

**Key Point:** The writer transaction must commit before the reader transaction commits.

## 6. Non-Recoverable Schedule

A schedule is Non-Recoverable if a transaction commits after reading uncommitted data from another transaction, but before the writer commits.

**Example:**

```text
T1: Write(A)
T2: Read(A)
T2: Commit
T1: Rollback
```

Here, T2 commits before T1. Later, T1 rolls back.

**Problem:** T2 has already committed using invalid data.

---

## 7. Cascading Schedule

A Cascading Schedule allows a transaction to read uncommitted data written by another transaction.

If the first transaction rolls back, dependent transactions may also need to roll back.

This is called **Cascading Rollback**.

**Example:**

```text
T1: Write(A)
T2: Read(A)
T3: Read(A)

T1: Rollback
T2: Rollback
T3: Rollback
```

**Key Point:** One transaction's rollback can cause multiple dependent transactions to roll back.

## 8. Cascadeless Schedule

A Cascadeless Schedule does not allow a transaction to read uncommitted data written by another transaction.

**Example:**

```text
T1: Write(A)
T1: Commit

T2: Read(A)
T2: Commit
```

Here, T2 reads A only after T1 commits.

**Key Point:**
- No dirty reads.
- Prevents Cascading Rollback.

## 9. Strict Schedule

A Strict Schedule does not allow another transaction to Read or Write a data item until the transaction that last wrote that item commits or aborts.

**Example:**

```text
T1: Write(A)
T1: Commit

T2: Read(A)
T2: Write(A)
T2: Commit
```

Here, T2 cannot Read or Write A before T1 finishes.

**Key Point:**
- No dirty reads.
- No dirty writes.
- Prevents Cascading Rollback.
- Easier database recovery.

---

## 10. Comparison of Schedules

| Schedule | Main Concept |
|---|---|
| Serial | One transaction completes before another starts |
| Non-Serial | Transaction operations are interleaved |
| Conflict Serializable | Can be converted into Serial by swapping non-conflicting operations |
| View Serializable | View-equivalent to a Serial Schedule |
| Non-Serializable | Not equivalent to any Serial Schedule |
| Recoverable | Writer commits before reader commits |
| Non-Recoverable | Reader commits before writer commits |
| Cascading | Rollback may affect dependent transactions |
| Cascadeless | Does not read uncommitted data |
| Strict | Does not read or write uncommitted data items |

---

## 11. Important Relationships for Job Exams

### Recoverability Relationship

```text
Strict Schedule
       |
       v
Cascadeless Schedule
       |
       v
Recoverable Schedule
```

**Remember:**

- Every Strict Schedule is Cascadeless.
- Every Cascadeless Schedule is Recoverable.
- Every Recoverable Schedule is not necessarily Cascadeless.
- Every Conflict Serializable Schedule is View Serializable.
- Every View Serializable Schedule is not necessarily Conflict Serializable.
- Every Serial Schedule is Serializable.
- Every Non-Serial Schedule is not necessarily Non-Serializable.

---

## 12. Important Terms

| Term | Meaning |
|---|---|
| Interleaving | Mixing operations of multiple transactions |
| Dirty Read | Reading uncommitted data |
| Dirty Write | Overwriting uncommitted data |
| Rollback | Undoing transaction changes |
| Commit | Permanently saving transaction changes |
| Serializability | Ensuring a schedule is equivalent to a Serial Schedule |

**Final Exam Tip:**

- Serial = One by one.
- Non-Serial = Interleaved.
- Serializable = Equivalent to Serial.
- Recoverable = Writer commits first.
- Cascadeless = No dirty read.
- Strict = No dirty read or dirty write.

