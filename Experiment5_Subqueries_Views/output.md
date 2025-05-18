**Question 1**
--
![image](https://github.com/user-attachments/assets/12286628-97ab-4023-aed3-1f2fa7928562)


```sql
select department_id,department_name
from departments
where length(department_name)>
(
    select avg(length(department_name))
    from departments
    
)
```

**Output:**

![image](https://github.com/user-attachments/assets/c41d88f0-cc9c-4b89-9a2c-065a4a32ab23)


**Question 2**
---
![image](https://github.com/user-attachments/assets/9f209c00-ff38-4353-9052-641f98a70432)

```sql
select * from customers
where age<30;
```

**Output:**

![image](https://github.com/user-attachments/assets/4ecc3c05-00e7-4368-97c5-be5386563020)


**Question 3**
---
![image](https://github.com/user-attachments/assets/3c5d7980-2555-4357-aba8-97bb5e838c98)


```sql
select medication_id,medication_name,dosage
from medications
where dosage=
 ( select max(dosage)
  from medications
 
  )
```

**Output:**

![image](https://github.com/user-attachments/assets/95cf3878-87e3-44b3-8759-a74ec9fb66dc)


**Question 4**
---
![image](https://github.com/user-attachments/assets/97ac191f-18ad-4568-9a70-dc9b0b74df66)


```sql
SELECT g.student_name, g.grade
FROM GRADES g
JOIN (
    SELECT subject, MAX(grade) AS max_grade
    FROM GRADES
    GROUP BY subject
) AS max_grades ON g.subject = max_grades.subject AND g.grade = max_grades.max_grade;

```

**Output:**

![image](https://github.com/user-attachments/assets/d0d1a01b-cf32-407f-ae71-e8f47a0785ce)


**Question 5**
---
![image](https://github.com/user-attachments/assets/d1e741fb-ab29-497a-a665-1e3d6dfae401)


```sql
select o.ord_no,o.purch_amt ,o.ord_date  , o.customer_id,o.salesman_id
from orders o
join salesman s on o.salesman_id = s.salesman_id
where s.city='New York'
```

**Output:**

![image](https://github.com/user-attachments/assets/ba7ad4e1-ed44-4a97-8f08-ce950df30333)


**Question 6**
---
![image](https://github.com/user-attachments/assets/a057357e-dce8-42cf-b271-c6f6d7cae4b3)


```sql
SELECT c.customer_id, c.cust_name, c.city, c.grade, c.salesman_id
FROM customer c
WHERE c.customer_id = (
    SELECT s.salesman_id - 2001
    FROM salesman s
    WHERE s.name = 'Mc Lyon'
);

```

**Output:**

![image](https://github.com/user-attachments/assets/c633c053-1209-4185-9dd4-49212e09b3a9)


**Question 7**
---
![image](https://github.com/user-attachments/assets/69222a00-cc19-43ff-8a2c-aaccafdeb359)


```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;

```

**Output:**

![image](https://github.com/user-attachments/assets/d48d7664-70b4-41b0-a48a-47f3bebee77e)


**Question 8**
---
![image](https://github.com/user-attachments/assets/309ed75f-13f5-46f4-94d6-42bc9e2f8884)


```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM ORDERS o
JOIN SALESMAN s ON o.salesman_id = s.salesman_id
WHERE s.city = 'London';

```

**Output:**

![image](https://github.com/user-attachments/assets/be531b06-c6b6-4428-92c1-46a0fe559f3c)


**Question 9**
---
![image](https://github.com/user-attachments/assets/2ef7a70f-03fa-4f18-be15-0835b0231e52)


```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.commission = (SELECT MAX(commission) FROM salesman);

```

**Output:**

![image](https://github.com/user-attachments/assets/2825286f-ba2a-4925-b28e-9b93eb9b874a)


**Question 10**
---
![image](https://github.com/user-attachments/assets/6ffd68b3-9c98-4d57-8c4e-edfe2825eb47)


```sql
SELECT g.*
FROM GRADES g
JOIN (
    SELECT subject, MIN(grade) AS min_grade
    FROM GRADES
    GROUP BY subject
) AS min_grades ON g.subject = min_grades.subject AND g.grade = min_grades.min_grade;

```

**Output:**

![image](https://github.com/user-attachments/assets/2d5f02d3-6576-4ec1-bf5c-90c8e306dea1)
