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
* It visually represents the relationships between different entities in a database. It is widely used in database design to help define the structure before creating the actual 
  database.

  ** what is Entity? **
   * An entity represents a real-world object or concept that can have data stored about it. (table)
   * Example: A "Student" in a school database or a "Product" in an e-commerce database.
    
  ** what is Attribute? **
   * Attributes provide more information about an entity. Each entity has a set of attributes that describe its characteristics.
   * Example: The "Student" entity might have attributes like "Name", "Age", and "Enrollment Number".
 
 ** waht is Relationship? **
  * A relationship represents an association between two or more entities.
  * Example: A "Student" enrolls in a "Course". The relationship here is "enrolls", which connects "Student" and "Course".
   
 ** what is key? **
  * a key is an attribute (or set of attributes) that is used to uniquely identify rows (records) in a table. Keys ensure that data in the table remains unique, accurate, and linked     
   across related tables.
   
 ** Types of Keys: **
   
   ** Primary Key : **
    * Cannot be NULL and must be unique.
    *  Example: student_id in a Students table.
      
   ** Candidate Key : **
    * A field (or combination of fields) that can qualify as a primary key.
    * There can be multiple candidate keys in one table.
    * One of them is chosen as the primary key.
    * Example: email and username in a Users table can both be candidate keys.
      
   ** Alternate Key **
    * Candidate keys that were not chosen as the primary key.
    * Example: If email is chosen as the primary key, then username becomes an alternate key.
      
   ** Composite Key **
    * A key that is made up of two or more attributes to uniquely identify a record.
    * Example: In an Enrollment table, student_id + course_id could form a composite key.
      
   ** Foreign Key **
    * A field in one table that refers to the primary key of another table.
    * It creates a relationship between two tables.
    * Example: student_id in Enrollments table refers to student_id in Students table.
      
   ** Super Key **
    * Any combination of columns that uniquely identifies a row.
    * Every primary key is a super key, but not every super key is a primary key.
    * Example: student_id, or student_id + email both are super keys if they uniquely identify records.

 ** what is Cardinality? **
  * Cardinality defines the number of instances of one entity that can be associated with instances of another entity.

 ** Types of cardinality: **
  * One-to-One (1:1): One record in the first entity is associated with exactly one record in the second entity.
  * One-to-Many (1:M): One record in the first entity can be associated with multiple records in the second entity.
  * Many-to-Many (M:N): Multiple records in the first entity can be associated with multiple records in the second entity.

** ER Diagrams (ER- Entity Relation) **
 * An ER diagram is a graphical representation of the ER model, showing entities, their attributes, and the relationships between them.
  
** Mapping ER Model to Relational Model **
  
** Relational Model Concepts **
  
** Schema and Instance **
 ** Schema :**
  * Definition: Schema is the blueprint or structure of a database. It defines how the data is organized and how the relationships between data are handled.
  Example :
  ```
  Student(StudentID INT, Name VARCHAR(50), Age INT)
  ```
  This tells us the table has 3 columns: StudentID, Name, and Age.

 ** Instance : **
  * Definition: Instance is the actual content or data stored in the database at a particular moment.
  Example: 
 | StudentID | Name     | Age |
 |-----------|----------|-----|
 | 1         | Asraful  | 22  |
 | 2         | Riya     | 21  |
 | 3         | Karim    | 23  |
 This table content is the instance — the current data inside the table.

 
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
