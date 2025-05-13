# 📚 Database Management System (DBMS) Topics

## 📘 Core Concepts

* Introduction to DBMS

  * **Definition:** A DBMS is a software system that allows creation, management, and use of databases.
  * **Purpose:** To provide a way to store and retrieve database information that is both convenient and efficient.
  * **Examples of DBMS:** MySQL, PostgreSQL, Oracle, Microsoft SQL Server, MongoDB

* Database vs. File System

  * **Key Differences**

  | Feature                 | File System                                           | Database (DBMS)                                            |
  | ----------------------- | ----------------------------------------------------- | ---------------------------------------------------------- |
  | **Data Storage**        | Stores data in files (e.g., .txt, .csv)               | Stores data in structured tables                           |
  | **Data Redundancy**     | High — same data may be stored in multiple files      | Low — uses normalization to reduce redundancy              |
  | **Data Access**         | Manual or through custom programs                     | Accessed using SQL queries                                 |
  | **Data Integrity**      | Hard to enforce                                       | Built-in constraints (e.g., primary & foreign keys)        |
  | **Security**            | Basic file-level protection                           | Role-based access control and permissions                  |
  | **Backup & Recovery**   | Manual and error-prone                                | Automated with recovery support                            |
  | **Concurrency Control** | Difficult — prone to conflicts in multi-user settings | Supports concurrent access and ACID properties             |
  | **Relationships**       | Not supported                                         | Supports relational data through table joins and keys      |
  | **Data Consistency**    | Difficult to maintain across files                    | High consistency maintained through transaction management |
  | **Scalability**         | Limited for large or complex datasets                 | Designed for large-scale applications                      |

  > ✅ **Conclusion:**
  > Use **File System** for simple, small-scale tasks.
  > Use **DBMS** for secure, consistent, and multi-user applications.

* Types of DBMS (Hierarchical, Network, Relational, NoSQL)

  | Type                  | Structure                    | Key Features                                                 | Examples                              |
  | --------------------- | ---------------------------- | ------------------------------------------------------------ | ------------------------------------- |
  | **Hierarchical DBMS** | Tree (one-to-many)           | Data organized in parent-child relationships                 | IBM IMS                               |
  | **Network DBMS**      | Graph (many-to-many)         | Allows complex relationships; children can have many parents | IDS, TurboIMAGE                       |
  | **Relational DBMS**   | Tables (rows and columns)    | Data stored in normalized tables; uses SQL                   | MySQL, PostgreSQL, Oracle, SQL Server |
  | **NoSQL DBMS**        | Key-Value / Document / Graph | Schema-less; handles unstructured/semi-structured data       | MongoDB, Redis, Cassandra, Neo4j      |

  > 📝 **Note:**
  >
  > * **RDBMS** is suitable for structured data and strong consistency.
  > * **NoSQL** is ideal for scalability and flexible schema requirements.

* DBMS Architecture (1-tier, 2-tier, 3-tier)

  | Architecture Type | Description                                                          | Layers Involved                               | Example Use Case                              |
  | ----------------- | -------------------------------------------------------------------- | --------------------------------------------- | --------------------------------------------- |
  | **1-Tier**        | The database and user interface run on the same machine              | DBMS + User directly on the same system       | Local personal DBMS (e.g., MS Access)         |
  | **2-Tier**        | The application communicates directly with the database server       | Client + Database Server                      | Small client-server apps (e.g., desktop apps) |
  | **3-Tier**        | Adds a middle layer between client and database for logic separation | Client + Application Server + Database Server | Web applications (frontend, backend, DB)      |

  > 📌 **Key Benefits of 3-Tier Architecture**
  >
  > * Better scalability and maintainability
  > * Improved security and performance
  > * Separation of concerns between UI, business logic, and data layer

## 🧩 Database Design

