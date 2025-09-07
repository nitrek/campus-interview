Question Bank: Database Management Systems (DBMS)
This section covers core concepts related to databases, including SQL, NoSQL, and database design principles.
Easy
Question: What is the difference between SQL and NoSQL databases?
Answer:
SQL (Relational Databases): They store data in a structured format using tables with rows and columns. They have a predefined schema and use SQL (Structured Query Language) for data manipulation. They are known for providing ACID (Atomicity, Consistency, Isolation, Durability) guarantees. Examples: MySQL, PostgreSQL, Oracle.
NoSQL (Non-relational Databases): They store data in various formats like document (JSON), key-value, wide-column, or graph. They typically have a dynamic or flexible schema and are designed for scalability, flexibility, and high performance. They often follow the BASE (Basically Available, Soft state, Eventually consistent) model. Examples: MongoDB, Redis, Cassandra.
Hint: Think "structure vs. flexibility." SQL is like a well-organized spreadsheet with fixed columns. NoSQL is like a folder of flexible documents (like JSON files).
Follow-up: "When would you choose a NoSQL database over a SQL database?"
Question: What are primary keys and foreign keys?
Answer:
Primary Key: A primary key is a constraint that uniquely identifies each record in a table. It must contain unique values and cannot contain NULL values. A table can have only one primary key.
Foreign Key: A foreign key is a key used to link two tables together. It is a field (or collection of fields) in one table that refers to the PRIMARY KEY in another table. The table containing the foreign key is the child table, and the table containing the primary key is the referenced or parent table.
Hint: A primary key is like a student's unique ID number. A foreign key in an Enrollments table would be that same student ID, linking the enrollment record back to the specific student.
Question: What is the difference between DELETE, TRUNCATE, and DROP commands in SQL?
Answer:
DELETE: This is a DML (Data Manipulation Language) command. It removes rows from a table based on a WHERE clause. You can roll back the changes. It is slower as it removes rows one by one and records an entry in the transaction log for each deleted row.
TRUNCATE: This is a DDL (Data Definition Language) command. It removes all rows from a table quickly. You cannot use a WHERE clause with it. The operation cannot be rolled back in most databases. It is much faster than DELETE.
DROP: This is a DDL command. It removes the entire table, including its structure, data, and constraints. This action cannot be undone.
Hint: DELETE removes some rows. TRUNCATE removes all rows (empties the table). DROP removes the entire table.
Medium
Question: What is database normalization? Explain 1NF, 2NF, and 3NF.
Answer: Normalization is the process of organizing columns and tables in a relational database to minimize data redundancy and improve data integrity.
First Normal Form (1NF): A table is in 1NF if all its columns contain atomic (indivisible) values, and each record is unique. There should be no repeating groups of columns.
Second Normal Form (2NF): A table is in 2NF if it is in 1NF and every non-primary-key attribute is fully functionally dependent on the entire primary key. This applies to tables with composite primary keys.
Third Normal Form (3NF): A table is in 3NF if it is in 2NF and all its attributes are dependent only on the primary key, not on other non-key attributes. There are no transitive dependencies.
Hint: 1NF: No multi-value cells. 2NF: No partial dependencies on a composite key. 3NF: No transitive dependencies (e.g., StudentID -> AdvisorID -> AdvisorName. AdvisorName should be in an Advisors table).
Follow-up: "What is denormalization and when would you use it?"
Question: What are database indexes and why are they important?
Answer: An index is a special lookup table that the database search engine can use to speed up data retrieval. An index is a pointer to data in a table. It works like an index in the back of a book; instead of searching the entire book (table), you look at the index to find the page number (data location) for a specific topic. They are important because they significantly improve the speed of query operations (especially SELECT queries with WHERE clauses), but they can slow down data modification operations (INSERT, UPDATE, DELETE) as the index also needs to be updated.
Hint: Think of a phone book sorted alphabetically by last name. That sorting is an index. It's fast to find someone by last name, but slow to find them by phone number.
Follow-up: "What is a clustered vs. a non-clustered index?"
Question: What are ACID properties in the context of a database transaction?
Answer: ACID is an acronym that describes the four key properties of a reliable database transaction:
Atomicity: A transaction is an "all or nothing" operation. It either completes fully, or it is rolled back entirely. There is no partial completion.
Consistency: A transaction brings the database from one valid state to another. Any data written to the database must be valid according to all defined rules, including constraints and triggers.
Isolation: The concurrent execution of transactions results in a system state that would be obtained if transactions were executed serially (one after another). A transaction in process and not yet committed must remain isolated from any other transaction.
Durability: Once a transaction has been successfully committed, it will remain so, even in the event of power loss, crashes, or errors.
Hint: Remember what each letter stands for. Atomicity = all or nothing. Consistency = valid state. Isolation = transactions don't interfere with each other. Durability = committed data is saved forever.
Follow-up: "How does a database typically implement Isolation? (e.g., locking)"
Difficult
Question: Explain the different transaction isolation levels in SQL.
Answer: Isolation levels define the degree to which a transaction must be isolated from data modifications made by other concurrent transactions. The standard levels are:
Read Uncommitted: The lowest level. A transaction can read data that has been modified by another transaction but not yet committed. This can lead to "dirty reads."
Read Committed: A transaction can only read data that has been committed. This prevents dirty reads, but can still lead to "non-repeatable reads" (data is changed by another transaction between two reads within the same transaction).
Repeatable Read: Guarantees that if a transaction reads a row multiple times, the result of those reads will be the same. It prevents dirty reads and non-repeatable reads, but "phantom reads" can still occur (new rows are inserted by another transaction).
Serializable: The highest level. It guarantees that transactions are executed serially, completely isolating them from one another. This prevents dirty, non-repeatable, and phantom reads, but it comes at a cost of reduced concurrency.
Hint: Think of the problems each level solves: Read Committed solves Dirty Reads. Repeatable Read solves Non-Repeatable Reads. Serializable solves Phantom Reads.
Follow-up: "What is optimistic vs. pessimistic locking?"
Question: What is database sharding? How does it differ from partitioning?
Answer:
Sharding: This is a type of horizontal partitioning that spreads data across multiple independent databases or servers. Each server (shard) holds a subset of the data. It's a "shared-nothing" architecture. Sharding is used to scale out a database horizontally to handle massive amounts of data and traffic. The application logic is usually aware of the sharding strategy.
Partitioning: This is a more general term for splitting a large table into smaller, more manageable pieces (partitions), but these partitions usually reside on the same database server. The database itself manages the partitions, and it's transparent to the application. Partitioning is typically done to improve query performance and manageability on a single large database.
Hint: The key difference is the scope. Partitioning happens within a single database instance. Sharding happens across multiple database instances/servers. Sharding is for scaling out, partitioning is for performance on a single node.
Follow-up: "What are some common sharding strategies (e.g., range-based, hash-based)?"
Question: What is the N+1 query problem and how can you solve it?
Answer: The N+1 query problem occurs when an application makes one initial query to retrieve a list of items (the "1" query), and then makes N subsequent queries to fetch related data for each of those N items. This is highly inefficient due to the overhead of making many separate database calls.
For example, fetching 10 blog posts, and then looping through them to fetch the author for each post would result in 1 (for posts) + 10 (for authors) = 11 queries.
Solution: The problem can be solved by "eager loading." Instead of fetching related data lazily, you fetch it all at once.
Using JOIN: Perform a JOIN in the initial query to retrieve both the posts and their authors in a single database call.
Using IN clause: Fetch all the posts first. Then, collect all the author_ids from the posts and fetch all the corresponding authors in a single second query using an IN clause (e.g., SELECT * FROM authors WHERE id IN (1, 2, 5, ...)).
Hint: It's a common performance bottleneck in applications that use ORMs (Object-Relational Mapping).
Follow-up: "When might using a JOIN be less performant than using an IN clause?"
