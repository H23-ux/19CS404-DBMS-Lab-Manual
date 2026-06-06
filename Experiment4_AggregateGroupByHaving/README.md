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
-- <img width="868" height="566" alt="image" src="https://github.com/user-attachments/assets/5ec1b8e9-f458-4c5b-9ac7-0a9c8e61ca7d" />


```sql
--
SELECT PatientID,COUNT(*) AS TotalMedications
FROM Prescriptions
GROUP BY PatientID;
```

**Output:**

<img width="618" height="729" alt="image" src="https://github.com/user-attachments/assets/751aa427-cb4e-411f-a7b0-1a3b7be67cf0" />


**Question 2**
---
-- <img width="880" height="568" alt="image" src="https://github.com/user-attachments/assets/6c76ab55-fbc0-4ff0-bedd-d8911585b9dc" />


```sql
--
SELECT Medication,AVG(Dosage) as AvgDosage
FROM Prescriptions
GROUP BY Medication;
```

**Output:**

<img width="548" height="757" alt="image" src="https://github.com/user-attachments/assets/cb28d3b1-618e-4df8-bd8f-a8acdc0b35a0" />


**Question 3**
---
-- <img width="827" height="590" alt="image" src="https://github.com/user-attachments/assets/70bfc90e-459c-416d-8a37-be3a95197826" />


```sql
--
SELECT InsuranceCompany,AVG(EndDate-StartDate) AS AvgCoverageDurationDays
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**

<img width="862" height="678" alt="image" src="https://github.com/user-attachments/assets/5ea73107-0b96-4871-adbd-3b27ca5957c0" />


**Question 4**
---
-- <img width="879" height="445" alt="image" src="https://github.com/user-attachments/assets/a59e1357-63b7-4bcc-a078-13e6be5e3cab" />


```sql
--
SELECT COUNT(*) AS COUNT
FROM customer
GROUP BY 'all'
HAVING grade is not null;
```

**Output:**
<img width="390" height="343" alt="image" src="https://github.com/user-attachments/assets/f1ffa23f-9977-43b3-ab7c-fa2f93da7aec" />



**Question 5**
---
-- <img width="818" height="453" alt="image" src="https://github.com/user-attachments/assets/0dd587cc-c7a9-4f54-ba65-7093fef71277" />


```sql
--
SELECT COUNT(*) AS COUNT
FROM customer
WHERE city='Noida'
GROUP BY 'all';
```

**Output:**

<img width="390" height="346" alt="image" src="https://github.com/user-attachments/assets/b83882ef-e25a-43d0-92b8-d1be064a569c" />


**Question 6**
---
-- <img width="775" height="441" alt="image" src="https://github.com/user-attachments/assets/ab5d776b-4825-4ff3-9621-28fcc5385ee9" />


```sql
--
SELECT COUNT(DISTINCT(salesman_id)) as COUNT
FROM orders;
```

**Output:**

<img width="378" height="346" alt="image" src="https://github.com/user-attachments/assets/aa0becc5-3305-44ee-b141-1f82e1b34db1" />


**Question 7**
---
-- <img width="880" height="417" alt="image" src="https://github.com/user-attachments/assets/43c7b18d-b7a4-49ca-9812-e556b7bda225" />


```sql
--
SELECT AVG(LENGTH(email)) AS avg_email_length_below_30
FROM customer
WHERE city='Mumbai'
GROUP BY 'all';
```

**Output:**

<img width="613" height="336" alt="image" src="https://github.com/user-attachments/assets/d80bcd1e-3290-4bb8-a46f-4d973615e52d" />


**Question 8**
---
-- <img width="1220" height="390" alt="image" src="https://github.com/user-attachments/assets/4827c497-7893-4c44-b0cf-6ba641ea8306" />


```sql
--
SELECT (age/5)*5 as age_group,MIN(age)
FROM customer1
GROUP BY (age/5)*5
HAVING MIN(age)<25;
```

**Output:**

<img width="581" height="350" alt="image" src="https://github.com/user-attachments/assets/1d632c55-acfa-4d93-a863-30619b053ae3" />


**Question 9**
---
-- <img width="1222" height="401" alt="image" src="https://github.com/user-attachments/assets/fac8b809-b13a-439b-adce-e2a39c5d65a4" />


```sql
--
SELECT (age/5)*5 as age_group,MIN(salary)
FROM customer1
GROUP BY (age/5)*5
HAVING MIN(salary)<2000;
```

**Output:**

<img width="579" height="365" alt="image" src="https://github.com/user-attachments/assets/1b50620b-f94d-4d2c-b511-d7e71f05755e" />


**Question 10**
---
-- <img width="1058" height="414" alt="image" src="https://github.com/user-attachments/assets/82848790-80d2-4288-b0d0-62be21b6bc96" />


```sql
--
SELECT address,AVG(salary)
FROM customer1
GROUP BY address
HAVING AVG(salary)>5000;
```

**Output:**

<img width="543" height="459" alt="image" src="https://github.com/user-attachments/assets/feab47ac-1140-48a1-8345-6fecefdd0cbc" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
