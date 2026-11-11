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
