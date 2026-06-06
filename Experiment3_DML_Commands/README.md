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
-- Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

products table

---------------

product_id

product_name

category_id

availability

```sql
-- 
UPDATE products
SET product_name='Grapefruit'
WHERE product_id=4;
```

**Output:**

<img width="1185" height="255" alt="image" src="https://github.com/user-attachments/assets/65b83084-5db1-4e83-96d8-aa6da323bec0" />

**Question 2**
---
-- 
Update the 'Selling_Price' to add 10% extra margin for all products supplied by the supplier with id 6.

PRODUCTS TABLE

name               type

-----------------  ---------------

product_id         INT

product_name       VARCHAR(100)

category           VARCHAR(50)

cost_price         DECIMAL(10,2)

sell_price         DECIMAL(10,2)

reorder_lvl        INT

quantity           INT

supplier_id        INT


```sql
--
UPDATE PRODUCTS
SET sell_price = ROUND(sell_price*1.10,2)
WHERE supplier_id=6;
```

**Output:**

<img width="1220" height="553" alt="image" src="https://github.com/user-attachments/assets/7e5c0a96-aee8-487f-9b01-6b02b0b50c2c" />


**Question 3**
---
-- 
Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```sql
--
DELETE FROM Customer
WHERE NOT(CUST_CITY = 'New York') AND OUTSTANDING_AMT >5000;
```

**Output:**

<img width="1237" height="612" alt="image" src="https://github.com/user-attachments/assets/db4aa95b-6b65-4cd7-8ee0-a366522fcf5a" />


**Question 4**
---
-- 
 Write a query to fetch 3 top salaried records from EmployeePosition table.

 <img width="453" height="205" alt="image" src="https://github.com/user-attachments/assets/543f2953-581f-4b93-a8db-de50694f60d4" />


```sql
--
SELECT EmpID,EmpPosition,DateOfJoining,Salary
FROM EmployeePosition
ORDER BY Salary DESC
LIMIT 3;
```

**Output:**

<img width="967" height="307" alt="image" src="https://github.com/user-attachments/assets/41f72ed5-8f70-4bbc-9638-fee2d38d659d" />


**Question 5**
---
-- 
 Write a query to fetch details of all employees excluding the employees with first names, “Sanjay” and “Sonia” from the EmployeeInfo table.

<img width="780" height="172" alt="image" src="https://github.com/user-attachments/assets/cfbe2cfd-be18-451e-bfeb-825a4731ef34" />

```sql
--
SELECT * FROM EmployeeInfo
WHERE EmpFname NOT IN('Sanjay','Sonia');
```

**Output:**

<img width="1238" height="331" alt="image" src="https://github.com/user-attachments/assets/ec324cdd-931e-43e9-a7ff-a9accd6a3d99" />


**Question 6**
---
-- 
<img width="1193" height="546" alt="image" src="https://github.com/user-attachments/assets/d51611dc-f042-46eb-a38d-8c463bbd713f" />


```sql
--
SELECT id,decimal,
CASE 
WHEN decimal>100 THEN 'High'
WHEN decimal BETWEEN 50 AND 100 THEN'Medium' ELSE 'Low'
END AS category
FROM Calculations;
```

**Output:**

<img width="791" height="493" alt="image" src="https://github.com/user-attachments/assets/745277ae-3214-49ed-b117-5d2db85d9e1f" />


**Question 7**
---
-- <img width="1253" height="453" alt="image" src="https://github.com/user-attachments/assets/2621ddff-c8e9-41e8-8bf7-9950f2ef8010" />


```sql
--
SELECT customer_id,cust_name,city,grade,salesman_id
FROM customer
WHERE city = 'New York' OR grade<=100;
```

**Output:**

<img width="1164" height="415" alt="image" src="https://github.com/user-attachments/assets/65eeb47b-e717-4ee5-90c9-6a64b6e9a0b2" />


**Question 8**
---
-- <img width="1243" height="499" alt="image" src="https://github.com/user-attachments/assets/cc92b04d-b992-4d8d-8771-48ad1a3482b2" />


```sql
--
SELECT ord_no,purch_amt,ord_date,customer_id,salesman_id
FROM orders
WHERE purch_amt BETWEEN 500 AND 4000 AND purch_amt NOT IN(948.50,1983.43);
```

**Output:**

<img width="1128" height="402" alt="image" src="https://github.com/user-attachments/assets/7832fa10-bef0-4325-afde-8d71fd4fc4c9" />


**Question 9**
---
-- 
<img width="1119" height="582" alt="image" src="https://github.com/user-attachments/assets/673b0aad-112b-4a77-a9d8-4b34071bb324" />


```sql
--
SELECT product_id,discounted_price,discount_percentage,discounted_price/(1-discount_percentage) AS original_price
FROM Products;
```

**Output:**

<img width="1216" height="306" alt="image" src="https://github.com/user-attachments/assets/83400c98-98cf-485d-9ebb-8861bf33376e" />


**Question 10**
---
-- 
<img width="750" height="612" alt="image" src="https://github.com/user-attachments/assets/d450cbc2-8e16-4b7d-a474-68cce458a61e" />


```sql
--
SELECT ename,hiredate,date(hiredate,'+100 days') AS DateAfter100Days
FROM emp;
```

**Output:**

<img width="837" height="417" alt="image" src="https://github.com/user-attachments/assets/2e77e0bb-68d3-41a7-b935-9c13f16af7e8" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
