# 📚 Database Management System (DBMS) Topics

## 📘 Core Concepts
- Introduction to DBMS
  * Definition: A DBMS is a software system that allows creation, management, and use of databases.
  * Purpose: To provide a way to store and retrieve database information that is both convenient and efficient.
  * Examples of DBMS: MySQL, PostgreSQL, Oracle, Microsoft SQL Server, MongoDB

- Database vs. File System
  * Key Differences
  
   | Feature                 | File System                                              | Database (DBMS)                                            |
  |------------------------|----------------------------------------------------------|------------------------------------------------------------|
  | **Data Storage**        | Stores data in files (e.g., .txt, .csv)                  | Stores data in structured tables                           |
  | **Data Redundancy**     | High — same data may be stored in multiple files         | Low — uses normalization to reduce redundancy              |
  | **Data Access**         | Manual or through custom programs                        | Accessed using SQL queries                                 |
  | **Data Integrity**      | Hard to enforce                                          | Built-in constraints (e.g., primary & foreign keys)        |
  | **Security**            | Basic file-level protection                              | Role-based access control and permissions                  |
  | **Backup & Recovery**   | Manual and error-prone                                   | Automated with recovery support                            |
  | **Concurrency Control** | Difficult — prone to conflicts in multi-user settings    | Supports concurrent access and ACID properties             |
  | **Relationships**       | Not supported                                            | Supports relational data through table joins and keys      |
  | **Data Consistency**    | Difficult to maintain across files                       | High consistency maintained through transaction management |
  | **Scalability**         | Limited for large or complex datasets                    | Designed for large-scale applications                      |

  > ✅ **Conclusion:**  
  > Use **File System** for simple, small-scale tasks.  
  > Use **DBMS** for secure, consistent, and multi-user applications.

  
- Types of DBMS (Hierarchical, Network, Relational, NoSQL)

  | Type                | Structure                     | Key Features                                                | Examples                             |
  |---------------------|-------------------------------|-------------------------------------------------------------|--------------------------------------|
  | **Hierarchical DBMS** | Tree (one-to-many)            | Data organized in parent-child relationships                | IBM IMS                              |
  | **Network DBMS**     | Graph (many-to-many)           | Allows complex relationships; children can have many parents| IDS, TurboIMAGE                      |
  | **Relational DBMS**  | Tables (rows and columns)      | Data stored in normalized tables; uses SQL                  | MySQL, PostgreSQL, Oracle, SQL Server|
  | **NoSQL DBMS**       | Key-Value / Document / Graph   | Schema-less; handles unstructured/semi-structured data      | MongoDB, Redis, Cassandra, Neo4j     |

  > 📝 **Note:**  
  > - **RDBMS** is suitable for structured data and strong consistency.  
  > - **NoSQL** is ideal for scalability and flexible schema requirements.

- DBMS Architecture (1-tier, 2-tier, 3-tier)

  | Architecture Type | Description                                                                 | Layers Involved                              | Example Use Case                           |
  |-------------------|-----------------------------------------------------------------------------|-----------------------------------------------|--------------------------------------------|
  | **1-Tier**         | The database and user interface run on the same machine                     | DBMS + User directly on the same system        | Local personal DBMS (e.g., MS     Access)       |
  | **2-Tier**         | The application communicates directly with the database server              | Client + Database Server                       | Small client-server apps (e.g., desktop apps)|
  | **3-Tier**         | Adds a middle layer between client and database for logic separation        | Client + Application Server + Database Server | Web applications (frontend, backend, DB)    |

  > 📌 **Key Benefits of 3-Tier Architecture**  
  > - Better scalability and maintainability  
  > - Improved security and performance  
  > - Separation of concerns between UI, business logic, and data layer
  

## 🧩 Database Design
- Entity-Relationship (ER) Model
- ER Diagrams
- Mapping ER Model to Relational Model
- Relational Model Concepts
- Schema and Instance

## 📐 Normalization
- Functional Dependency
- 1NF, 2NF, 3NF, BCNF
- Multivalued and Join Dependencies
- Denormalization

## 💬 SQL (Structured Query Language)
- DDL (Data Definition Language)
- DML (Data Manipulation Language)
- DCL (Data Control Language)
- TCL (Transaction Control Language)
- Joins (INNER, LEFT, RIGHT, FULL)
- Subqueries and Nested Queries
- Indexes and Views

## 🔁 Transaction Management
- ACID Properties
- Transactions and Concurrency
- Serializability
- Concurrency Control Techniques (Locking, Timestamping)

## 💾 Storage and File Structure
- File Organization
- Buffer Management
- Indexing (Single-level, Multi-level, B+ Tree, Hashing)

## 🧮 Query Processing and Optimization
- Query Execution Plan
- Heuristics and Cost-Based Optimization

## 🔐 Security & Authorization
- Authentication and Authorization
- Data Security and Integrity Constraints

## ⚠️ Database Recovery
- Failure Types
- Recovery Techniques (Log-based, Checkpointing)

## 🔌 Advanced Topics (Optional)
- Distributed Databases
- NoSQL Databases
- Big Data and DBMS
- Cloud Databases
- Object-oriented DBMS
- Data Warehousing and OLAP
