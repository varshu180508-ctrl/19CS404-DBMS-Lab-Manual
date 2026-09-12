# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
-- How many patients have expired insurance coverage for each insurance company?

Sample table:Insurance Table

```sql
select InsuranceCompany,COUNT(InsuranceID) AS TotalExpiredPatients FROM Insurance GROUP BY(InsuranceCompany); 
```

**Output:**

<img width="940" height="840" alt="image" src="https://github.com/user-attachments/assets/d0ce34ac-b574-4bc0-b1b7-a730cdec5ae9" />

**Question 2**
---
-- What is the most common diagnosis among patients?

Sample table:MedicalRecords Table

```sql
-- SELECT Diagnosis,COUNT(*) AS DiagnosisCount FROM MedicalRecords GROUP BY Diagnosis ORDER BY DiagnosisCount DESC limit 1;
```

**Output:**

<img width="872" height="372" alt="image" src="https://github.com/user-attachments/assets/8010cf0b-9ebf-4208-a09f-2998452f9a3c" />


**Question 3**
---
-- How many appointments are scheduled for each doctor?

Sample table:Appointments Table

```sql
-- SELECT DoctorID,COUNT(AppointmentID) AS TotalAppointments FROM Appointments GROUP BY DoctorID;
```

**Output:**

<img width="747" height="707" alt="image" src="https://github.com/user-attachments/assets/5a2e4414-e763-40cb-9b3b-fe5ba4c71e39" />


**Question 4**
---
-- Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002

```sql
-select count(*) as COUNT from customer where grade>=1;
```

**Output:**

<img width="417" height="408" alt="image" src="https://github.com/user-attachments/assets/f02a7ca2-3dfd-4a62-bd07-ce3125fbd6e2" />


**Question 5**
---
-- Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.

Sample table: customer

```sql
-- SELECT COUNT(*) AS COUNT FROM customer WHERE city='Noida';
```

**Output:**
<img width="385" height="388" alt="image" src="https://github.com/user-attachments/assets/b476dca7-549a-4d91-a73a-20b698707a70" />


**Question 6**
---
-- Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
 

```sql
-- select SUM(inventory) as total from fruits where unit='LB';
```

**Output:**


<img width="412" height="392" alt="image" src="https://github.com/user-attachments/assets/459aead7-10a0-4630-ae0c-beda2e4cc4bc" />

**Question 7**
---
-- Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

Sample table: customer


```sql
-- SELECT COUNT(*) as COUNT from customer where city<> 'Noida';
```

**Output:**

<img width="397" height="403" alt="image" src="https://github.com/user-attachments/assets/822733de-5e61-44a6-864a-ce1111ae27af" />


**Question 8**
---
-- Write an SQL query that groups the customer data into 5-year age intervals, calculates the minimum salary for each group, and excludes groups where the minimum salary is not less than 2000.

Table: customer1

```sql
-- SELECT (age/5)*5  age_group,MIN(salary) FROM customer1 group by age_group HAVING MIN(salary)<2000;
```

**Output:**

<img width="585" height="425" alt="image" src="https://github.com/user-attachments/assets/cd21de82-f808-464c-a710-43ac8eb385d2" />


**Question 9**
---
-- Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.

Sample table: customer1

```sql
-- SELECT (age/5)*5 as  age_group,AVG(age) FROM customer1 group by age_group HAVING AVG(age)<24;
```

**Output:**
<img width="587" height="390" alt="image" src="https://github.com/user-attachments/assets/2b1bb5ac-9fab-4434-8b56-38163e8fbd51" />


**Question 10**
---
-- Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.

Sample table: customer1

```sql
--SELECT (age/5)*5  age_group,SUM(salary) FROM customer1 group by age_group HAVING SUM(salary)>5000;
```

**Output:**

<img width="622" height="427" alt="image" src="https://github.com/user-attachments/assets/a5b9821b-a4aa-41fa-9eb1-135dad16d6e2" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
