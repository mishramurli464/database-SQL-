 
SQL (Structured Query Language) is a comprehensive language used for managing and manipulating relational databases. It encompasses a wide range of capabilities and features.  
Some of the key subsets and areas of SQL include:  

# Data Query Language (DQL): 
This subset of SQL is used for querying and retrieving data from a database. It primarily includes the SELECT statement to retrieve data from one or more tables.  

# Data Definition Language (DDL):  
DDL is used for defining the structure and schema of a database. It includes statements like CREATE TABLE, ALTER TABLE, DROP TABLE, and others for creating, modifying, and deleting database objects.  
## 1)CREATE TABLE:  
The CREATE TABLE statement is used to create a new table in the database.
Example:  
```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Department VARCHAR(50)
);
```
In this example, a table named "Employees" is created with columns for employee ID, first name, last name, and department.  

## 2)ALTER TABLE:
The ALTER TABLE statement is used to modify an existing table, such as adding, modifying, or dropping columns.
Example:
```sql
ALTER TABLE Employees
ADD Email VARCHAR(100);
```
This SQL statement adds an "Email" column to the "Employees" table.  

## 3)DROP TABLE:
The DROP TABLE statement is used to delete an entire table and all its data.
Example:  
```sql
DROP TABLE Employees;
```
This command would remove the "Employees" table from the database, including all its data.  

## 4)CREATE INDEX:
The CREATE INDEX statement is used to create an index on one or more columns of a table to improve query performance.
Example:  
```sql
CREATE INDEX idx_LastName ON Employees(LastName);
```
This command creates an index on the "LastName" column of the "Employees" table.  

## 5)DROP INDEX:
The DROP INDEX statement is used to remove an existing index from a table.
Example:  
```sql
DROP INDEX idx_LastName;
```
This command would remove the "idx_LastName" index from the "Employees" table.  

## 6)TRUNCATE TABLE:
The TRUNCATE TABLE statement is used to remove all rows from a table while keeping the table structure intact.
Example:  
```sql
TRUNCATE TABLE Employees;
```
This command would delete all rows from the "Employees" table, leaving an empty table.  

# Data Manipulation Language (DML): 
DML is used for modifying and manipulating data within the database. It includes statements like INSERT, UPDATE, and DELETE for adding, modifying, and removing records.  

## 1)INSERT:
The INSERT statement is used to add new rows (records) to a table.
Example:
```sql
INSERT INTO Employees (FirstName, LastName, Department)
VALUES ('John', 'Doe', 'HR');
```  
This SQL command adds a new employee to the "Employees" table with the specified first name, last name, and department.

## 2)UPDATE:
The UPDATE statement is used to modify existing data in a table.
Example:
```sql
UPDATE Employees
SET Department = 'Finance'
WHERE LastName = 'Doe';
```
This command updates the "Department" for the employee with the last name "Doe" to 'Finance'.

## 3)DELETE:
The DELETE statement is used to remove rows from a table.  
Example:
```sql
DELETE FROM Employees
WHERE EmployeeID = 101;
```  
This command deletes the employee with an "EmployeeID" of 101 from the "Employees" table.

# Data Control Language (DCL):  
DCL is used for controlling access to data. It includes statements like GRANT and REVOKE to manage permissions and access rights.  

## 1)GRANT:  
Example:  
```sql
GRANT SELECT, INSERT ON Employees TO HR_Manager;
```  
This command grants the SELECT and INSERT privileges on the "Employees" table to the "HR_Manager" user or role. After this command, the "HR_Manager" will be able to query and insert data into the "Employees" table.

## 2)REVOKE:
Example:
```sql
REVOKE INSERT ON Employees FROM Temporary_Employee;
```  
This command revokes the INSERT privilege on the "Employees" table from the "Temporary_Employee" user or role. After this command, the "Temporary_Employee" will no longer be able to insert data into the "Employees" table.

# Transaction Control Language (TCL):  
TCL is used for managing transactions in a database. It includes commands like COMMIT, ROLLBACK, and SAVEPOINT to control transaction behavior.  

## 1)COMMIT:
Example:
```sql
BEGIN TRANSACTION;
-- SQL statements within the transaction
COMMIT;
```  
In this example, the COMMIT statement is used to save the changes made within a transaction to the database. The changes are now permanent.

## 2)ROLLBACK:
Example:
```sql
BEGIN TRANSACTION;

-- SQL statements within the transaction

ROLLBACK;
```  
In this example, the ROLLBACK statement is used to cancel the changes made within a transaction, and the database returns to its state prior to the transaction.  

## 3)SAVEPOINT:
Example:
```sql
BEGIN TRANSACTION;

-- SQL statements within the transaction

SAVEPOINT point1;

-- More SQL statements

ROLLBACK TO point1;
```  
In this example, the SAVEPOINT statement is used to create an intermediate point called "point1" within the transaction. Later, you can use ROLLBACK TO point1 to revert the transaction to that specific point.

