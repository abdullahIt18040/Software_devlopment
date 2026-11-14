# Database and DBMS

## 1. Database
A **Database** is an organized collection of related data that can be easily accessed, managed, and updated.

Example: Customer, Account, Employee, and Transaction records.

## 2. DBMS
**DBMS (Database Management System)** is software that is used to create, store, retrieve, update, and manage data in a database.

Examples: MySQL, PostgreSQL, Oracle, SQL Server.

## 3. Database vs DBMS

| Database | DBMS |
|---|---|
| Collection of data | Software to manage data |
| Stores information | Controls information |
| Example: BankDB | Example: PostgreSQL |

## 4. Types of DBMS
1. Hierarchical DBMS
2. Network DBMS
3. Relational DBMS (RDBMS)
4. Object-Oriented DBMS

## 5. Main Functions of DBMS
- Data Storage and Retrieval
- Data Security
- Backup and Recovery
- Data Integrity
- Concurrency Control
- Transaction Management

**Remember:**
- Database = Collection of Data
- DBMS = Software to Manage Data
- RDBMS = Table-based Database Management System

 # DBMS vs File System

## 1. File System
A **File System** stores and manages data in separate files (e.g., TXT, CSV, Excel).

Example: Student information stored in a `students.txt` file.

## 2. DBMS

**DBMS (Database Management System)** is software used to store, retrieve, update, and manage data in an organized database.

Example: MySQL, PostgreSQL, Oracle.

## 3. Difference Between DBMS and File System

| File System | DBMS |
|---|---|
| Stores data in files | Stores data in databases |
| Data redundancy is high | Reduces data redundancy |
| Limited security | Better security |
| Difficult data sharing | Easy data sharing |
| Limited backup and recovery | Provides backup and recovery |
| Difficult concurrent access | Supports concurrency control |
| Data inconsistency may occur | Helps maintain consistency |
| No built-in transaction management | Supports transactions |
# RDBMS (Relational Database Management System)

## 1. What is RDBMS?
**RDBMS** is a type of DBMS that stores data in tables (rows and columns) and establishes relationships between tables using keys.

Example: MySQL, PostgreSQL, Oracle, SQL Server.

## 2. Main Components
- **Table:** Collection of related data.
- **Row (Record):** A single data entry.
- **Column (Field):** An attribute of data.
- **Primary Key:** Uniquely identifies each row.
- **Foreign Key:** Establishes relationships between tables.

## 3. Example

**Student Table**

| ID (PK) | Name | Dept |
|---|---|---|
| 1 | Abdullah | CSE |
| 2 | Rahim | ICT |

**Department Table**

| Dept_ID (PK) | Dept_Name |
|---|---|
| 101 | CSE |
| 102 | ICT |

## 4. Features of RDBMS
- Stores data in tables.
- Maintains relationships between tables.
- Supports SQL.
- Reduces data redundancy.
- Maintains data integrity.
- Supports ACID properties.
- Provides security and concurrency control.

## 5. DBMS vs RDBMS

| DBMS | RDBMS |
|---|---|
| General database management system | Relational database management system |
| May use different data models | Uses relational tables |
| Relationships are not mandatory | Relationships use keys |
| May not support ACID fully | Supports ACID transactions |

**Remember:**

RDBMS = Tables + Rows + Columns + Relationships + Keys
# NoSQL Database

## 1. What is NoSQL?
**NoSQL (Not Only SQL)** is a non-relational database used to store and manage structured, semi-structured, and unstructured data.

Examples: MongoDB, Redis, Cassandra, CouchDB.

## 2. Types of NoSQL Database

1. **Document Database:** Stores data in JSON-like documents. Example: MongoDB.
2. **Key-Value Database:** Stores data as key-value pairs. Example: Redis.
3. **Column-Family Database:** Stores data in column families. Example: Cassandra.
4. **Graph Database:** Stores data as nodes and relationships. Example: Neo4j.

## 3. Features of NoSQL
- Flexible schema.
- Handles large amounts of data.
- Horizontal scalability.
- High availability.
- Supports distributed databases.
- Suitable for unstructured and semi-structured data.

## 4. RDBMS vs NoSQL

| RDBMS | NoSQL |
|---|---|
| Relational database | Non-relational database |
| Stores data in tables | Stores data in different models |
| Fixed schema (typically) | Flexible schema (typically) |
| Uses SQL | Uses different query methods |
| Relationships through keys | Relationships depend on database model |
| Commonly used for structured data | Suitable for Horizontal Scalling |
| Example: PostgreSQL | Example: MongoDB |

