# Experiment 3: DML Commands
# Name: Sridharan J
# Register No: 21222204058

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
```
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```
```sql
UPDATE Employees
SET salary = salary * 2
WHERE department_id =20 AND job_id LIKE '%MAN';
```
**Output**
![image](https://github.com/user-attachments/assets/8106af6c-b2af-4d83-90c1-d1530d9208dd)

**Question 2**
```
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```
```sql
UPDATE employees
SET email = 'not available' ,commission_pct = 0.55
WHERE department_id = 110;
```
**Output**
![image](https://github.com/user-attachments/assets/70790773-3341-4f42-8ba5-45aeb83c7d9b)

**Question 3**
```
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```
```sql
UPDATE employees
SET first_name = 'John'
WHERE department_id = 80;
```
**Output**
![image](https://github.com/user-attachments/assets/1598ec9c-9c8f-4fc4-9725-39591033a4c5)

**Question 4**
```
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)
```
```sql
UPDATE suppliers
SET supplier_name = UPPER(supplier_name)
WHERE contact_person LIKE '%Singh%';
```
**Output**
![image](https://github.com/user-attachments/assets/8ca7067e-1e4b-4a54-b675-5e0b42b6cf4e)

**Question 5**
```
Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```
```sql
UPDATE Employees
SET hire_date = '2024-01-24'
WHERE department_id = 50;
```
**Output**
![image](https://github.com/user-attachments/assets/a9fd111f-d37b-408a-a39a-794f0dfa4521)

**Question 6**
```
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000
Sample table: Customer
```
```sql
DELETE FROM Customer
WHERE (grade = 3 OR agent_code = 'A008') AND outstanding_amt < 5000;
```
**Output**
![image](https://github.com/user-attachments/assets/395d67cb-f1e1-4e2c-a63b-5d16d17a0c5e)

**Question 7**
```
Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.
Sample table: Doctors
attributes : doctor_id, first_name, last_name, specialization
```
```sql
DELETE FROM Doctors
WHERE specialization = 'Pediatrics' AND first_name = 'Michael';
```
**Output**
![image](https://github.com/user-attachments/assets/5e48f852-998f-4d03-8e91-0ec0653b06aa)

**Question 8**
```
Write a SQL query to Delete a Specific Surgery whose ID is 3
```
```sql
DELETE FROM Surgeries
WHERE surgery_id = 3;
```
**Output**
![image](https://github.com/user-attachments/assets/6b024d3a-3514-4e33-ad48-397481f9a26c)

**Question 9**
```
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.
```
```sql
DELETE FROM Customer
WHERE cust_name LIKE '%Holmes%';
```
**Output**
![image](https://github.com/user-attachments/assets/c682f415-b84e-4f81-b4e9-a316d6303ab6)

**Question 10**
```
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.
```
```sql
DELETE FROM Customer
WHERE grade < 2;
```
**Output**
![image](https://github.com/user-attachments/assets/1b54d708-cfca-4acd-adec-9ba3d76b7e49)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
