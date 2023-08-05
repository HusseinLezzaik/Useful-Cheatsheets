## Popular Databases
- MySQL
- PostgreSQL
- MongoDB

## Databases Types
- MySQL
- PostgreSQL
- Oracle
- Microsoft SQL Server
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
