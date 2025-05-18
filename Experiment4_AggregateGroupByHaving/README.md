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
![image](https://github.com/user-attachments/assets/c20e9827-6c28-41f5-9e31-81f9f5a45ea0)

```sql
select Medication ,count(*) as TotalPrescriptions
from Prescriptions
group by Medication
```

**Output:**

![image](https://github.com/user-attachments/assets/7f3c35f9-b2cd-4bef-9365-03517a00e5cb)


**Question 2**
---
![image](https://github.com/user-attachments/assets/b8a2649f-d2ab-40cd-ac97-dc991f9352aa)


```sql
select DoctorID , count(*) as TotalPrescriptions
from Prescriptions
group by DoctorID
```

**Output:**

![image](https://github.com/user-attachments/assets/28271c15-e793-4ad2-a29b-d3e6a2eb7ffb)


**Question 3**
---
![image](https://github.com/user-attachments/assets/07ec12a2-0db3-4f8a-8c31-8b727190b285)


```sql
select avg(length((TRIM(name)))) as avg_name_length
from customer
where lower(city)='chennai';
```

**Output:**

![image](https://github.com/user-attachments/assets/c1a01ddc-875e-4db0-8e35-08442f129cdd)


**Question 4**
---
![image](https://github.com/user-attachments/assets/60c706d9-17bd-422f-bfad-e3784d1522af)


```sql
select name,max(income) as 'max(income)'
from employee
where city= 'California'

```

**Output:**

![image](https://github.com/user-attachments/assets/35a12f99-b7ed-427c-8637-d5f1e84478c6)


**Question 5**
---
![image](https://github.com/user-attachments/assets/1e62ac7c-bd05-49d4-afe6-6d53510d7eca)


```sql
select sum(inventory) as 'total_available_amount'
from fruits
where price > 0.5
```

**Output:**

![image](https://github.com/user-attachments/assets/ed8453b2-a843-4207-9ac4-d26fa76d5437)


**Question 6**
---
![image](https://github.com/user-attachments/assets/440942bb-4b67-4ddd-8650-da08559b648d)



```sql
select count(distinct city) as unique_cities
from customer--
```

**Output:**

![image](https://github.com/user-attachments/assets/1ac22239-383c-4861-b2c9-acec7c828e3b)


**Question 7**
---
![image](https://github.com/user-attachments/assets/283b6a21-5125-4329-ad3c-0d523f694e8f)


```sql
select city,sum(Income) as Income
from employee
group by city
having sum(income)>200000
```

**Output:**

![image](https://github.com/user-attachments/assets/0bc08419-781d-44fd-8383-c04af37b1b74)


**Question 8**
---
![image](https://github.com/user-attachments/assets/18dd1ca2-20de-4338-8424-d5fc457d6cad)


```sql
select  (age/5)*5 as 'age_group',MIN(age) 
from customer1
group by age_group
HAVING MIN(age)<25
```

**Output:**

![image](https://github.com/user-attachments/assets/408f5167-44f6-41c1-a3e8-38c41e6d38ff)


**Question 9**
---
![image](https://github.com/user-attachments/assets/94bde942-14a1-40e0-acb6-742f88b29384)


```sql
select category_id , sum(price) as Total_Cost
from products
group by category_id
having sum(price)>50
```

**Output:**

![image](https://github.com/user-attachments/assets/da0d8905-6e09-4f83-bb98-70046914d99c)


**Question 10**
---
![image](https://github.com/user-attachments/assets/0d8e7338-8b4d-4c97-a586-092273b6cc88)


```sql
select address,AVG(salary)
from customer1
group by address
having AVG(salary)>5000;
```

**Output:**

![image](https://github.com/user-attachments/assets/7db45bd7-4094-4edc-9b0c-207f49ad85ed)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
