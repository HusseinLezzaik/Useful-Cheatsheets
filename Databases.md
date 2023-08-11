## Popular Databases
- MySQL
- PostgreSQL
- MongoDB
- Oracle
- SQLite
- Sybase
- Drizzle
- Firebird

## Relational Database Management Systems:
- Microsoft SQL Server
- MySQL
- SQLIte
- PostgresSql

## Principles of DB Design
### 1. Normalization
- Normalization is a process of organizing data within a database to reduce redundancy and improve integrity. It involves dividing tables into related parts and ensuring that relationships are logical.
- Example: Instead of having a single table with customer details and their orders, you might separate this into two tables: Customers and Orders. This helps in eliminating duplicate data.

### 2. ACID (Atomicity, Consistency, Isolation, Durability)
- These are the properties that guarantee reliable processing in a database.

1. **Atomicity:** Ensures that all operations within a transaction are completed successfully or none at all. If one part fails, the entire transaction fails, and the database is left unchanged.
2. **Consistency:** Ensures that a transaction brings a database from one valid state to another, maintaining all defined rules, constraints, and integrity.
3. **Isolation:** Ensures that concurrent execution of transactions leaves the database in the same state as if the transactions were executed sequentially.
4. **Durability:** Ensures that once a transaction has been committed, it will remain committed even in the case of a system failure.

### 3. Proper Indexing
- Indexing is a structure that improves the speed of data retrieval operations on a database table. By creating indexes on specific columns, the database can quickly locate the data without scanning the entire table.
- Example: Indexing the 'customer_id' field in an 'Orders' table enables the database to quickly find all orders associated with a particular customer.

## Databases Types, Design Principles, Languages, Servers, Projects
**1. Relational Databases (SQL):**
**- Design Principles:** Store data in tables with predefined schemas, emphasize relationships between data.
**- Languages:** SQL (Structured Query Language).
**- Servers:** MySQL, PostgreSQL, Microsoft SQL Server, Oracle.
**- Project Examples:**
  - **E-Commerce Platforms:** Manage products, orders, customers.
  - **Inventory Systems:** Track items, quantities, suppliers.

**2. NoSQL Databases:**
- **Design Principles:** Schema-less design, flexible and scalable.
- **Types:**
  - **Document-Based (e.g., MongoDB)**:
    - **Design**: Store data in JSON-like documents.
    - **Project Examples**:
      - **Blogs**: Handle posts, comments, categories.
      - **Real-Time Analytics**: Process and store large volumes of data.
  - **Key-Value Stores (e.g., Redis):**
    - D**esign:** Simple key-value pairs, fast access.
    - **Project Examples:**
      - **Caching:** Improve performance of web applications.
      - **Session Management:** Store user session information.
  - **Column-Family Stores (e.g., Cassandra):**
    - **Design:** Organize data by columns, suitable for write-heavy applications.
    - **Project Examples:**
      - **Time-Series Data:** Analyze metrics over time.
      - **Event Logging:** Handle large-scale event logs.
  - **Graph-Based (e.g., Neo4j):**
    - **Design:** Emphasize relationships between entities, connected data.
    -** Project Examples:**
      - **Social Networks:** Map relationships between users.
      - **Recommendation Systems:** Analyze interconnected data for suggestions.

**3. In-Memory Databases (e.g., Redis):**
- **Design Principles:** Store data in RAM, extremely fast access.
- **Project Examples:**
  - **Real-Time Analytics:** Process data with low latency.
  - **Caching:** Store frequently accessed data for quick retrieval.

**4. Object-Oriented Databases:**
- **Design Principles:** Store data as objects, aligned with object-oriented programming.
- **Servers:** db4o, ObjectDB.
- **Project Examples:**
  - **Complex Systems:** Manage data with intricate relationships and structures.
  - **CAD Systems: **Handle complex design data.

**5. NewSQL Databases (e.g., Google Spanner):**
- **Design Principles:** Combine benefits of traditional SQL with NoSQL scalability.
- **Project Examples:**
  - **Distributed Systems:** Handle transactions across globally distributed data.
  - **Large-Scale Applications:** Manage extensive datasets with SQL-like querying.


## CRUD vs. ACID
**1) CRUD:**
- CRUD stands for the four basic operations that you can perform on data in a database:
1. **Create**: Add new records.
2. **Read:** Retrieve existing records.
3. **Update:** Modify existing records.
4. **Delete:** Remove records.
- These operations form the core of most applications interacting with a database, whether it's a traditional SQL database or a NoSQL database.

**2) ACID:**
- ACID refers to a set of properties that ensure reliable processing in a database system, particularly important in transaction processing. ACID stands for:
1. **Atomicity:** Ensures that all operations within a transaction are completed successfully or none at all. If any part of the transaction fails, the whole transaction is rolled back to its initial state.
2. **Consistency:** Ensures that the database remains in a consistent state before and after the transaction. The transaction brings the database from one valid state to another.
3. **Isolation:** Ensures that concurrent execution of transactions leaves the database in the same state as if the transactions were executed sequentially.
4. **Durability:** Ensures that once a transaction has been committed, it will remain so, even in the event of system failure. This usually means that completed transactions are saved to non-volatile storage.

**3) Relationship Between CRUD and ACID:**
- **CRUD** is about the basic actions you can perform on data.
- **ACID** is about ensuring that these actions are performed reliably, especially when dealing with transactions (a series of operations that are treated as a single unit).
- While **CRUD** is a concept that can apply to almost any data manipulation, **ACID** properties are specifically tied to `relational databases` and `some NewSQL databases` where transactions are a key feature.
- ACID ensures that transactions in a database are processed reliably, which is crucial for applications like banking systems, e-commerce platforms, and other scenarios where data integrity is paramount.
