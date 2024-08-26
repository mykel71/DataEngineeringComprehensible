
# SQL Overview

## What is SQL?

SQL (Structured Query Language) is a standard programming language used for managing and manipulating relational databases. It allows you to create, read, update, and delete data stored in relational databases.

## Key Features of SQL

- **Declarative Language:** SQL is a declarative language, meaning you specify what you want to do with the data, and the database management system (DBMS) figures out how to execute it.
- **Data Manipulation:** SQL provides commands for querying and modifying data in a database.
- **Data Definition:** SQL includes commands for defining the structure of the database, such as creating tables and indexes.
- **Data Control:** SQL offers commands to control access to data in the database.

## Common SQL Commands

### Data Querying

- **SELECT:** Retrieves data from one or more tables.
  
  \`\`\`sql
  SELECT column1, column2 FROM table_name WHERE condition;
  \`\`\`

- **WHERE:** Filters the result set based on specified conditions.

  \`\`\`sql
  SELECT * FROM Employees WHERE Age > 30;
  \`\`\`

- **JOIN:** Combines rows from two or more tables based on a related column.

  \`\`\`sql
  SELECT Employees.Name, Departments.Department
  FROM Employees
  JOIN Departments ON Employees.DepartmentID = Departments.ID;
  \`\`\`

- **GROUP BY:** Groups rows that have the same values in specified columns.

  \`\`\`sql
  SELECT Department, COUNT(*)
  FROM Employees
  GROUP BY Department;
  \`\`\`

- **ORDER BY:** Sorts the result set in ascending or descending order.

  \`\`\`sql
  SELECT * FROM Employees ORDER BY LastName ASC;
  \`\`\`

- **HAVING:** Filters groups in a \`GROUP BY\` clause.

  \`\`\`sql
  SELECT Department, COUNT(*)
  FROM Employees
  GROUP BY Department
  HAVING COUNT(*) > 5;
  \`\`\`

### Data Manipulation

- **INSERT:** Adds new rows to a table.
  
  \`\`\`sql
  INSERT INTO table_name (column1, column2) VALUES (value1, value2);
  \`\`\`

- **UPDATE:** Modifies existing rows in a table.

  \`\`\`sql
  UPDATE table_name SET column1 = value1 WHERE condition;
  \`\`\`

- **DELETE:** Removes rows from a table.

  \`\`\`sql
  DELETE FROM table_name WHERE condition;
  \`\`\`

### Data Definition

- **CREATE TABLE:** Defines a new table and its columns.
  
  \`\`\`sql
  CREATE TABLE Employees (
      ID INT PRIMARY KEY,
      Name VARCHAR(100),
      Age INT,
      DepartmentID INT
  );
  \`\`\`

- **ALTER TABLE:** Modifies the structure of an existing table.

  \`\`\`sql
  ALTER TABLE Employees ADD COLUMN Salary DECIMAL(10, 2);
  \`\`\`

- **DROP TABLE:** Deletes a table and all its data.

  \`\`\`sql
  DROP TABLE Employees;
  \`\`\`

### Data Control

- **GRANT:** Gives a user access to a database or table.

  \`\`\`sql
  GRANT SELECT, INSERT ON Employees TO 'username';
  \`\`\`

- **REVOKE:** Removes a user’s access to a database or table.

  \`\`\`sql
  REVOKE INSERT ON Employees FROM 'username';
  \`\`\`

## Advanced SQL Concepts

### Indexes

Indexes are special lookup tables that the database search engine can use to speed up data retrieval.

\`\`\`sql
CREATE INDEX idx_name ON Employees (LastName);
\`\`\`

### Views

A view is a virtual table based on the result set of an SQL query. It can simplify complex queries by encapsulating them.

\`\`\`sql
CREATE VIEW EmployeeView AS
SELECT Name, Department FROM Employees WHERE Age > 30;
\`\`\`

### Transactions

Transactions are a sequence of SQL statements that are executed as a single unit. If any part of the transaction fails, the entire transaction is rolled back.

\`\`\`sql
BEGIN TRANSACTION;
UPDATE Accounts SET Balance = Balance - 100 WHERE AccountID = 1;
UPDATE Accounts SET Balance = Balance + 100 WHERE AccountID = 2;
COMMIT;
\`\`\`

### Stored Procedures

Stored procedures are precompiled collections of SQL statements that can be executed on the database server.

\`\`\`sql
CREATE PROCEDURE UpdateEmployeeSalary
AS
BEGIN
    UPDATE Employees SET Salary = Salary * 1.1 WHERE DepartmentID = 1;
END;
\`\`\`

### Triggers

Triggers are SQL code that automatically executes in response to certain events on a particular table.

\`\`\`sql
CREATE TRIGGER trg_after_insert
AFTER INSERT ON Employees
FOR EACH ROW
BEGIN
    INSERT INTO AuditLog(EmployeeID, Action) VALUES(NEW.ID, 'Inserted');
END;
\`\`\`

## SQL Best Practices

- **Normalize Your Database:** Use normalization to reduce data redundancy and improve data integrity.
- **Use Indexes Wisely:** Indexes can improve query performance but can slow down write operations.
- **Avoid SELECT *:** Explicitly specify the columns you need to retrieve to reduce the amount of data transferred.
- **Use Transactions:** Ensure data integrity by using transactions for critical operations.
- **Optimize Joins:** Joins can be costly; make sure your queries are optimized for performance.

## Conclusion

SQL is a powerful language for managing and manipulating relational databases. Understanding the various commands and concepts of SQL is essential for anyone working with databases. Whether you're querying data, defining database structures, or managing user access, SQL provides the tools needed to interact effectively with your data.

---

**References**

- [SQL Tutorial - W3Schools](https://www.w3schools.com/sql/)
- [SQL: The Complete Reference by James R. Groff, Paul N. Weinberg](https://www.oreilly.com/library/view/sql-the-complete/9780071592550/)
- [Learning SQL by Alan Beaulieu](https://www.oreilly.com/library/view/learning-sql/9781449373092/)
