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

Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary
| EmployeeID | Name        | Department  | Salary |
|------------|-------------|-------------|--------|
| 201        | John Doe    | HR          | 50000  |
| 202        | Jane Smith  | Engineering | 75000  |
| 203        | Emily Davis | Marketing   | 60000  |

```sql
INSERT INTO Employee SELECT * FROM Former_employees;


```

**Output:**

<img width="1232" height="427" alt="image" src="https://github.com/user-attachments/assets/c46b4623-5fe4-4364-91ce-5af0deba63f8" />


**Question 2**
 Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300
For example:
Table attributes are Name, Category, Price, Stock

| Name | Category | Price | Stock |
|------|----------|------:|------:|
| Smartphone | Electronics | 800 | 150 |
| Headphones | Accessories | 200 | 300 |



```sql
INSERT INTO Products (Name,Category,Price,Stock) VALUES('Smartphone','Electronics',800,150);
INSERT INTO Products (Name,Category,Price,Stock) VALUES('Headphones','Accessories',200,300);
```

**Output:**

<img width="1228" height="456" alt="image" src="https://github.com/user-attachments/assets/9c513be2-3ea3-437e-898a-0db07ca491cd" />


**Question 3**
Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer
Table attributes are customer_id, cust_name, city, grade, salesman_id, birth_date

| customer_id | cust_name | city | grade | salesman_id | birth_date |
|-------------|-----------|------|-------|-------------|------------|
| 101 | John | Chennai | 100 | 5001 | 1995-06-15 |
| 102 | Priya | Bangalore | 200 | 5002 | 1998-02-20 |
| 103 | Rahul | Hyderabad | 300 | 5003 | 1996-09-10 |
 
 


```sql
ALTER TABLE customer
ADD birth_date timestamp;
```

**Output:**

<img width="1206" height="455" alt="image" src="https://github.com/user-attachments/assets/5a7dfc56-a880-43a3-91c2-11004ca18233" />


**Question 4**

create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.
For example:

Table attributes are job_id, job_title, min_salary, max_salary

| job_id | job_title | min_salary | max_salary |
|--------|-----------|-----------:|-----------:|
| 1 | Software Engineer | 9000 | 15000 |
```sql
CREATE TABLE jobs(
job_id INT PRIMARY KEY,
job_title VARCHAR(50) DEFAULT ' ',
min_salary INT DEFAULT 8000,
max_salary INT DEFAULT NULL
);


```

**Output:**

<img width="1230" height="420" alt="image" src="https://github.com/user-attachments/assets/89e4dec8-30c5-4ac6-a8a2-538c3ea32adf" />


**Question 5**

Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.
For example:


```sql
CREATE TABLE ProjectAssignments(
AssignmentID INTEGER PRIMARY KEY,
EmployeeID INTEGER REFERENCES EmployeeS(EmployeeID),
ProjectID INTEGER REFERENCES Projects(ProjectID),
AssignmentDate DATE NOT NULL
);
```

**Output:**

<img width="1212" height="365" alt="image" src="https://github.com/user-attachments/assets/fc90e22d-4955-4e6c-993f-d3a32685a438" />


**Question 6**

 Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

Table attributes are CustomerID, Name, Address

| CustomerID | Name | Address |
|------------|------|---------|
| 304 | Peter Parker | Spider St |
 



```sql
INSERT INTO Customers (CustomerID,Name,Address)
VALUES(304,'Peter Parker','Spider St');
```

**Output:**

<img width="1207" height="392" alt="image" src="https://github.com/user-attachments/assets/78ba53f1-5cf1-4110-9265-dfe713c09092" />


**Question 7**

Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.
For example:

Table attributes are item_id, item_desc, rate, icom_id

| item_id | item_desc | rate | icom_id |
|---------|-----------|-----:|---------|
| ITM5 | Charlie Gold | 700 | COM5 |
```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT CHECK (length(icom_id)=4),
FOREIGN  KEY (icom_id) REFERENCES company(com_id) ON UPDATE SET NULL ON DELETE SET NULL
);
```

**Output:**

<img width="1211" height="452" alt="image" src="https://github.com/user-attachments/assets/0dda1f36-c5d1-4676-929a-4d2cdbcf28a4" />


**Question 8**

Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.
For example:



```sql
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY ,
InvoiceDate DATE,
DueDate DATE CHECK (DueDate > InvoiceDate),
Amount REAL CHECK (Amount >0)
);
```

**Output:**

<img width="1232" height="362" alt="image" src="https://github.com/user-attachments/assets/5a37b896-e997-406d-aede-ab1f78989fc0" />


**Question 9**

Create a table named Reviews with the following columns:

ReviewID as INTEGER
ProductID as INTEGER
Rating as REAL
ReviewText as TEXT
For example:

Table attributes are ReviewID, ProductID, Rating, ReviewText

| ReviewID | ProductID | Rating | ReviewText |
|----------|-----------|-------:|------------|
| 1 | 101 | 4.5 | Excellent product |
| 2 | 102 | 3.8 | Good quality |
| 3 | 103 | 5.0 | Highly recommended |

```sql
CREATE TABLE Reviews(
ReviewID INTEGER,
ProductID INTEGER,
Rating REAL,
ReviewText TEXT 
);
```

**Output:**

<img width="1226" height="473" alt="image" src="https://github.com/user-attachments/assets/96619e59-139c-42b4-b999-8603a266eeb4" />


**Question 10**

 Write a SQL Query to add an attribute designation in the employee table with the data type VARCHAR(50).

For example:
Table attributes are id, salary, designation

| id | salary | designation |
|----|-------:|-------------|
| 101 | 50000 | Manager |
| 102 | 35000 | Developer |
| 103 | 25000 | Tester |


```sql
ALTER TABLE employee ADD designation varchar(50);
```

**Output:**

<img width="1205" height="372" alt="image" src="https://github.com/user-attachments/assets/db5332e1-8cbc-45de-be55-655b2125eb7d" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