## 5. When to Use?
- **RDBMS:** Banking, accounting, financial transactions.
- **NoSQL:** Big data, caching, real-time applications, IoT.

**Remember:**
- RDBMS = Relational + Tables + SQL.
- NoSQL = Non-relational + Flexible Data Models.
- NoSQL means "Not Only SQL", not "No SQL".
# Horizontal Scaling vs Vertical Scaling

## 1. Vertical Scaling (Scale Up)
Vertical scaling means increasing the resources (CPU, RAM, Storage) of an existing server to handle more workload.

**Example:**
- 8 GB RAM → 32 GB RAM
- 4 CPU Cores → 16 CPU Cores

## 2. Horizontal Scaling (Scale Out)
Horizontal scaling means adding more servers or machines to distribute the workload.

**Example:**
- 1 Server → 3 Servers
- Multiple servers handle incoming requests using a Load Balancer.

## 3. Difference Between Horizontal and Vertical Scaling

| Vertical Scaling | Horizontal Scaling |
|---|---|
| Adds resources to one server | Adds more servers |
| Scale Up | Scale Out |
| Hardware upgrade required | More machines required |
| Limited by server capacity | Can scale across multiple machines |
| May require downtime | Can often add servers without downtime |
| Single server failure can cause downtime | Better fault tolerance when properly designed |
| Example: Increasing RAM | Example: Adding servers |

## 4. Diagram

**Vertical Scaling:**
```text
     Existing Server
           |
     Upgrade CPU/RAM
           |
     Powerful Server
```

**Horizontal Scaling:**
```text
        Load Balancer
          /   |   \
         /    |    \
     Server  Server  Server
       1       2       3
```

## 5. Real-World Examples
- Vertical Scaling: Increasing RAM and CPU of a PostgreSQL server.
- Horizontal Scaling: Adding multiple application servers behind a load balancer.

**Remember:**
- Vertical Scaling = Increase server capacity (Scale Up).
- Horizontal Scaling = Increase number of servers (Scale Out).

  # Types of DBMS

## 1. Distributed DBMS (DDBMS)
A Distributed DBMS stores data across multiple locations or computers but manages them as a single database system.

**Example:** Distributed banking systems.

**Features:**
- Data stored at multiple locations.
- Supports data sharing.
- Improves availability and reliability.

## 2. Object-Oriented DBMS (OODBMS)
An Object-Oriented DBMS stores data in the form of objects, similar to Object-Oriented Programming (OOP).

**Example:** ObjectDB, db4o.

**Features:**
- Stores objects and classes.
- Supports inheritance.
- Supports encapsulation.

## 3. Network DBMS
A Network DBMS organizes data using a network structure where one record can have multiple parent and child records.

**Example:** IDMS.

**Features:**
- Supports many-to-many relationships.
- Uses links or pointers between records.
- More flexible than Hierarchical DBMS.

## Quick Comparison

| DBMS Type | Data Structure |
|---|---|
| Distributed DBMS | Multiple locations |
| Object-Oriented DBMS | Objects |
| Network DBMS | Network of records |

**Remember:**
- Distributed DBMS = Data across multiple locations.
- Object-Oriented DBMS = Data stored as objects.
- Network DBMS = Records connected through multiple relationships.
# ER Model (Entity-Relationship Model)

## 1. What is ER Model?
ER Model is a conceptual database model used to design database structures using Entities, Attributes, and Relationships.

## 2. Main Components

- **Entity:** A real-world object about which data is stored. Example: Student, Teacher.
- **Attribute:** Properties of an entity. Example: Student_ID, Name, Age.
- **Relationship:** Association between entities. Example: Student enrolls in Course.
Tuple: A tuple is a single row (record) in a database table.
<img width="778" height="419" alt="image" src="https://github.com/user-attachments/assets/aaed8358-bdb7-4a97-8113-9d91e6ebc450" />

## 3. ER Diagram Symbols

| Symbol | Meaning |
|---|---|
| Rectangle | Entity |
| Oval | Attribute |
| Diamond | Relationship |
| Underlined Attribute | Primary Key |
| Double Oval | Multivalued Attribute |
| Dashed Oval | Derived Attribute |
| Double Rectangle | Weak Entity |

## 4. Types of Relationships

| Relationship | Meaning | Example |
|---|---|---|
| One-to-One (1:1) | One to One | Person – Passport |
| One-to-Many (1:N) | One to Many | Department – Employees |
| Many-to-Many (M:N) | Many to Many | Students – Courses |

## 5. Example