* Entity-Relationship (ER) Model

  * It visually represents the relationships between different entities in a database. It is widely used in database design to help define the structure before creating the actual database.

  **What is Entity?**

  * An entity represents a real-world object or concept that can have data stored about it. (table)
  * Example: A "Student" in a school database or a "Product" in an e-commerce database.

  **What is Attribute?**

  * Attributes provide more information about an entity. Each entity has a set of attributes that describe its characteristics.
  * Example: The "Student" entity might have attributes like "Name", "Age", and "Enrollment Number".

  **What is Relationship?**

  * A relationship represents an association between two or more entities.
  * Example: A "Student" enrolls in a "Course". The relationship here is "enrolls", which connects "Student" and "Course".

  **What is Key?**

  * A key is an attribute (or set of attributes) that is used to uniquely identify rows (records) in a table. Keys ensure that data in the table remains unique, accurate, and linked across related tables.

  **Types of Keys:**

  * **Primary Key:**

    * Cannot be NULL and must be unique.
    * Example: student\_id in a Students table.

  * **Candidate Key:**

    * A field (or combination of fields) that can qualify as a primary key.
    * There can be multiple candidate keys in one table.
    * One of them is chosen as the primary key.
    * Example: email and username in a Users table can both be candidate keys.

  * **Alternate Key:**

    * Candidate keys that were not chosen as the primary key.
    * Example: If email is chosen as the primary key, then username becomes an alternate key.

  * **Composite Key:**

    * A key that is made up of two or more attributes to uniquely identify a record.
    * Example: In an Enrollment table, student\_id + course\_id could form a composite key.

  * **Foreign Key:**

    * A field in one table that refers to the primary key of another table.
    * It creates a relationship between two tables.
    * Example: student\_id in Enrollments table refers to student\_id in Students table.

  * **Super Key:**

    * Any combination of columns that uniquely identifies a row.
    * Every primary key is a super key, but not every super key is a primary key.
    * Example: student\_id, or student\_id + email both are super keys if they uniquely identify records.

  **What is Cardinality?**

  * Cardinality defines the number of instances of one entity that can be associated with instances of another entity.

  **Types of Cardinality:**

  * One-to-One (1:1): One record in the first entity is associated with exactly one record in the second entity.
  * One-to-Many (1\:M): One record in the first entity can be associated with multiple records in the second entity.
  * Many-to-Many (M\:N): Multiple records in the first entity can be associated with multiple records in the second entity.

  **ER Diagrams (ER- Entity Relation)**

  * An ER diagram is a graphical representation of the ER model, showing entities, their attributes, and the relationships between them.

  **Mapping ER Model to Relational Model**

  **Relational Model Concepts**

  **Schema and Instance**

  * **Schema:**

    * Definition: Schema is the blueprint or structure of a database. It defines how the data is organized and how the relationships between data are handled.
    * Example:

    ```
    Student(StudentID INT, Name VARCHAR(50), Age INT)
    ```

    This tells us the table has 3 columns: StudentID, Name, and Age.

  * **Instance:**

    * Definition: Instance is the actual content or data stored in the database at a particular moment.
    * Example: 
      | StudentID | Name     | Age |
      |-----------|----------|-----|
      | 1         | Asraful  | 22  |
      | 2         | Riya     | 21  |
      | 3         | Karim    | 23  |
   This table content is the instance — the current data inside the table.

# 📐 Normalization

**Database Normalization** is the process of structuring a relational database to reduce data redundancy and improve data integrity. It involves decomposing large tables into smaller ones and defining relationships between them using a series of **normal forms**.

---

## 🔗 Functional Dependency

A **functional dependency** occurs when one attribute uniquely determines another attribute.

**Notation:** `A → B` means B is functionally dependent on A.

**Example:**

| StudentID | StudentName |
|-----------|-------------|
| 101       | Alice       |
| 102       | Bob         |

Here, `StudentID → StudentName`

---

## 📘 First Normal Form (1NF)

A table is in **1NF** if:

- All attributes contain only atomic (indivisible) values.
- Each record is unique.
- No repeating groups or arrays.

❌ **Not in 1NF:**

| StudentID | Name  | Courses           |
|-----------|-------|-------------------|
| 101       | Alice | Math, Physics     |
| 102       | Bob   | English, History  |

✅ **In 1NF (after fixing):**

| StudentID | Name  | Course    |
|-----------|-------|-----------|
| 101       | Alice | Math      |
| 101       | Alice | Physics   |
| 102       | Bob   | English   |
| 102       | Bob   | History   |

---

## 📙 Second Normal Form (2NF)

A table is in **2NF** if:

- It is in 1NF.
- All non-key attributes are **fully functionally dependent** on the entire primary key.

**❌ Not in 2NF (Partial dependency):**

| StudentID | CourseID | StudentName | CourseName |
|-----------|----------|-------------|------------|
| 101       | C01      | Alice       | Math       |
| 102       | C02      | Bob         | English    |

Here, `StudentName` depends only on `StudentID`, and `CourseName` only on `CourseID`.

✅ **Split into two tables:**

**Students Table:**

| StudentID | StudentName |
|-----------|-------------|
| 101       | Alice       |
| 102       | Bob         |

**Courses Table:**

| CourseID | CourseName |
|----------|------------|
| C01      | Math       |
| C02      | English    |

**Enrollment Table:**

| StudentID | CourseID |
|-----------|----------|
| 101       | C01      |
| 102       | C02      |

---

## 📗 Third Normal Form (3NF)

A table is in **3NF** if:

- It is in 2NF.
- There are **no transitive dependencies**.

**❌ Not in 3NF:**

