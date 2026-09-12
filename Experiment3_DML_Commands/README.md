# Experiment 3: DML Commands

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
--
-- How many patients have expired insurance coverage for each insurance company?

Sample table:Insurance Table

```sql
select InsuranceCompany,COUNT(InsuranceID) AS TotalExpiredPatients FROM Insurance GROUP BY(InsuranceCompany); 
```

**Output:**


<img width="871" height="827" alt="image" src="https://github.com/user-attachments/assets/c090ad17-4c35-48c9-94e4-1b95f83a5fa0" />


**Question 2**
---
-- What is the most common diagnosis among patients?

Sample table:MedicalRecords Table

```sql
SELECT Diagnosis,COUNT(*) AS DiagnosisCount FROM MedicalRecords GROUP BY Diagnosis ORDER BY DiagnosisCount DESC limit 1;
```

**Output:**


<img width="968" height="398" alt="image" src="https://github.com/user-attachments/assets/b0e18dfa-9ccd-4068-b634-a415a800d319" />


**Question 3**
---
-- How many appointments are scheduled for each doctor?

Sample table:Appointments Table

```sql
SELECT DoctorID,COUNT(AppointmentID) AS TotalAppointments FROM Appointments GROUP BY DoctorID;
```

**Output:**


<img width="715" height="697" alt="image" src="https://github.com/user-attachments/assets/ebff8164-6261-467e-95be-20a66986cffb" />


**Question 4**
---
-- ## Count Customers Who Received a Grade

**Question:**  
Write a SQL query to determine the number of customers who received at least one grade for their activity.

### Sample Table: `customer`

| customer_id | cust_name | city | grade | salesman_id |
|---|---|---|---:|---:|
| 3002 | Nick Rimando | New York | 100 | 5001 |
| 3007 | Brad Davis | New York | 200 | 5001 |
| 3005 | Graham Zusi | California | 200 | 5002 |

### SQL Query



```sql
select count(*) as COUNT from customer where grade>=1;
```

**Output:**


<img width="392" height="407" alt="image" src="https://github.com/user-attachments/assets/ada1f357-3cec-4f60-b333-82476ef5cf3d" />


**Question 5**
---
-- Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.

Sample table: customer

```sql
-- SELECT COUNT(*) AS COUNT FROM customer WHERE city='Noida';
```

**Output:**



<img width="372" height="405" alt="image" src="https://github.com/user-attachments/assets/b6c90cf1-7e31-4adf-af6c-39507931f2b6" />

**Question 6**
---
--## Total Amount of Fruits with Unit Type 'LB'

**Question:**  
Write a SQL query to find the total amount of fruits with a unit type of `'LB'`.

**Note:** Inventory attribute contains the amount of fruits.

### Table: `fruits`

| id | name | unit | inventory | price |
|---:|---|---|---:|---:|
| 1 | Apple | LB | 50 | 2.5 |
| 2 | Banana | KG | 30 | 1.5 |
| 3 | Orange | LB | 40 | 2.0 |


```sql
select SUM(inventory) as total from fruits where unit='LB';
```

**Output:**


<img width="417" height="392" alt="image" src="https://github.com/user-attachments/assets/731c74b0-7f38-4ffd-9674-cfab822a2b6c" />


**Question 7**
---
-- Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

Sample table: customer

```sql
SELECT COUNT(*) as COUNT from customer where city<> 'Noida';
```

**Output:**


<img width="398" height="420" alt="image" src="https://github.com/user-attachments/assets/5e7b0fca-3c50-4ecd-84b7-4239dd291d79" />


**Question 8**
---
-- Write an SQL query that groups the customer data into 5-year age intervals, calculates the minimum salary for each group, and excludes groups where the minimum salary is not less than 2000.

Table: customer1

```sql
-- SELECT (age/5)*5  age_group,MIN(salary) FROM customer1 group by age_group HAVING MIN(salary)<2000;
```

**Output:**


<img width="610" height="441" alt="image" src="https://github.com/user-attachments/assets/76f91820-775f-4a1c-a033-2d1e0ada6994" />


**Question 9**
---
-- Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.

Sample table: customer1



```sql
-- SELECT (age/5)*5 as  age_group,AVG(age) FROM customer1 group by age_group HAVING AVG(age)<24;
```

**Output:**


<img width="667" height="403" alt="image" src="https://github.com/user-attachments/assets/73e4204f-17f7-4b28-9638-1fddc014b349" />


**Question 10**
---
-- Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.

Sample table: customer1

```sql
-- SELECT (age/5)*5  age_group,SUM(salary) FROM customer1 group by age_group HAVING SUM(salary)>5000;
```

**Output:**


<img width="672" height="447" alt="image" src="https://github.com/user-attachments/assets/a0705918-3e5e-4b11-8390-8585f3e13071" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