```text
STUDENT ─── ENROLLS ─── COURSE
   |                         |
Student_ID               Course_ID
   |                         |
  Name                   Course_Name
```
# Types of Entity in DBMS (ER Model)

## 1. Strong Entity
A Strong Entity has its own Primary Key and can exist independently.

**Example:** Student, Employee.

- Has its own Primary Key.
- Exists independently.
- Represented by a Single Rectangle.

## 2. Weak Entity
A Weak Entity cannot be uniquely identified by its own attributes and depends on a Strong Entity.

**Example:** Employee's Dependent.

- Does not have a complete Primary Key of its own.
- Depends on a Strong Entity.
- Represented by a Double Rectangle.

## 3. Strong Entity vs Weak Entity

| Strong Entity | Weak Entity |
|---|---|
| Independent | Dependent |
| Has its own Primary Key | Uses owner's key with a partial key |
| Single Rectangle | Double Rectangle |
| Example: Employee | Example: Dependent |

**Remember:**
- Strong Entity = Independent Entity.
- Weak Entity = Dependent Entity.
<img width="815" height="655" alt="image" src="https://github.com/user-attachments/assets/14f61ee2-5576-402d-8098-709acf644597" />
# Types of Attributes in ER Model

An **Attribute** describes the properties or characteristics of an entity.

## 1. Simple Attribute
- Cannot be divided into smaller attributes.
- Symbol: Single Oval.
- Example: Age, Salary, Gender.

## 2. Composite Attribute
- Can be divided into smaller attributes.
- Symbol: Connected Ovals.
- Example: Name → First Name, Middle Name, Last Name.

## 3. Derived Attribute
- Value is calculated from another attribute.
- Symbol: Dashed Oval.
- Example: Age (calculated from DOB).

## 4. Multivalued Attribute
- Can contain multiple values for a single entity.
- Symbol: Double Oval.
- Example: Phone Number, Email, Skills.
- Example: One student can have multiple phone numbers.

## 5. Unique / Key Attribute
- Uniquely identifies each entity.
- Symbol: Underlined Attribute Name.
- Example: Student_ID, Employee_ID, NID.

  <img width="579" height="599" alt="image" src="https://github.com/user-attachments/assets/24ad083f-1b92-4f54-b4e7-92b457d23df3" />


## Quick Revision

| Attribute | Symbol | Example |
|---|---|---|
| Simple | Single Oval | Age |
| Composite | Connected Ovals | Name |
| Derived | Dashed Oval | Age from DOB |
| Multivalued | Double Oval | Phone |
| Unique / Key | Underlined Oval | Student_ID |

<img width="706" height="423" alt="image" src="https://github.com/user-attachments/assets/8e9e0e02-2b92-4356-9f5b-89b710531224" />

<img width="553" height="435" alt="image" src="https://github.com/user-attachments/assets/fd7beb0d-dbaa-4228-8a4b-070a737bd9ec" />
<img width="657" height="422" alt="image" src="https://github.com/user-attachments/assets/657c83be-74ed-4391-92fb-97ba5d3b6815" />
<img width="872" height="500" alt="image" src="https://github.com/user-attachments/assets/7a4be55e-2f3a-4a2d-80b6-4f32a9730896" />
Many-to-Many (M:N) relationship implement করার জন্য একটি third entity তৈরি করা হয়। একে Associative Entity, Junction Table অথবা Bridge Table বলে।
<img width="737" height="343" alt="image" src="https://github.com/user-attachments/assets/06c6a618-ed9a-423d-a9f1-7b628dc1bf2f" />

<img width="554" height="250" alt="image" src="https://github.com/user-attachments/assets/bc751c37-9dea-407f-8fcd-4e238ff9257b" />

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/e757e5de-16c6-43e3-8499-739248bac5d6" />
<img width="791" height="171" alt="image" src="https://github.com/user-attachments/assets/eedf5a5d-3f3f-4da6-8448-9630f3bcfbdc" />
<img width="996" height="639" alt="image" src="https://github.com/user-attachments/assets/4c5c2fb4-92bb-4d90-a9c5-961390c7d422" />

# DBMS Keys – Complete Notes
<img width="468" height="207" alt="image" src="https://github.com/user-attachments/assets/d9a16264-05c5-4044-aeb5-7dd099461428" />
<img width="478" height="304" alt="image" src="https://github.com/user-attachments/assets/9ddb6bd2-5b26-48fc-a512-5e170f2bc7b3" />

## 1. Super Key
- A Super Key is a set of one or more attributes that uniquely identifies a record.
- It may contain extra (unnecessary) attributes.
- Example: `{Student_ID}`, `{Student_ID, Name}`.

