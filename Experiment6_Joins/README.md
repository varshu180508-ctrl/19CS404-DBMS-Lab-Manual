# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
--Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "doctor_id" column and conditions filtering for patients whose doctor has the first name 'Emily', last name 'Johnson', and a non-null discharge date.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id



DOCTORS TABLE:

ATTRIBUTES - doctor_id, first_name, last_name, specialization

```sql
-- SELECT patients.first_name AS patient_name
FROM patients
INNER JOIN doctors ON patients.doctor_id = doctors.doctor_id
WHERE doctors.first_name = 'Emily'
  AND doctors.last_name = 'Johnson'
  AND patients.discharge_date IS NOT NULL;
```

**Output:**

<img width="467" height="483" alt="image" src="https://github.com/user-attachments/assets/d8516712-9acf-472d-9510-67ded8390de3" />

**Question 2**
---
-- Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n") and the "department_name" column from the "departments" table, with an inner join on the "department_id" column.

NURSES TABLE:

ATTRIBUTES - nurse_id, first_name, last_name, department_id



DEPARTMENTS TABLE:

ATTRIBUTES - department_id, department_name
```sql
--SELECT n.*, d.department_name
FROM nurses n
INNER JOIN departments d ON n.department_id = d.department_id;
```

**Output:**

<img width="1233" height="647" alt="image" src="https://github.com/user-attachments/assets/4238a10b-81f4-4843-a341-15b9fbbcaf1a" />


**Question 3**
---
-- From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 



```sql
-- SELECT 
    a.ord_no, 
    a.ord_date, 
    a.purch_amt, 
    b.cust_name AS "Customer Name", 
    b.grade, 
    c.name AS "Salesman", 
    c.commission 
FROM orders a 
INNER JOIN customer b ON a.customer_id = b.customer_id 
INNER JOIN salesman c ON a.salesman_id = c.salesman_id;
```

**Output:**
<img width="1082" height="801" alt="image" src="https://github.com/user-attachments/assets/073e6b4e-e3fd-44bb-9f08-c243b552602d" />


**Question 4**
---
-- Write the SQL query that achieves the selection of all columns from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers with the name 'Fabian Johns'.

Customer Table: (customer_id, cust_name, city, grade, salesman_id)

Salesman Table: (salesman_id, name, city, commission)

```sql
-- SELECT s.*
FROM salesman s
LEFT JOIN customer c ON s.salesman_id = c.salesman_id
WHERE c.cust_name = 'Fabian Johns';
```

**Output:**

<img width="1256" height="488" alt="image" src="https://github.com/user-attachments/assets/61adec3a-af27-4043-a88e-ee36a6985669" />


**Question 5**
---
--write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

Sample table: salesman

 

```sql
-- SELECT 
    s.name AS Salesman, 
    c.cust_name, 
    s.city 
FROM salesman s 
INNER JOIN customer c ON s.city = c.city;
```

**Output:**

<img width="1042" height="770" alt="image" src="https://github.com/user-attachments/assets/b3654d45-219d-4ced-a226-eff78aac2691" />


**Question 6**
---
-- From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  



```sql
-- SELECT 
    a.cust_name AS "Customer Name", 
    a.city, 
    b.name AS "Salesman", 
    b.commission 
FROM customer a 
INNER JOIN salesman b ON a.salesman_id = b.salesman_id 
WHERE b.commission > 0.12;
```

**Output:**

<img width="1262" height="846" alt="image" src="https://github.com/user-attachments/assets/ba3e4d44-21c1-460d-824f-d1ae4eef95c4" />


**Question 7**
---
-- From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

Sample table: customer

 

```sql
-- SELECT 
    customer.cust_name, 
    customer.city, 
    customer.grade, 
    salesman.name AS Salesman, 
    salesman.city AS city
FROM customer 
LEFT JOIN salesman ON customer.salesman_id = salesman.salesman_id
WHERE customer.grade < 300
ORDER BY customer.customer_id ASC;
```

**Output:**

<img width="800" height="818" alt="image" src="https://github.com/user-attachments/assets/f48f2255-1e72-443a-9238-bd9a3b52fd0b" />

**Question 8**
---
-- Paste Question 8 here

```sql
-- From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
```

**Output:**

<img width="1326" height="586" alt="image" src="https://github.com/user-attachments/assets/20bdcbb8-6a28-4d81-b14f-6e873324be38" />

**Question 9**
---
-- Write the SQL query that achieves the selection of the "cust_name" and "city" columns from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for customers in the city 'London'.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)

 

```sql
-- SELECT 
    c.cust_name, 
    c.city, 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt 
FROM customer c 
LEFT JOIN orders o ON c.customer_id = o.customer_id 
WHERE c.city = 'London';
```

**Output:**

<img width="1276" height="568" alt="image" src="https://github.com/user-attachments/assets/47a52738-0e61-4daf-b199-b5dce65ce665" />

**Question 10**
---
-- Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id



TEST_RESULT TABLES:

ATTRIBUTES - result_id, patient_id, test_name, result, test_date

```sql
-- SELECT patients.first_name AS patient_name, t.*
FROM patients
INNER JOIN test_results t ON patients.patient_id = t.patient_id
WHERE t.test_name = 'Blood Pressure';
```

**Output:**

![Uploading image.png…]()



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