| StudentID | StudentName | DepartmentID | DepartmentName |
|-----------|-------------|--------------|----------------|
| 101       | Alice       | D01          | Computer Science |
| 102       | Bob         | D02          | Literature       |

Here, `DepartmentName` is dependent on `DepartmentID`, not directly on `StudentID`.

✅ **Split into:**

**Students Table:**

| StudentID | StudentName | DepartmentID |
|-----------|-------------|--------------|
| 101       | Alice       | D01          |
| 102       | Bob         | D02          |

**Departments Table:**

| DepartmentID | DepartmentName     |
|--------------|--------------------|
| D01          | Computer Science   |
| D02          | Literature         |

---

## 📘 Boyce-Codd Normal Form (BCNF)

A table is in **BCNF** if:

- For every non-trivial functional dependency `X → Y`, X is a super key.

**❌ Not in BCNF:**

| Teacher | Subject | Room |
|---------|---------|------|
| Alice   | Math    | 101  |
| Bob     | Math    | 101  |

Assume:
- `Teacher → Subject`
- `Room → Subject`

Neither `Teacher` nor `Room` is a super key.

✅ **Decompose into:**

**Teacher_Subject Table:**

| Teacher | Subject |
|---------|---------|
| Alice   | Math    |
| Bob     | Math    |

**Room_Subject Table:**

| Room | Subject |
|------|---------|
| 101  | Math    |

---

## 🔁 Multivalued Dependency (4NF)

A **multivalued dependency** exists when one attribute is independent of another, but both depend on the same key.

**❌ Not in 4NF:**

| Employee | Skill     | Language  |
|----------|-----------|-----------|
| John     | Python    | English   |
| John     | Java      | English   |
| John     | Python    | Spanish   |
| John     | Java      | Spanish   |

✅ **Split into:**

**Employee_Skill Table:**

| Employee | Skill  |
|----------|--------|
| John     | Python |
| John     | Java   |

**Employee_Language Table:**

| Employee | Language |
|----------|----------|
| John     | English  |
| John     | Spanish  |

---

## 🔗 Join Dependency (5NF)

A **join dependency** exists when a table can be split into multiple tables and then recombined (joined) to recreate the original without loss of data.

Used in advanced normalization where there are complex many-to-many relationships.

---

## 🧩 Denormalization

**Denormalization** is the process of adding redundancy to improve read performance at the cost of update complexity.

**Example:**

Instead of joining multiple tables:

| OrderID | CustomerName | ProductName | Price |
|---------|--------------|-------------|-------|
| 501     | Alice        | Shirt       | $20   |

✅ Reduces query time but introduces redundancy (e.g., if Alice changes her name, multiple rows must be updated).

---

## ✅ Summary Table

| Normal Form | Key Condition                                       |
|-------------|-----------------------------------------------------|
| 1NF         | Atomic values, no repeating groups                  |
| 2NF         | 1NF + No partial dependencies                       |
| 3NF         | 2NF + No transitive dependencies                    |
| BCNF        | Every determinant is a super key                    |
| 4NF         | No multivalued dependencies                         |
| 5NF         | No join dependencies                                |




# 💬 SQL (Structured Query Language)

SQL is the standard language used to interact with relational databases. It is categorized into multiple sublanguages, each serving a specific purpose.

---

## 📘 DDL (Data Definition Language)

DDL is used to define and manage the structure of database objects such as tables, views, indexes, etc.

### ✅ Common Commands:
- `CREATE`
- `ALTER`
- `DROP`
- `TRUNCATE`

### ❌ Example Before:

You don’t have any structure defined.

✅ **Example After:**
```sql
CREATE TABLE Users (
  UserID INT PRIMARY KEY,
  Name VARCHAR(50),
  Email VARCHAR(100)
);
```

---

## 📗 DML (Data Manipulation Language)

DML is used to manipulate the data inside database tables.

### ✅ Common Commands:
- `INSERT`
- `UPDATE`
- `DELETE`
- `SELECT`

### ❌ Empty Table:

| UserID | Name  | Email       |
|--------|-------|-------------|
|        |       |             |

✅ **After Insert:**
```sql
INSERT INTO Users (UserID, Name, Email)
VALUES (1, 'Alice', 'alice@example.com');
```

| UserID | Name  | Email            |
|--------|-------|------------------|
| 1      | Alice | alice@example.com|

---

## 🛡️ DCL (Data Control Language)

DCL is used to control access to the database and define user privileges.

### ✅ Common Commands:
- `GRANT`
- `REVOKE`

✅ **Grant Permissions:**
```sql
GRANT SELECT, INSERT ON Users TO 'readonly_user';
```

✅ **Revoke Permissions:**
```sql
REVOKE INSERT ON Users FROM 'readonly_user';
```

---

## 🔄 TCL (Transaction Control Language)