## 2. Candidate Key

- A Candidate Key is a minimal Super Key.
- It uniquely identifies each record.
- It contains no unnecessary attributes.
- A table can have multiple Candidate Keys.

## 3. Primary Key (PK)
- A Primary Key is a Candidate Key selected to uniquely identify each record.
- ## Must be unique.
- ## Cannot contain NULL values.
- Only one Primary Key constraint per table.

## 4. Alternate Key
- Candidate Keys that are not selected as the Primary Key are called Alternate Keys.
- Example: If `Student_ID` is PK and `Email` is another Candidate Key, then `Email` is an Alternate Key.

## 5. Foreign Key (FK)
- A Foreign Key is an attribute that references a Primary Key or a suitable UNIQUE key in another table.
- Establishes relationships between tables.
- Can contain duplicate values.
- Can contain NULL values unless restricted.

## 6. Composite Key
- A Composite Key consists of two or more attributes used together to uniquely identify a record.
- Example: `(Student_ID, Course_ID)`.

## 7. Unique Key
- Ensures that values in a column or combination of columns are unique.
- A table can have multiple UNIQUE constraints.
- NULL handling depends on the DBMS.

## 8. Simple Key
- A Simple Key consists of only one attribute.
- Example: `Student_ID`.

## 9. Natural Key
- A Natural Key has real-world meaning.
- Examples: Email, Passport_Number, National_ID.

## 10. Surrogate Key
- An artificially generated key with no business meaning.
- Examples: Auto-generated ID, Sequence ID.

## 11. Secondary Key
- An attribute used for searching or retrieving records.
- It does not necessarily uniquely identify a record.
- Example: Department_ID, City.

---

## Key Differences

| Key | Purpose |
|---|---|
| Super Key | Uniquely identifies records |
| Candidate Key | Minimal Super Key |
| Primary Key | Selected Candidate Key |
| Alternate Key | Remaining Candidate Keys |
| Foreign Key | Establishes relationships |
| Composite Key | Uses multiple attributes |
| Unique Key | Prevents duplicate values |
| Simple Key | Uses one attribute |
| Natural Key | Real-world meaningful key |
| Surrogate Key | Artificially generated key |
| Secondary Key | Helps search records |

## Relationship Between Keys

```text
       Super Key
           |
           v
     Candidate Key
           |
       Selection
       /       \
      v         v
 Primary Key  Alternate Key
```
**Remember:**
- PK = Unique + NOT NULL
- FK = Relationship between tables
- Candidate Key = Minimal Super Key
- Composite Key = Multiple attributes
- Alternate Key = Candidate Key not selected as PK

<img width="818" height="429" alt="image" src="https://github.com/user-attachments/assets/f87717a1-0f6f-4955-b597-b3d97a8106e6" />

# ANSWE 4 . ROLL NUMBER IS PRIMARY KEY BECAUSE . IT IS UNIQUE AND NOT NULL, BUT EMAIL CAN NULL.SO EMAIL IS NOT PRIMARY KEY

## 1. Index
- An Index is a data structure used to retrieve data quickly from a database table.
- Similar to an index in a book.
- Improves SELECT query performance.

## 2. Types of Index

1. **Primary Index:** Created based on the primary key in traditional ordered-file indexing.
2. **Secondary Index:** Created on a non-ordering attribute.
3. **Clustered Index:** Determines the physical order of records.
4. **Non-Clustered Index:** Stores index entries separately from table data.
5. **Unique Index:** Prevents duplicate indexed values.
6. **Composite Index:** Created using two or more columns.

## 3. Advantages
- Faster data searching.
- Improves SELECT performance.
- Helps sorting and filtering.

## 4. Disadvantages
- Requires extra storage.
- Slows down INSERT, UPDATE and DELETE operations due to index maintenance.

## 5. SQL Example

```sql
-- Create Index
CREATE INDEX idx_student_name
ON Student(Name);

-- Create Unique Index
CREATE UNIQUE INDEX idx_student_email
ON Student(Email);

-- Create Composite Index
CREATE INDEX idx_student_dept
ON Student(Dept_ID, Name);

-- Drop Index (syntax varies by DBMS)
DROP INDEX idx_student_name;
```

## 6. Important Exam Notes
- Index improves data retrieval speed.
- Index requires additional storage.
- Too many indexes can slow down write operations.
- Primary Key usually creates an index automatically.
- Composite Index uses multiple columns.

**Remember:**

`Index = Faster Searching + Extra Storage`

`More Indexes = Faster Reads + Potentially Slower Writes`

