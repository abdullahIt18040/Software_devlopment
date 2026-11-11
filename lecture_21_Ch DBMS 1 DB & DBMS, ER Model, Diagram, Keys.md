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

