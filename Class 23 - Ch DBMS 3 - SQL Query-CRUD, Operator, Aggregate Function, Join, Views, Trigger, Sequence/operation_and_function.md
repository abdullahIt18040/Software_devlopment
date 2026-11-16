# CRUD in DBMS

## 1. What is CRUD?

**CRUD** stands for:

- **C – Create**
- **R – Read**
- **U – Update**
- **D – Delete**

CRUD represents the four basic operations used to manage data in a Database Management System (DBMS).

## 2. CRUD Operations with SQL

### 1. Create (INSERT)

Create means inserting new records into a database table.

```sql
INSERT INTO employees (id, name, salary)
VALUES (1, 'Abdullah', 30000);
```

**বাংলা:** Database-এ নতুন Record বা তথ্য যোগ করাকে Create বলে।

### 2. Read (SELECT)

Read means retrieving or viewing existing records from a database.

```sql
-- Retrieve all records
SELECT * FROM employees;

-- Retrieve a specific record
SELECT * FROM employees
WHERE id = 1;
```

**বাংলা:** Database থেকে সংরক্ষিত তথ্য দেখা বা পড়াকে Read বলে।

### 3. Update (UPDATE)

Update means modifying existing records in a database.

```sql
UPDATE employees
SET salary = 35000
WHERE id = 1;
```

**বাংলা:** Database-এ আগে থেকে থাকা তথ্য পরিবর্তন করাকে Update বলে।

### 4. Delete (DELETE)

Delete means removing existing records from a database.

```sql
DELETE FROM employees
WHERE id = 1;
```

**বাংলা:** Database থেকে কোনো Record মুছে ফেলাকে Delete বলে।

## 3. CRUD Summary

| CRUD | SQL Command | Description |
|---|---|---|
| Create | INSERT | Add new records |
| Read | SELECT | Retrieve records |
| Update | UPDATE | Modify existing records |
| Delete | DELETE | Remove records |

## 4. Important Notes

- CRUD is the foundation of database operations.
- CRUD is used in almost every software application.
- SQL provides commands to perform CRUD operations.
- CRUD operations are commonly implemented in REST APIs.

## 5. CRUD in REST API

| CRUD Operation | HTTP Method | Example Endpoint |
|---|---|---|
| Create | POST | `/api/employees` |
| Read | GET | `/api/employees` |
| Update | PUT / PATCH | `/api/employees/1` |
| Delete | DELETE | `/api/employees/1` |

## 6. Important Warning

Always use a `WHERE` condition when updating or deleting a specific record.

```sql
-- Without WHERE: Updates all records
UPDATE employees
SET salary = 35000;

-- Without WHERE: Deletes all records
DELETE FROM employees;
```

## 7. Remember

**CRUD = Create + Read + Update + Delete**

CRUD is the four fundamental operations for managing records in a database.
