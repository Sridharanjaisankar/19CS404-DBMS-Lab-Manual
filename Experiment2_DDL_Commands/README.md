# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.
```sql
CREATE TABLE Department(
    DepartmentID INTEGER PRIMARY KEY,
    DepartmentName TEXT UNIQUE NOT NULL,
    Location TEXT
    );
```
**Output**
![image](https://github.com/user-attachments/assets/10670564-566d-4503-902e-50e89ec08cb8)

**Question 2**
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.
```sql
CREATE TABLE Products(
    ProductID INTEGER PRIMARY KEY,
    ProductName CHAR(50) NOT NULL,
    Price REAL NOT NULL CHECK (Price > 0),
    Stock INTEGER CHECK (Stock >= 0)
    );
```
**Output**
![image](https://github.com/user-attachments/assets/7d11382b-389e-4007-87a9-d4d6696a9a7a)

**Question 3**
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
```sql
CREATE TABLE Invoices(
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate DATE,
    Amount REAL CHECK(Amount>0),
    DueDate DATE CHECK(DueDate>InvoiceDate),
    OrderID INTEGER,
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
    );
```
**Output**
![image](https://github.com/user-attachments/assets/cc5a8bf7-698b-4e34-8e31-9e8e9ac1865d)

**Question 4**
Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.
Sample table: customer
```sql
ALTER TABLE customer
ADD COLUMN discount DECIMAL(5,2);
```
**Output**
![image](https://github.com/user-attachments/assets/5361aefb-7652-420c-92d1-5593594a7dce)

**Question 5**
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
```sql
CREATE TABLE Shipments(
    ShipmentID INTEGER PRIMARY KEY,
    ShipmentDate DATE,
    SupplierID INTEGER,
    OrderID INTEGER,
    FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
    );
```
**Output**
![image](https://github.com/user-attachments/assets/ed87ec2d-d08e-48d0-8c4a-d5fa1e5f5628)

**Question 6**
Insert the following employees into the Employee table:
EmployeeID  Name        Position    Department  Salary
2           John Smith  Developer   IT          75000
3           Anna Bell   Designer    Marketing   68000
```sql
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
VALUES (2,'John Smith','Developer','IT',75000),
(3,'Anna Bell','Designer','Marketing',68000);
```
**Output**
![image](https://github.com/user-attachments/assets/cc1b5a0a-d52f-462a-a9e8-ad9cd694d095)

**Question 7**
Write a SQL Query  to Rename attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date,State as varchar(30) in the table Companies. 
```sql
ALTER TABLE Companies
RENAME COLUMN name to first_name;
ALTER TABLE Companies ADD COLUMN
mobilenumber number;
ALTER TABLE Companies ADD COLUMN
DOB Date;
ALTER TABLE Companies ADD COLUMN
State varchar(30);
```
**Output**
![image](https://github.com/user-attachments/assets/9242d771-5440-4d88-babb-07d9efaa1283)

**Question 8**
Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.
CustomerID  Name          Address
304         Peter Parker  Spider St      
Note: The City and ZipCode columns will use their default values.
```sql
INSERT INTO Customers(CustomerID,Name,Address)
VALUES (304,'Peter Parker','Spider St');
```
**Output**
![image](https://github.com/user-attachments/assets/e3247efc-3f1a-413b-9557-4d38c0f85e56)

**Question 9**
Insert all students from Archived_students table into the Student_details table.
cid         name        type        notnull     dflt_value  pk
0           RollNo      INT           0                       1
1           Name        VARCHAR(100)  0                       0
2           Gender      VARCHAR(10)   0                       0
3           Subject     VARCHAR(50)   0                       0
4           MARKS       INT           0                       0
```sql
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
SELECT RollNo,Name,Gender,Subject,Marks FROM Archived_students;
```
**Output**
![image](https://github.com/user-attachments/assets/1aa7cf32-3c55-48b5-910a-1d9f0417afab)

**Question 10**
Create a table named Departments with the following columns:
DepartmentID as INTEGER
DepartmentName as TEXT
```sql
CREATE TABLE Departments(
    DepartmentID INTEGER,
    DepartmentName TEXT
    );
```
**Output**
![image](https://github.com/user-attachments/assets/560bb5c5-1c84-4455-8456-b3b22fd09dde)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