TCL is used to manage changes made by DML statements and group them into logical transactions.

### ✅ Common Commands:
- `BEGIN`
- `COMMIT`
- `ROLLBACK`
- `SAVEPOINT`

✅ **Example Transaction:**
```sql
BEGIN;
UPDATE Accounts SET Balance = Balance - 100 WHERE AccountID = 1;
UPDATE Accounts SET Balance = Balance + 100 WHERE AccountID = 2;
COMMIT;
```

❌ If something fails, rollback:
```sql
ROLLBACK;
```

---

## 🔗 Joins

Joins combine rows from two or more tables based on related columns.

---

### 🔸 INNER JOIN

Returns only matching rows.

```sql
SELECT Orders.OrderID, Customers.Name
FROM Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

---

### 🔸 LEFT JOIN

Returns all rows from the left table and matched rows from the right table.

```sql
SELECT Customers.Name, Orders.OrderID
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

---

### 🔸 RIGHT JOIN

Returns all rows from the right table and matched rows from the left table.

```sql
SELECT Orders.OrderID, Customers.Name
FROM Customers
RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

---

### 🔸 FULL OUTER JOIN

Returns all rows when there is a match in either table.

```sql
SELECT Customers.Name, Orders.OrderID
FROM Customers
FULL OUTER JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

---

## 🧠 Subqueries & Nested Queries

A subquery is a query within another query, useful for filtering or deriving data.

✅ **Subquery in WHERE clause:**
```sql
SELECT Name FROM Employees
WHERE DepartmentID = (
  SELECT DepartmentID FROM Departments WHERE DepartmentName = 'HR'
);
```

✅ **Subquery in FROM clause:**
```sql
SELECT d.AvgSalary FROM (
  SELECT DepartmentID, AVG(Salary) AS AvgSalary
  FROM Employees
  GROUP BY DepartmentID
) d;
```

✅ **Correlated Subquery:**
```sql
SELECT Name FROM Employees e1
WHERE Salary > (
  SELECT AVG(Salary)
  FROM Employees e2
  WHERE e2.DepartmentID = e1.DepartmentID
);
```

---

## 🚀 Indexes

Indexes are used to speed up searches and queries on tables.

✅ **Create Index:**
```sql
CREATE INDEX idx_name ON Employees(Name);
```

✅ **Drop Index:**
```sql
DROP INDEX idx_name;
```

---

## 👁️ Views

Views are virtual tables based on the result of an SQL query.

✅ **Create View:**
```sql
CREATE VIEW HR_Employees AS
SELECT Name, Department FROM Employees WHERE Department = 'HR';
```

✅ **Use View:**
```sql
SELECT * FROM HR_Employees;
```

✅ **Drop View:**
```sql
DROP VIEW HR_Employees;
```

---

## 📋 Summary Table

| Category | Description                     | Example Commands                             |
|----------|---------------------------------|----------------------------------------------|
| DDL      | Define structure                | `CREATE`, `ALTER`, `DROP`, `TRUNCATE`        |
| DML      | Manipulate data                 | `INSERT`, `UPDATE`, `DELETE`, `SELECT`       |
| DCL      | Control user access             | `GRANT`, `REVOKE`                            |
| TCL      | Manage transactions             | `BEGIN`, `COMMIT`, `ROLLBACK`, `SAVEPOINT`   |
| Joins    | Combine tables                  | `INNER`, `LEFT`, `RIGHT`, `FULL OUTER`       |
| Subquery | Query inside a query            | `SELECT ... WHERE (...)`                     |
| Indexes  | Speed up data access            | `CREATE INDEX`, `DROP INDEX`                 |
| Views    | Virtual tables from SELECT      | `CREATE VIEW`, `SELECT`, `DROP VIEW`         |

---

> 💡 Mastering SQL is essential for backend development, data analytics, and database design.  
> 🛠️ Use this reference as a cheat sheet while working with SQL queries and designing schemas.

## 🔁 Transaction Management

* ACID Properties
* Transactions and Concurrency
* Serializability
* Concurrency Control Techniques (Locking, Timestamping)

## 💾 Storage and File Structure

* File Organization
* Buffer Management
* Indexing (Single-level, Multi-level, B+ Tree, Hashing)

## 🧮 Query Processing and Optimization

* Query Execution Plan
* Heuristics and Cost-Based Optimization

## 🔐 Security & Authorization

* Authentication and Authorization
* Data Security and Integrity Constraints

## ⚠️ Database Recovery

* Failure Types
* Recovery Techniques (Log-based, Checkpointing)

## 🔌 Advanced Topics (Optional)

* Distributed Databases
* NoSQL Databases
* Big Data and DBMS
* Cloud Databases
* Object-oriented DBMS
* Data Warehousing and OLAP
