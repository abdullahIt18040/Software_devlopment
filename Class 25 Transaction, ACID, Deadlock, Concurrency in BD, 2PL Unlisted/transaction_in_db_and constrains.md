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

<img width="875" height="456" alt="image" src="https://github.com/user-attachments/assets/188b00bb-e6a1-43a0-bcbb-4bdc5619058e" />

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

When operations of multiple transactions are executed simultaneously in a mixed order, it is called a Non-Serial Schedule.
<img width="853" height="414" alt="image" src="https://github.com/user-attachments/assets/f7c5e8e2-232f-4d13-bc66-39523dfdaa70" />


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

A Non-Serial Schedule that can be converted into an equivalent Serial Schedule is called a Serializable Schedule.
There are two types:
Non-Serial Schedule + Equivalent Serial Schedule = Serializable Schedule

### A. Conflict Serializable

A schedule is Conflict Serializable if it can be transformed into a Serial Schedule by swapping non-conflicting operations.

1. NO loop or cycle
2. must be consistence .
   
<img width="990" height="541" alt="image" src="https://github.com/user-attachments/assets/ad30dfbb-4280-4216-abd7-51abe64850cb" />

<img width="816" height="421" alt="image" src="https://github.com/user-attachments/assets/63d06b4c-0ab9-4558-81a3-6c32f94130a6" />

je node er incoming edge nai sai edge age execute hobe.

convert non serial schedule to serial sedule ;
<img width="935" height="623" alt="image" src="https://github.com/user-attachments/assets/e7dcd483-5ba3-4e01-98e6-9c6be2c577fd" />

<img width="933" height="423" alt="image" src="https://github.com/user-attachments/assets/96662d07-adc9-4ee6-83c3-9bde30dd37c2" />
<img width="765" height="489" alt="image" src="https://github.com/user-attachments/assets/335c862c-d55d-4f6d-8174-36a3d4192048" />
<img width="713" height="205" alt="image" src="https://github.com/user-attachments/assets/33785940-f7f3-4d1d-9b95-01443fc56260" />

serial diya thakle tavle e sagiye likbo then solve korbo
 <img width="896" height="465" alt="image" src="https://github.com/user-attachments/assets/f66e9fd0-6db2-4dbc-9fea-aa3f6ccc6f5f" />
<img width="722" height="765" alt="image" src="https://github.com/user-attachments/assets/6c3ec917-b94d-41be-8b89-a908006d2055" />
<img width="739" height="303" alt="image" src="https://github.com/user-attachments/assets/e0c803d8-253f-4f45-a53c-5203fb255d7d" />



**Conflict Operations:**

<img width="479" height="217" alt="image" src="https://github.com/user-attachments/assets/467a865c-89e6-49b2-9e0b-13f398d29951" />

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

<img width="927" height="492" alt="image" src="https://github.com/user-attachments/assets/b8a1034a-e637-4692-b62d-d1a2beeb36b5" />
<img width="812" height="558" alt="image" src="https://github.com/user-attachments/assets/763a9158-cc0f-4fb7-99f0-64b23d192a05" />

make all posible combination : 
Three conditions must be satisfied:

1. Initial Read: Both schedules read the initial value of a data item.
2. Read-from Relationship: Both schedules read data written by the same transaction.
3. Final Write: Both schedules have the same final writer for each data item.

<img width="1124" height="611" alt="image" src="https://github.com/user-attachments/assets/dbab7d49-34be-4105-8fdc-413f116f9188" />

non serial schedule convert into serial schedule.
<img width="1104" height="764" alt="image" src="https://github.com/user-attachments/assets/767ba894-5d7f-4119-b050-c98a529bec25" />

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

A schedule is Non-Recoverable if The writer transaction  commit after the reader transaction commits.
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

Strict Schedule: A transaction cannot Read or Write data until the transaction that last wrote that data commits or aborts.

সহজ বাংলা: কোনো Transaction data Write করলে, সেটি Commit বা Rollback না করা পর্যন্ত অন্য Transaction সেই data Read বা Write করতে পারবে না।

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

<img width="728" height="484" alt="image" src="https://github.com/user-attachments/assets/28a93f2e-1edb-44d6-a69d-33f56842d338" />
# Deadlock in DBMS

