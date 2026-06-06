# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1275" height="715" alt="image" src="https://github.com/user-attachments/assets/4afdc462-198f-41bf-b85f-0b4e6aa765fe" />
--

**sql**
```
--
SELECT* FROM orders
WHERE salesman_id IN(
SELECT salesman_id
FROM salesman
WHERE city='New York'); 
```

**Output:**

<img width="1143" height="463" alt="image" src="https://github.com/user-attachments/assets/15328425-5611-4edd-aeda-c5cc6830fedb" />


**Question 2**
---
<img width="1180" height="562" alt="image" src="https://github.com/user-attachments/assets/ce359043-ef57-4f37-ac5c-4b35b7d42d88" />

---

**sql**
```sql
--
SELECT* FROM GRADES g
WHERE grade=(
SELECT min(grade)
FROM GRADES
WHERE subject=g.subject );
```

**Output:**

<img width="1248" height="457" alt="image" src="https://github.com/user-attachments/assets/66722273-9bbd-46b3-a53c-cd5019da0f92" />


**Question 3**
---
-- 
<img width="916" height="584" alt="image" src="https://github.com/user-attachments/assets/40619833-b70b-4519-a62b-93d5ad5cb87e" />


```sql
--
SELECT * FROM CUSTOMERS
WHERE SALARY IN(
SELECT SALARY
FROM CUSTOMERS
WHERE SALARY<2500);
```

**Output:**

<img width="1105" height="477" alt="image" src="https://github.com/user-attachments/assets/077e43dc-746c-4476-978e-53d60c8b5648" />


**Question 4**
---
<img width="1020" height="601" alt="image" src="https://github.com/user-attachments/assets/35b978d8-8eee-4e1f-acd6-9336303baa37" />

---

```sql
--
SELECT * FROM Employee
WHERE age<(
SELECT AVG(age)
FROM Employee
WHERE income>250000);
```

**Output:**

<img width="1296" height="523" alt="image" src="https://github.com/user-attachments/assets/0f87643b-dbaf-468b-8d29-2d330c80135a" />


**Question 5**
---
 <img width="986" height="487" alt="image" src="https://github.com/user-attachments/assets/19202f3f-b351-4d37-9ac7-e5f110eb5aa0" />
---


```sql
--
SELECT * FROM customer 
WHERE city != (
    SELECT city 
    FROM customer 
    WHERE id = (SELECT MAX(id) FROM customer)
);
```

**Output:**

<img width="1284" height="500" alt="image" src="https://github.com/user-attachments/assets/89c31606-e228-4651-ad9d-e65f7e320289" />


**Question 6**
---
--
<img width="1004" height="490" alt="image" src="https://github.com/user-attachments/assets/bc6311e2-b9cd-4dc9-8ebe-61ef18855a43" />


```sql
--
SELECT name,city
FROM customer
WHERE city IN(
SELECT city
FROM customer
WHERE id in(3,7));
```

**Output:**
<img width="541" height="466" alt="image" src="https://github.com/user-attachments/assets/31014ba6-59b8-4ea5-ba93-488599c8bfff" />


**Question 7**
---
<img width="1257" height="558" alt="image" src="https://github.com/user-attachments/assets/10fa6eaa-b00c-4ea1-aafa-28adcf2a1ad8" />
---


```sql
--
SELECT*FROM ORDERS
WHERE purch_amt>(
SELECT AVG(purch_amt)
FROM ORDERS
WHERE ord_date='2012-10-10');
```

**Output:**

<img width="1114" height="477" alt="image" src="https://github.com/user-attachments/assets/1e53e0fc-72f3-4acd-be13-0f6a5c215deb" />


**Question 8**
---
<img width="895" height="664" alt="image" src="https://github.com/user-attachments/assets/d6385fab-7321-461f-b03b-dc434796c2ba" />
---

```sql
--
SELECT*FROM CUSTOMERS
WHERE AGE IN (SELECT AGE FROM CUSTOMERS WHERE AGE<30);
```

**Output:**

<img width="1099" height="576" alt="image" src="https://github.com/user-attachments/assets/c0f16260-3051-4412-bf4a-a88dee66d415" />


**Question 9**
---
<img width="1231" height="554" alt="image" src="https://github.com/user-attachments/assets/f7d43cd2-52e5-41cc-a4c7-b04a7e60627d" />
---

```sql
--
SELECT student_name,grade
FROM GRADES g
WHERE grade in(
SELECT max(grade)
FROM GRADES
WHERE subject=g.subject)
GROUP BY student_name;

```

**Output:**

<img width="716" height="445" alt="image" src="https://github.com/user-attachments/assets/c728d906-9e69-4277-9b6a-53fe8016f619" />


**Question 10**
---
<img width="1036" height="536" alt="image" src="https://github.com/user-attachments/assets/aec205bf-5590-4673-861c-1a4896d76f4b" />
---

```sql
--
SELECT*FROM Employee
WHERE age<(
SELECT AVG(age)
FROM Employee
WHERE income>1000000);
```

**Output:**

<img width="1236" height="411" alt="image" src="https://github.com/user-attachments/assets/bed0daf0-a41c-4d9f-9a92-f90ddbb89d2d" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
