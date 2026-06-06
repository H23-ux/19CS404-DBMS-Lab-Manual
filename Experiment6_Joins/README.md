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
<img width="1223" height="392" alt="image" src="https://github.com/user-attachments/assets/0efff6f6-f774-4df3-a492-c2af4a9e8e36" />
-- 

```sql
SELECT c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt
FROM customer c
LEFT JOIN orders o
ON c.customer_id=o.customer_id
WHERE c.city='London';
```

**Output:**

<img width="1274" height="505" alt="image" src="https://github.com/user-attachments/assets/a5f3883b-676e-4072-9be1-bea4cdeaa5b5" />


**Question 2**
---
<img width="1198" height="885" alt="image" src="https://github.com/user-attachments/assets/b66b0145-bd58-45e4-a1cd-e785d9e9c703" />
---

```sql
SELECT o.ord_no,
       o.ord_date,
       o.purch_amt,
       c.cust_name as "Customer Name",
       c.grade,
       s.name as "Salesman",
       s.commission
FROM orders o 
INNER JOIN customer c
ON o.customer_id = c.customer_id
INNER JOIN salesman s
ON o.salesman_id = s.salesman_id;
```

**Output:**


<img width="1290" height="400" alt="image" src="https://github.com/user-attachments/assets/5c93c915-eea1-48a5-8cbf-31244d343d54" />


**Question 3**
---

<img width="1266" height="618" alt="image" src="https://github.com/user-attachments/assets/49105799-257b-4653-825b-bc6f023bfe67" />
---

```sql
SELECT p.*
FROM PATIENTS p
INNER JOIN APPOINTMENTS a
ON p.patient_id = a.patient_id
WHERE a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**


<img width="1275" height="441" alt="image" src="https://github.com/user-attachments/assets/1499e922-d3eb-41fe-a5d5-f81bb46731a5" />


**Question 4**
---

<img width="1265" height="699" alt="image" src="https://github.com/user-attachments/assets/e1859458-22ab-4c1f-b8ee-cc992d48c3f9" />
---

```sql
SELECT p.*
FROM PATIENTS p
INNER JOIN DOCTORS d
ON p.doctor_id = d.doctor_id
WHERE d.first_name ='John' AND d.last_name='Smith';
```

**Output:**


<img width="1289" height="444" alt="image" src="https://github.com/user-attachments/assets/fea29e9f-b063-4ab8-a601-7886b5b5ae38" />


**Question 5**
---

<img width="1279" height="740" alt="image" src="https://github.com/user-attachments/assets/21045c17-8b1f-4df1-9003-c2655a6b6dd4" />
---

```sql
SELECT p.admission_date,s.surgery_date
FROM PATIENTS p
INNER JOIN SURGERIES s
ON p.patient_id=s.patient_id;
```

**Output:**


<img width="705" height="554" alt="image" src="https://github.com/user-attachments/assets/fe97a19b-73bd-4301-81d2-a8a2c802ce28" />


**Question 6**
---

<img width="1299" height="803" alt="image" src="https://github.com/user-attachments/assets/cd886b2e-f107-4202-aaa1-03e5279424f8" />
---

```sql
SELECT c.cust_name as "Customer Name",
       c.city,
       s.name as "Salesman",
       s.city,
       s.commission
FROM customer c
INNER JOIN salesman s ON c.salesman_id = s.salesman_id
AND c.city != s.city
WHERE s.commission>0.12;
```

**Output:**


<img width="1305" height="632" alt="image" src="https://github.com/user-attachments/assets/2ee0b8df-3897-4ace-b913-6a6e12ce3c68" />


**Question 7**
---

<img width="1242" height="663" alt="image" src="https://github.com/user-attachments/assets/d2b199fe-783e-4392-8e4f-819d91b2c43b" />
---

```sql
SELECT c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt as "Order Amount"
FROM customer c
LEFT JOIN orders o
ON o.customer_id = c.customer_id
ORDER BY o.ord_date ASC;
```

**Output:**


<img width="1263" height="699" alt="image" src="https://github.com/user-attachments/assets/72c0dfe3-097d-402e-bf0c-e8a834cb70b7" />


**Question 8**
---

<img width="1310" height="907" alt="image" src="https://github.com/user-attachments/assets/6010aa33-0f99-4257-8cd9-87012f2e9796" />
---

```sql
SELECT c.cust_name,c.city,c.grade,s.name as  "Salesman",s.city
FROM customer c
LEFT JOIN salesman s
ON c.salesman_id = s.salesman_id
ORDER BY c.customer_id ASC;
```

**Output:**


<img width="1281" height="851" alt="image" src="https://github.com/user-attachments/assets/477e521e-240c-4106-a1d3-ab696e07fc2d" />


**Question 9**
---

<img width="1304" height="903" alt="image" src="https://github.com/user-attachments/assets/073c0aed-6468-4b3d-a5e8-e05587dbc14d" />
---

```sql
SELECT o.ord_no,o.purch_amt,o.ord_date,c.cust_name,c.city as "customer_city",c.grade,s.name as "salesman_name",s.city as "salesman_city",s.commission
FROM orders o
LEFT JOIN customer c
ON o.customer_id = c.customer_id
LEFT JOIN salesman s
ON o.salesman_id = s.salesman_id;
```

**Output:**


<img width="1299" height="700" alt="image" src="https://github.com/user-attachments/assets/e3a65571-e348-4538-b7cb-895b651712f5" />


**Question 10**
---

<img width="1278" height="314" alt="image" src="https://github.com/user-attachments/assets/884fa0b5-8a9f-4a35-98bb-33e4caab166f" />
---

```sql
SELECT c.*
FROM Customer c
LEFT JOIN Salesman s
ON c.salesman_id = s.salesman_id
WHERE s.name ='Mc Lyon';
```

**Output:**


<img width="1292" height="438" alt="image" src="https://github.com/user-attachments/assets/51bc881e-044a-4b51-980b-3302d3571cbe" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