## 1. What is Deadlock?

A **Deadlock** is a situation in a Database Management System (DBMS) where two or more transactions wait indefinitely for resources locked by each other.

As a result, none of the transactions can proceed.

**In simple words:** When two or more transactions wait for each other to release resources, this situation is called Deadlock.

---

## 2. Deadlock Example

Suppose we have two resources:

- Resource A
- Resource B

And two transactions: T1 and T2.

### Transaction T1

```sql
LOCK(A);
LOCK(B);
```

### Transaction T2

```sql
LOCK(B);
LOCK(A);
```

### Execution Scenario

| Transaction T1 | Transaction T2 |
|---|---|
| Locks Resource A | |
| | Locks Resource B |
| Waits for Resource B | |
| | Waits for Resource A |

**Result:**

- T1 holds Resource A and waits for Resource B.
- T2 holds Resource B and waits for Resource A.
- Neither transaction can proceed.

This situation is called **Deadlock**.

---

## 3. Four Necessary Conditions of Deadlock
<img width="787" height="310" alt="image" src="https://github.com/user-attachments/assets/0d2815d5-7e4c-4fe4-8af2-c84c19c7ef47" />


Deadlock occurs when all four conditions exist simultaneously.

### 1. Mutual Exclusion

A resource can be used by only one transaction at a time.

### 2. Hold and Wait

A transaction holds one resource while waiting for another resource.

### 3. No Preemption

A resource cannot be forcibly taken away from a transaction. It must be released voluntarily.

### 4. Circular Wait

Two or more transactions wait for resources in a circular chain.

**Remember: M-H-N-C**

- M = Mutual Exclusion
- H = Hold and Wait
- N = No Preemption
- C = Circular Wait

---

## 4. Deadlock Handling Techniques

There are four major techniques for handling deadlocks.

### 1. Deadlock Prevention

```
Deadlock হওয়ার আগেই চারটি condition-এর যেকোনো একটি ভেঙে দেওয়া হয়।
Prevent deadlock before it happens by eliminating at least one of the four necessary conditions.

Example: Prevent Hold and Wait by requiring a transaction to request all required resources before execution.

Wait-Die Scheme in DBMS
Wait-Die Scheme হলো একটি Deadlock Prevention Technique, যা Timestamp-based protocol ব্যবহার করে Deadlock প্রতিরোধ করে।

এখানে Transaction-এর বয়স (Timestamp) অনুযায়ী সিদ্ধান্ত নেওয়া হয় কোন Transaction অপেক্ষা করবে এবং কোন Transaction abort হবে।
1. Basic Concept
- Older Transaction: যে Transaction আগে শুরু হয়েছে (smaller timestamp)।
- Younger Transaction: যে Transaction পরে শুরু হয়েছে (larger timestamp)।
Wait-Die Scheme-এর নিয়ম:
1. Older Transaction যদি Younger Transaction-এর Resource চায় → Wait করবে।
2. Younger Transaction যদি Older Transaction-এর Resource চায় → Die (Abort) হবে।
Wait-Die Rules
Wait
Older → Younger

Older Transaction অপেক্ষা করবে।

Die (Abort)
Younger → Older

Younger Transaction abort হবে।


2. Example
ধরি:
- T1 → Timestamp = 5 (Older)
- T2 → Timestamp = 10 (Younger)
এখন দুটি পরিস্থিতি দেখি।

Case 1: T1 requests a resource held by T2
- T1 is Older.
- T2 is Younger.
- T1 will Wait.
Result: T1 → Wait

Case 2: T2 requests a resource held by T1
- T2 is Younger.
- T1 is Older.
- T2 will Die (Abort).
Result: T2 → Abort
Wound-Wait Scheme (Deadlock Prevention in DBMS)
Wound-Wait Scheme হলো DBMS-এর একটি Deadlock Prevention Technique। এটি Timestamp-based protocol ব্যবহার করে deadlock প্রতিরোধ করে।

এখানে দুটি Transaction-এর বয়স (Timestamp) তুলনা করে সিদ্ধান্ত নেওয়া হয় কোন Transaction অপেক্ষা করবে এবং কোন Transaction abort হবে।
1. Basic Rules
Wound-Wait Scheme-এ:
- Older Transaction: যে Transaction আগে শুরু হয়েছে (ছোট Timestamp)।
- Younger Transaction: যে Transaction পরে শুরু হয়েছে (বড় Timestamp)।
দুটি নিয়ম:
1. Older Transaction যদি Younger Transaction-এর Lock চায় → Younger Transaction-কে Abort (Wound) করা হবে।
2. Younger Transaction যদি Older Transaction-এর Lock চায় → Younger Transaction অপেক্ষা করবে (Wait)।
2. Example
ধরি:
- T1 Timestamp = 5 (Older)
- T2 Timestamp = 10 (Younger)
Case 1: Older requests Younger’s lock
Wound – Abort
T1 wants a lock held by T2.
T1 (Older)

T2 (Younger)

T2 will be aborted, and T1 gets the lock.

Case 2: Younger requests Older’s lock
Wait
T2 wants a lock held by T1.
T2 (Younger)

T1 (Older)

T2 must wait until T1 releases the lock.
```

