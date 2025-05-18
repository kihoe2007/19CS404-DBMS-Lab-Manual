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
![image](https://github.com/user-attachments/assets/204a508b-d1da-4861-aafa-b46b21fcbbaf)


```sql
select c.* 
from Customer c
left join salesman s on c.salesman_id=s.salesman_id
where s.name='Mc Lyon'
```

**Output:**

![image](https://github.com/user-attachments/assets/c9679985-aed0-46db-a37c-0252f1b95b79)

**Question 2**
---
![image](https://github.com/user-attachments/assets/27a3cfe6-dd9d-4d61-a4ba-2552398babc9)


```sql
select c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt
from CUSTOMER c
left join ORDERS o ON c.customer_id = o.customer_id
where c.city='London'
```

**Output:**

![image](https://github.com/user-attachments/assets/2ad731f6-922e-4e0e-a349-4428549255c6)

**Question 3**
---
![image](https://github.com/user-attachments/assets/03fe1d24-a958-43e9-bdca-24f0d34957f6)


```sql
select p.first_name,s.* 
from PATIENTS p
inner join SURGERIES s ON p.patient_id=s.patient_id
where discharge_date='2024-03-01' and '2024-03-31'
```

**Output:**

![image](https://github.com/user-attachments/assets/081e35b6-a1d7-4389-8346-b2a02699407d)


**Question 4**
---
![image](https://github.com/user-attachments/assets/6879948c-a28c-4937-be12-03353f960223)


```sql
-- Paste your SQL code below for Question 4select c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt as 'Order Amount'
from customer c
left join orders o on  c.customer_id=o.customer_id
order by o.ord_date ASC

```

**Output:**

![image](https://github.com/user-attachments/assets/5daeddc0-a103-4d9c-a7a7-7450a18f7bd2)


**Question 5**
---
![image](https://github.com/user-attachments/assets/d713b8c8-568d-42c6-9067-abd32d44b710)


```sql
SELECT p.first_name as 'patient_name',d.first_name as 'doctor_name'
from PATIENTS p
inner join DOCTORS d ON p.doctor_id=d.doctor_id
where p.discharge_date IS NULL
```

**Output:**

![image](https://github.com/user-attachments/assets/6d12412a-4ab1-4f23-98de-f92253601f36)

**Question 6**
---
![image](https://github.com/user-attachments/assets/b94cb877-0e63-4a2c-bdde-7be1b07d5b5f)

```sql
select c.cust_name as "Customer Name",c.city as "city",s.name as "Salesman",s.commission as "commission"
from customer c
left join salesman s on c.salesman_id = s.salesman_id
```

**Output:**

![image](https://github.com/user-attachments/assets/b6f98970-ceb3-44fe-ada7-e7c02776cd8b)


**Question 7**
---
![image](https://github.com/user-attachments/assets/addd8a0c-e191-4ed9-9545-f280fb986fbc)


```sql
select p.*
from PATIENTS p
inner join DOCTORS d ON p.doctor_id=d.doctor_id
where d.first_name='John' and d.last_name='Smith'
```

**Output:**

![image](https://github.com/user-attachments/assets/0f78494d-1e6c-4ec7-991e-d0788a342b84)


**Question 8**
---
![image](https://github.com/user-attachments/assets/6a9a0f97-9494-4dad-8543-6a7cbfeba3e6)


```sql
select c.cust_name as 'Customer Name',c.city,s.name as 'Salesman',s.commission
from customer c
left join salesman s on c.salesman_id=s.salesman_id
where s.commission >0.12
```

**Output:**

![image](https://github.com/user-attachments/assets/5e173815-e9f6-42a6-82e1-f184c6f0ad3e)

**Question 9**
---
![image](https://github.com/user-attachments/assets/e06fbb33-7654-4c29-a19e-3e1f367e8d93)


```sql
select c.cust_name ,c.city,o.ord_no,o.ord_date,o.purch_amt as 'Order Amount',s.name,s.commission
from customer c
left outer join orders o on c.customer_id =o.customer_id
left outer join salesman s on c.salesman_id=s.salesman_id
```

**Output:**

![image](https://github.com/user-attachments/assets/e57fdd83-a611-46fa-b1fb-b11419cb5ac9)


**Question 10**
---
![image](https://github.com/user-attachments/assets/7c2423ea-726b-43aa-a484-a4af700d44cf)


```sql
select c.cust_name as 'Customer Name',c.city,s.name as 'Salesman',s.commission
from customer c
left join salesman s on c.salesman_id=s.salesman_id
```

**Output:**

![image](https://github.com/user-attachments/assets/fd38ec67-c578-4b16-b66d-cc6650db557c)
## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
