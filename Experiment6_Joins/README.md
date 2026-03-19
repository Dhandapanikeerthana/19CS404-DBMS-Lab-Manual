## REG NO: 212224040155
## NAME: KEERTHANA D
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

## Question 1
<img width="1258" height="612" alt="image" src="https://github.com/user-attachments/assets/b96ac790-ae60-4106-8569-45a3a07fdf46" />

## Program
```
SELECT p.*
FROM patients p, test_results t
WHERE p.patient_id = t.patient_id
  AND t.test_name IN ('Blood Test','Blood Pressure')
  AND t.result NOT LIKE '%Normal%';

```

## Output
<img width="1604" height="292" alt="image" src="https://github.com/user-attachments/assets/4796ec25-66a5-4e7b-b879-8cd1ee71252d" />



## Question 2
<img width="1608" height="552" alt="image" src="https://github.com/user-attachments/assets/39885341-3eb9-4f00-8cd8-03b33a129d39" />

## Program
```
SELECT p.first_name AS patient_name, d.first_name AS doctor_name
FROM patients p
JOIN doctors d ON p.doctor_id = d.doctor_id
WHERE p.discharge_date IS NOT NULL;

```
## Output

<img width="876" height="292" alt="image" src="https://github.com/user-attachments/assets/925e895d-60a6-4229-8d35-45c1f8126051" />




## Question 3

<img width="1611" height="647" alt="image" src="https://github.com/user-attachments/assets/b46ced48-7561-4994-ac25-88653052850e" />

## Program
```
SELECT c.cust_name AS "Customer Name", c.city AS "city",
       s.name AS "Salesman", s.city AS "city", s.commission AS "commission"
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city AND s.commission > 0.12;

```

## Output

<img width="841" height="232" alt="image" src="https://github.com/user-attachments/assets/3230bc9a-91d8-4add-9eb1-7f47a6b73347" />




## Question 4

<img width="1189" height="174" alt="image" src="https://github.com/user-attachments/assets/44cba233-c506-4cc9-a397-1ea4f9c30795" />


## Program
```
SELECT s.name
FROM salesman s
LEFT JOIN customer c ON s.salesman_id = c.salesman_id
WHERE c.city = 'New York';
```

## Output

  <img width="726" height="225" alt="image" src="https://github.com/user-attachments/assets/eea5e523-e2a1-43a2-bbc2-3361dc8bc8e4" />



## Question 5

<img width="1134" height="515" alt="image" src="https://github.com/user-attachments/assets/a35fcafe-1696-42c6-9e02-b705e6bdfa81" />

## Program
```
SELECT c.cust_name AS "Customer Name", c.city AS "city",
       s.name AS "Salesman", s.commission AS "commission"
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;

```

## Output
<img width="1093" height="435" alt="image" src="https://github.com/user-attachments/assets/7662dd13-fea6-4193-9a0d-1d064a045478" />


## Question 6

<img width="1260" height="267" alt="image" src="https://github.com/user-attachments/assets/ed12ed1c-a64a-4b79-9e00-d5a184aacc72" />


## Program
```
SELECT c.*
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.ord_date > '2012-08-17';

```

## Output
  <img width="1123" height="479" alt="image" src="https://github.com/user-attachments/assets/20317266-cb15-4b03-85d0-3d35bb339bf2" />


## Question 7

<img width="1259" height="542" alt="image" src="https://github.com/user-attachments/assets/620b8848-ccbc-4baa-9731-d38054aa7d65" />

## Program
```
SELECT a.cust_name, a.city, b.ord_no,
       b.ord_date, b.purch_amt AS "Order Amount", 
       c.name, c.commission 
-- Specifying the tables to retrieve data from ('customer' as 'a', 'orders' as 'b', and 'salesman' as 'c')
FROM customer a 
-- Performing a left outer join based on the customer_id, including unmatched rows from 'customer'
LEFT OUTER JOIN orders b 
ON a.customer_id = b.customer_id 
-- Performing another left outer join with the result of the previous join and the 'salesman' table based on salesman_id
LEFT OUTER JOIN salesman c 
ON c.salesman_id = b.salesman_id;
```


## Output
<img width="1252" height="679" alt="image" src="https://github.com/user-attachments/assets/d1d7892b-641b-4501-b47d-c3bed0a4547c" />


## Question 8


<img width="1262" height="558" alt="image" src="https://github.com/user-attachments/assets/0cb14eaf-9505-4841-b5d9-b3378793ef41" />

## Program
```
SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```

## Output

<img width="1237" height="443" alt="image" src="https://github.com/user-attachments/assets/3e3b8d3a-6bb5-4346-9a78-1d509532494d" />


## Question 9


<img width="1247" height="551" alt="image" src="https://github.com/user-attachments/assets/2b4572e4-4159-4ec1-8f48-23696c6d1f26" />

## Program
```
SELECT a.cust_name, a.city, a.grade, 
       b.name AS "Salesman", b.city 
FROM customer a 
LEFT JOIN salesman b 
ON a.salesman_id = b.salesman_id 
ORDER BY a.customer_id;
```


## Output

<img width="1171" height="512" alt="image" src="https://github.com/user-attachments/assets/b6ed4e77-fc42-4740-aa48-1da38ebae06c" />


## Question 10

<img width="1252" height="401" alt="image" src="https://github.com/user-attachments/assets/558eed87-65e1-44fb-a9d9-4759caa44b00" />

## Program
```
SELECT 
    p.first_name AS patient_name,
    t.test_name
FROM patients p
INNER JOIN test_results t 
    ON p.patient_id = t.patient_id;

```

## Output

<img width="952" height="315" alt="image" src="https://github.com/user-attachments/assets/b390878c-90c1-4384-9654-19a0893fdbbd" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