### 2. Deadlock Avoidance
Transaction execute করার আগে check করা হয় Deadlock হওয়ার সম্ভাবনা আছে কি না।
Before allocating resources, check whether the allocation keeps the system in a safe state.

**Example:** Banker's Algorithm.

### 3. Deadlock Detection
<img width="817" height="601" alt="image" src="https://github.com/user-attachments/assets/350c8487-d31b-4fca-9ad8-38b906a7a779" />

Allow deadlocks to occur and periodically check whether a deadlock exists.

**Example:** Wait-for Graph.

If a cycle exists in a Wait-for Graph, a deadlock exists when each resource type has only one instance.

### 4. Deadlock Recovery
Deadlock detect হওয়ার পর কোনো একটি Transaction rollback বা terminate করে Lock release করা হয়।
After detecting a deadlock, take action to resolve it.

Common approaches:

- Abort one or more transactions.
- Rollback a transaction.
- Release locked resources.

---

## 5. Wait-for Graph

A Wait-for Graph is used for deadlock detection.

- Each node represents a transaction.
- An edge `T1 → T2` means T1 is waiting for a resource held by T2.
- A cycle indicates deadlock when each resource has a single instance.

### Example

```text
T1 → T2
↑     ↓
└─────┘
```

Here:

- T1 waits for T2.
- T2 waits for T1.
- A cycle exists.
- Therefore, Deadlock occurs.

---

## 6. Deadlock vs Starvation

| Deadlock | Starvation |
|---|---|
| Transactions wait for each other indefinitely. | A transaction waits indefinitely because resources keep being allocated to others. |
| Circular waiting may occur. | Circular waiting is not necessary. |
| No transaction in the deadlocked cycle can proceed. | Other transactions may continue executing. |
| Resolved through deadlock recovery. | Resolved through fair scheduling or resource allocation. |

---

## 7. Important Algorithms

| Algorithm | Purpose |
|---|---|
| Banker's Algorithm | Deadlock Avoidance |
| Wait-for Graph | Deadlock Detection |
| Resource Allocation Graph | Deadlock Analysis |

---

<img width="573" height="220" alt="image" src="https://github.com/user-attachments/assets/26ff3fad-d557-42db-b235-7c26689cb49d" />

- Concurrency = Multiple transactions execute in overlapping time periods.
- Concurrency Control = Managing concurrent transactions to maintain data consistency.

  ```
  Overlapping Time Periods অর্থ হলো সময়ের মধ্যে একটির সাথে অন্যটির মিল থাকা বা সময়ের কিছু অংশ একসাথে চলা।

সহজভাবে: একটি কাজ শেষ হওয়ার আগেই অন্য একটি কাজ শুরু হলে, তাদের সময়ের মধ্যে Overlap থাকে।

Example:
- Task A: সকাল ১০:০০ – ১০:৩০
- Task B: সকাল ১০:১৫ – ১০:৪৫
এখানে দুটি কাজের সময় ১০:১৫ থেকে ১০:৩০ পর্যন্ত একসাথে চলছে।

এটাই Overlapping Time Periods।
```
