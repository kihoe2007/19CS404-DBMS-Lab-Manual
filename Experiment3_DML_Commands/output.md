**Question 1**
--
![image](https://github.com/user-attachments/assets/1d5923d0-1ddd-46ea-869f-1b7248ff2417)


```sql
UPDATE products
set product_name='Premium Bread'
where product_id =5
```

**Output:**

![image](https://github.com/user-attachments/assets/9e4baf63-8af6-40f9-8715-ac39efd17a06)


**Question 2**
---
![image](https://github.com/user-attachments/assets/9ecb40e9-c77a-429e-88f5-5c2c6f623a3f)


```sql
update products
set quantity = quantity *1.10
```

**Output:**

![image](https://github.com/user-attachments/assets/9e2bd31c-c2c9-4503-9e3a-98e6843a55b4)


**Question 3**
---
![image](https://github.com/user-attachments/assets/d6699c4a-ef94-404b-9e80-e0a4d641b894)


```sql
update SALES
set total_sell_price=quantity*sell_price
where product_id=10
```

**Output:**

![image](https://github.com/user-attachments/assets/f778c94c-fdbb-4204-b5af-8f365fdecc93)


**Question 4**
---
![image](https://github.com/user-attachments/assets/540aac5b-838a-4d9c-81ba-d391f640ce38)

```sql
update suppliers
set supplier_name='A1 Suppliers'
where supplier_id=8
```

**Output:**

![image](https://github.com/user-attachments/assets/4c1b9aa7-5b39-4c21-b64d-0995c62f8f25)

**Question 5**
---
![image](https://github.com/user-attachments/assets/5b931500-0d0a-49c5-840f-fccb41cc6527)


```sql
update PRODUCTS
set reorder_lvl=40
where category="Grocery"
```

**Output:**

![image](https://github.com/user-attachments/assets/623a7916-4826-4a21-877b-c71f1b3c53db)

**Question 6**
---
![image](https://github.com/user-attachments/assets/0d32b081-cc1b-49fa-bd5c-4f80850d88d5)


```sql
delete from Surgeries
where surgery_id = 3

```

**Output:**

![image](https://github.com/user-attachments/assets/e7cb2140-ed37-409f-9080-ec39708714bc)


**Question 7**
---
![image](https://github.com/user-attachments/assets/6509dd96-7a21-456d-b811-f14feeb2d80a)


```sql
delete from Doctors
where specialization = 'Cardiology'
```

**Output:**

![image](https://github.com/user-attachments/assets/50d2f4fa-b8d9-4216-b490-31b3d7128f6c)


**Question 8**
---
![image](https://github.com/user-attachments/assets/0c829cb3-9b5d-4ef6-ac16-50f053102a6c)


```sql
delete from Customer
where grade!=3
```

**Output:**

![image](https://github.com/user-attachments/assets/c3e4d933-418c-4830-903d-2e35e3460f8b)


**Question 9**
---
![image](https://github.com/user-attachments/assets/00d532d0-0be9-4df1-a043-b9623f51b0e2)

```sql
select * from employeeposition
where salary between 50000 and 100000
```

**Output:**

![image](https://github.com/user-attachments/assets/15036e91-09f1-4265-adc2-864292ec4b94)


**Question 10**
---
![image](https://github.com/user-attachments/assets/ddbacac3-6241-4aba-a934-1feeb6ddefde)


```sql
select * from EmployeeInfo
limit 5 offset 4
```

**Output:**

![image](https://github.com/user-attachments/assets/01dbda25-782a-4c1e-8089-f2355ca35611)
