Experiment 3: DML Commands
AIM
To study and implement DML (Data Manipulation Language) commands.

THEORY
1. INSERT INTO
Used to add records into a relation. These are three type of INSERT INTO queries which are as A)Inserting a single record Syntax (Single Row):

INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
Syntax (Multiple Rows):

INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
Syntax (Insert from another table):

INSERT INTO table_name SELECT * FROM other_table WHERE condition;
2. UPDATE
Used to modify records in a relation. Syntax:

UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
3. DELETE
Used to delete records from a relation. Syntax (All rows):

DELETE FROM table_name;
Syntax (Specific condition):

DELETE FROM table_name WHERE condition;
4. SELECT
Used to retrieve records from a table. Syntax:

SELECT column1, column2 FROM table_name WHERE condition;
Question 1
-- How many patients have expired insurance coverage for each insurance company?

Sample table:Insurance Table

select InsuranceCompany,COUNT(InsuranceID) AS TotalExpiredPatients FROM Insurance GROUP BY(InsuranceCompany); 
Output:

image
Question 2
-- What is the most common diagnosis among patients?

Sample table:MedicalRecords Table

SELECT Diagnosis,COUNT(*) AS DiagnosisCount FROM MedicalRecords GROUP BY Diagnosis ORDER BY DiagnosisCount DESC limit 1;
Output:

image
Question 3
-- How many appointments are scheduled for each doctor?

Sample table:Appointments Table

SELECT DoctorID,COUNT(AppointmentID) AS TotalAppointments FROM Appointments GROUP BY DoctorID;
Output:

image
Question 4
-- ## Count Customers Who Received a Grade

Question:
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample Table: customer
customer_id	cust_name	city	grade	salesman_id
3002	Nick Rimando	New York	100	5001
3007	Brad Davis	New York	200	5001
3005	Graham Zusi	California	200	5002
SQL Query
select count(*) as COUNT from customer where grade>=1;
Output:

image
Question 5
-- Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.

Sample table: customer

-- SELECT COUNT(*) AS COUNT FROM customer WHERE city='Noida';
Output:

image
Question 6
--## Total Amount of Fruits with Unit Type 'LB'

Question:
Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

Note: Inventory attribute contains the amount of fruits.

Table: fruits
id	name	unit	inventory	price
1	Apple	LB	50	2.5
2	Banana	KG	30	1.5
3	Orange	LB	40	2.0
select SUM(inventory) as total from fruits where unit='LB';
Output:

image
Question 7
-- Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

Sample table: customer

SELECT COUNT(*) as COUNT from customer where city<> 'Noida';
Output:

image
Question 8
-- Write an SQL query that groups the customer data into 5-year age intervals, calculates the minimum salary for each group, and excludes groups where the minimum salary is not less than 2000.

Table: customer1

-- SELECT (age/5)*5  age_group,MIN(salary) FROM customer1 group by age_group HAVING MIN(salary)<2000;
Output:

image
Question 9
-- Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.

Sample table: customer1

-- SELECT (age/5)*5 as  age_group,AVG(age) FROM customer1 group by age_group HAVING AVG(age)<24;
Output:

image
Question 10
-- Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.

Sample table: customer1

-- SELECT (age/5)*5  age_group,SUM(salary) FROM customer1 group by age_group HAVING SUM(salary)>5000;
Output:

image
RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