# Data Integrity Constraints:  
SQL supports the definition of constraints, such as PRIMARY KEY, FOREIGN KEY, CHECK, and UNIQUE, to ensure data integrity and enforce rules on data. 
## 1)Primary Key Constraint:
Example:
```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50)
);
```  
In this example, the "StudentID" column is designated as the primary key, ensuring that each student record is uniquely identified by their student ID.

## 2)Foreign Key Constraint:
Example:
```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    OrderDate DATE,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```  
Here, the "CustomerID" column in the "Orders" table is a foreign key that references the "CustomerID" column in the "Customers" table, ensuring that orders are associated with valid customers.

## 3)Unique Constraint:
Example:
```sql
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(50) UNIQUE,
    Price DECIMAL(10, 2)
);
```  
In this example, the "ProductName" column must have unique values, but it can contain null values.

## 4)Check Constraint:
Example:
```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    BirthDate DATE,
    HireDate DATE,
    CONSTRAINT CHK_HireDate CHECK (HireDate >= BirthDate)
);
```  
The "CHK_HireDate" constraint ensures that the "HireDate" is not earlier than the "BirthDate."  

## 5)Not Null Constraint:
Example:
```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    FirstName VARCHAR(50) NOT NULL,
    LastName VARCHAR(50) NOT NULL
);
```  
This constraint ensures that both "FirstName" and "LastName" must have values for every customer.

# Aggregation and Grouping:  
SQL provides functions like SUM, AVG, COUNT, and GROUP BY for performing aggregate calculations and grouping data.  

1) Aggregate Functions:   
COUNT(): Counts the number of records in a table.

```sql
SELECT COUNT(*) FROM Employees;
```  
SUM(): Calculates the total salary of employees.

```sql
SELECT SUM(Salary) FROM Employees;
```  
AVG(): Calculates the average age of customers.
```sql
SELECT AVG(Age) FROM Customers;
```
MAX(): Retrieves the highest sale amount.  
```sql
SELECT MAX(SaleAmount) FROM Sales;
```
MIN(): Retrieves the lowest temperature recorded.
```sql
SELECT MIN(Temperature) FROM WeatherData;
```
2) String Functions:

CONCAT(): Combines first name and last name.  
```sql
SELECT CONCAT(FirstName, ' ', LastName) AS FullName FROM Employees;
```  
SUBSTRING(): Extracts the first 3 characters of a string.
```sql
SELECT SUBSTRING(ProductName, 1, 3) AS ShortName FROM Products;
```
UPPER(): Converts a string to uppercase.
```sql
SELECT UPPER(City) FROM Customers;
```  
LOWER(): Converts a string to lowercase.
```sql
SELECT LOWER(Description) FROM Products;
```
LENGTH(): Calculates the length of a string.
```sql
SELECT LENGTH(Comments) FROM Reviews;
```
3) Date and Time Functions:

CURRENT_DATE: Retrieves the current date.
```sql
SELECT CURRENT_DATE AS Today;
```

CURRENT_TIME: Retrieves the current time.
```sql
SELECT CURRENT_TIME AS CurrentTime;
```
CURRENT_TIMESTAMP: Retrieves the current date and time.
```sql
SELECT CURRENT_TIMESTAMP AS CurrentDateTime;
```
DATEADD(): Adds 7 days to a given date.  
```sql
SELECT DATEADD(DAY, 7, OrderDate) AS NewDeliveryDate FROM Orders;
```
DATEDIFF(): Calculates the number of days between two dates.  
```sql
SELECT DATEDIFF(DAY, OrderDate, ShipmentDate) AS DaysToShip FROM Orders;
```
4)Mathematical Functions:

ROUND(): Rounds a number to 2 decimal places.
```sql
SELECT ROUND(Price, 2) FROM Products;
```
ABS(): Returns the absolute value of a number.
```sql
SELECT ABS(Discount) FROM Sales;
```
POWER(): Calculates the square of a number.
```sql
SELECT POWER(2, 3) AS Result;
```
SQRT(): Calculates the square root of a number.
```sql
SELECT SQRT(25) AS SquareRoot;
```
RAND(): Generates a random number between 1 and 100.
```sql
SELECT RAND() * 100 AS RandomNumber;
```
# Joins:  
SQL allows you to combine data from multiple tables using different types of joins, such as INNER JOIN, LEFT JOIN, and RIGHT JOIN.

# Subqueries:  
SQL supports subqueries, which are queries embedded within other queries, to retrieve or filter data based on the results of another query.

# Views:  
You can create virtual tables known as views using SQL. Views are useful for simplifying complex queries and controlling access to sensitive data.

# Stored Procedures and Functions:  
SQL supports the creation of stored procedures and functions, allowing you to encapsulate sequences of SQL statements for reuse and modularity.


