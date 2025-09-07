

# **DBMS Question Bank**

This section covers core concepts related to **databases**, including **SQL**, **NoSQL**, and **database design principles**.

---

## **Table of Contents**

- [**DBMS Question Bank**](#dbms-question-bank)
  - [**Table of Contents**](#table-of-contents)
  - [**Easy**](#easy)
    - [**What is the difference between SQL and NoSQL databases?**](#what-is-the-difference-between-sql-and-nosql-databases)
    - [**What are primary keys and foreign keys?**](#what-are-primary-keys-and-foreign-keys)
    - [**What is the difference between DELETE, TRUNCATE, and DROP commands in SQL?**](#what-is-the-difference-between-delete-truncate-and-drop-commands-in-sql)
  - [**Medium**](#medium)
    - [**What is database normalization? Explain 1NF, 2NF, and 3NF.**](#what-is-database-normalization-explain-1nf-2nf-and-3nf)
    - [**What are database indexes and why are they important?**](#what-are-database-indexes-and-why-are-they-important)
    - [**What are ACID properties in the context of a database transaction?**](#what-are-acid-properties-in-the-context-of-a-database-transaction)
  - [**Difficult**](#difficult)
    - [**Explain the different transaction isolation levels in SQL.**](#explain-the-different-transaction-isolation-levels-in-sql)
    - [**What is database sharding? How does it differ from partitioning?**](#what-is-database-sharding-how-does-it-differ-from-partitioning)
    - [**What is the N+1 query problem and how can you solve it?**](#what-is-the-n1-query-problem-and-how-can-you-solve-it)

---

## **Easy**

### **What is the difference between SQL and NoSQL databases?**

**Answer:**

* **SQL (Relational Databases):**

  * Stores data in a structured format using tables with rows and columns.
  * Predefined schema.
  * Uses SQL (Structured Query Language) for data manipulation.
  * Provides **ACID** (Atomicity, Consistency, Isolation, Durability) guarantees.
  * **Examples:** MySQL, PostgreSQL, Oracle.

* **NoSQL (Non-relational Databases):**

  * Stores data in formats like **document (JSON)**, key-value, wide-column, or graph.
  * Dynamic or flexible schema.
  * Designed for **scalability, flexibility, and high performance**.
  * Follows **BASE** (Basically Available, Soft state, Eventually consistent) model.
  * **Examples:** MongoDB, Redis, Cassandra.

**Hint:**
Think **"structure vs. flexibility"**.
SQL is like a **well-organized spreadsheet with fixed columns**.
NoSQL is like a **folder of flexible documents (like JSON files)**.

**Follow-up:**
*When would you choose a NoSQL database over a SQL database?*

---

### **What are primary keys and foreign keys?**

**Answer:**

* **Primary Key:**

  * Uniquely identifies each record in a table.
  * Must contain **unique values** and **cannot be NULL**.
  * A table can have **only one primary key**.

* **Foreign Key:**

  * Used to **link two tables together**.
  * A field (or fields) in one table that refers to the **PRIMARY KEY in another table**.
  * The table with the foreign key = **child table**, and the referenced table = **parent table**.

**Hint:**
A **primary key** is like a **student's unique ID number**.
A **foreign key** in an *Enrollments table* would be that same **student ID**, linking back to the specific student.

---

### **What is the difference between DELETE, TRUNCATE, and DROP commands in SQL?**

**Answer:**

* **DELETE:**

  * A **DML (Data Manipulation Language)** command.
  * Removes rows from a table based on a **WHERE** clause.
  * **Can be rolled back**.
  * Slower, removes rows one by one, logs each delete.

* **TRUNCATE:**

  * A **DDL (Data Definition Language)** command.
  * Removes **all rows** from a table.
  * **Cannot use WHERE clause**.
  * Usually **cannot be rolled back**.
  * Much faster than DELETE.

* **DROP:**

  * A **DDL command**.
  * Removes the **entire table** including structure, data, and constraints.
  * **Cannot be undone**.

**Hint:**
DELETE → removes **some rows**
TRUNCATE → removes **all rows (empties the table)**
DROP → removes the **entire table**

---

## **Medium**

### **What is database normalization? Explain 1NF, 2NF, and 3NF.**

**Answer:**
**Normalization** is the process of organizing columns and tables in a relational database to **minimize data redundancy and improve data integrity**.

* **First Normal Form (1NF):**

  * Columns contain **atomic (indivisible)** values.
  * No repeating groups of columns.

* **Second Normal Form (2NF):**

  * Table is in 1NF.
  * Every non-primary-key attribute is **fully functionally dependent** on the entire primary key.

* **Third Normal Form (3NF):**

  * Table is in 2NF.
  * All attributes depend only on the primary key, not on non-key attributes (**no transitive dependencies**).

**Hint:**

* 1NF: **No multi-value cells**.
* 2NF: **No partial dependencies on composite key**.
* 3NF: **No transitive dependencies** (e.g., `StudentID -> AdvisorID -> AdvisorName` → AdvisorName should be in Advisors table).

**Follow-up:**
*What is denormalization and when would you use it?*

---

### **What are database indexes and why are they important?**

**Answer:**
An **index** is a special lookup table that speeds up **data retrieval**.

* Works like an **index in a book** – instead of scanning the entire table, you look up the indexed values.
* Improves **SELECT query performance**.
* **Trade-off:** Slows down **INSERT, UPDATE, DELETE** because index updates are required.

**Hint:**
Think of a **phone book** sorted by last name.
Fast to find someone by name, slow to find by phone number.

**Follow-up:**
*What is a clustered vs. non-clustered index?*

---

### **What are ACID properties in the context of a database transaction?**

**Answer:**

* **Atomicity:** All or nothing.
* **Consistency:** Brings DB from one valid state to another.
* **Isolation:** Transactions don't interfere with each other.
* **Durability:** Committed data is permanent.

**Hint:**

* Atomicity = all or nothing
* Consistency = valid state
* Isolation = no interference
* Durability = saved forever

**Follow-up:**
*How does a database implement Isolation? (e.g., locking)*

---

## **Difficult**

### **Explain the different transaction isolation levels in SQL.**

**Answer:**

* **Read Uncommitted:** Allows dirty reads.
* **Read Committed:** Prevents dirty reads, but non-repeatable reads can occur.
* **Repeatable Read:** Prevents dirty & non-repeatable reads, but phantom reads can occur.
* **Serializable:** Full isolation, prevents all issues (but reduces concurrency).

**Hint:**

* Dirty Reads → solved by **Read Committed**
* Non-repeatable Reads → solved by **Repeatable Read**
* Phantom Reads → solved by **Serializable**

**Follow-up:**
*What is optimistic vs. pessimistic locking?*

---

### **What is database sharding? How does it differ from partitioning?**

**Answer:**

* **Sharding:**

  * Horizontal partitioning across **multiple servers**.
  * Each server holds a **subset of data**.
  * **Shared-nothing architecture** for scalability.

* **Partitioning:**

  * Splitting a table into **smaller pieces** within the **same database instance**.
  * Improves performance on a single node.

**Hint:**
Sharding = **scale out across servers**
Partitioning = **optimize inside one server**

**Follow-up:**
*What are some common sharding strategies (range-based, hash-based)?*

---

### **What is the N+1 query problem and how can you solve it?**

**Answer:**

* Happens when you make **1 query for main data** and then **N queries for related data**.
* Example: Fetch posts (1 query) → Fetch author for each post (N queries).

**Solution:**

* **JOIN:** Fetch all data in one query.
* **IN clause:** Fetch related data in a single query using `IN`.

**Hint:**
Common in ORMs.

**Follow-up:**
*When is JOIN less performant than IN clause?*