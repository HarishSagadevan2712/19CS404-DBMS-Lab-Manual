# Experiment 5: Subqueries and Views

## NAME : HARISH S
## REG.NO: 212224110022

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
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is EQUAL TO $1500.

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY = 1500;
```

**Output:**

<img width="1227" height="407" alt="image" src="https://github.com/user-attachments/assets/21230cc3-7c2a-4a8d-9a13-05ceb783f107" />

**Question 2**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

```sql
SELECT *
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi';
```

**Output:**

<img width="1233" height="415" alt="image" src="https://github.com/user-attachments/assets/38e7dea9-c15c-480f-9e60-540fbda345f8" />

**Question 3**
---
From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql
SELECT o.ord_no, 
       o.purch_amt, 
       o.ord_date, 
       o.customer_id, 
       o.salesman_id
FROM ORDERS o
JOIN SALESMAN s
     ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';
```

**Output:**

<img width="1221" height="566" alt="image" src="https://github.com/user-attachments/assets/1a1d0b43-2d05-467f-8dda-8b5d7f34e6fd" />

**Question 4**
---
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the minimum grade achieved in each subject.

```sql
SELECT student_name, grade
FROM GRADES g
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES
    WHERE subject = g.subject
);
```

**Output:**

<img width="808" height="504" alt="image" src="https://github.com/user-attachments/assets/c4043991-c623-45a4-aea1-d57944821ca2" />

**Question 5**
---
Write a SQL query to Retrieve the names and cities of customers who have the same city as customers with IDs 3 and 7

```sql
SELECT name, city
FROM customer
WHERE city IN (
    SELECT city 
    FROM customer 
    WHERE id IN (3, 7)
);
```

**Output:**

<img width="580" height="538" alt="image" src="https://github.com/user-attachments/assets/45454949-e09a-4fc7-9087-137ff542ed84" />

**Question 6**
---
Write a SQL query to List departments with names longer than the average length

```sql
SELECT department_id, department_name
FROM Departments
WHERE LENGTH(department_name) > (
    SELECT AVG(LENGTH(department_name)) 
    FROM Departments
);
```

**Output:**

<img width="621" height="470" alt="image" src="https://github.com/user-attachments/assets/8dc1d8c9-e67a-4d86-8ab9-e0fda4dd03d9" />

**Question 7**
---
Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.

```sql
SELECT *
FROM GRADES g
WHERE grade = (
    SELECT MAX(grade)
    FROM GRADES
    WHERE subject = g.subject
);
```

**Output:**

<img width="1233" height="528" alt="image" src="https://github.com/user-attachments/assets/74a546a6-1604-4d9a-b07e-85237caa2e2c" />

**Question 8**
---
From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql
SELECT o.ord_no, 
       o.purch_amt, 
       o.ord_date, 
       o.customer_id, 
       o.salesman_id
FROM ORDERS o
JOIN SALESMAN s
     ON o.salesman_id = s.salesman_id
WHERE s.name = 'Paul Adam';
```

**Output:**

<img width="1230" height="472" alt="image" src="https://github.com/user-attachments/assets/c85dacf9-61d8-40a0-a6eb-ccb2ea51663a" />

**Question 9**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $1500.

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;
```

**Output:**

<img width="1231" height="686" alt="image" src="https://github.com/user-attachments/assets/31491202-11ff-4513-97f6-fdee56d7bf6c" />

**Question 10**
---
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the maximum grade achieved in each subject.

```sql
SELECT student_name, grade
FROM GRADES g
WHERE grade = (
    SELECT MAX(grade)
    FROM GRADES
    WHERE subject = g.subject
);
```

**Output:**

<img width="791" height="510" alt="image" src="https://github.com/user-attachments/assets/b30c6445-75f3-4b44-9a17-7418d09b0869" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
