# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers
## PROGRAM
```
DECLARE
   num1 NUMBER := 25;  -- You can change the values as needed
   num2 NUMBER := 40;
   greatest NUMBER;
BEGIN
   IF num1 > num2 THEN
      greatest := num1;
   ELSE
      greatest := num2;
   END IF;

   DBMS_OUTPUT.PUT_LINE('The greatest number is: ' || greatest);
END;
```

## OUTPUT
![image](https://github.com/user-attachments/assets/d076b533-1f4b-4187-ad90-dcc4ce6a7b7a)

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

## PROGRAM
```
DECLARE
   n        NUMBER := 10; -- You can change this value or accept input
   sum      NUMBER := 0;
   counter  NUMBER := 1;
BEGIN
   WHILE counter <= n LOOP
      sum := sum + counter;
      counter := counter + 1;
   END LOOP;

   DBMS_OUTPUT.PUT_LINE('The sum of first ' || n || ' natural numbers is: ' || sum);
END;
```

## OUTPUT
![image](https://github.com/user-attachments/assets/2c602fea-16b5-49be-8f61-9fcb8ff98fb3)


## 3. Write a PL/SQL program to generate Fibonacci series

## PROGRAM
```
DECLARE
   n        NUMBER := 10; -- Number of terms to generate
   a        NUMBER := 0;
   b        NUMBER := 1;
   c        NUMBER;
   i        NUMBER := 1;
BEGIN
   DBMS_OUTPUT.PUT_LINE('Fibonacci Series up to ' || n || ' terms:');
   WHILE i <= n LOOP
      DBMS_OUTPUT.PUT_LINE(a);
      c := a + b;
      a := b;
      b := c;
      i := i + 1;
   END LOOP;
END;
```

## OUTPUT
![image](https://github.com/user-attachments/assets/f7d3359d-8d03-434b-9255-2dc5b5988be0)


## 4. Write a PL/SQL Program to display the number in Reverse Order

## PROGRAM
```
DECLARE
   num        NUMBER := 12345;  -- Original number
   reversed   NUMBER := 0;
   remainder  NUMBER;
BEGIN
   DBMS_OUTPUT.PUT_LINE('Original number: ' || num);

   WHILE num > 0 LOOP
      remainder := MOD(num, 10);        -- Get the last digit
      reversed := reversed * 10 + remainder;  -- Append it in reverse
      num := TRUNC(num / 10);           -- Remove the last digit
   END LOOP;

   DBMS_OUTPUT.PUT_LINE('Reversed number: ' || reversed);
END;
```

## OUTPUT
![image](https://github.com/user-attachments/assets/b45f23c6-4e9f-4d95-909e-b31812f10bd2)

## 5. Write a PL/SQL program to find the largest of three numbers
## PROGRAM
```
DECLARE
   num1     NUMBER := 25;  -- You can change these values
   num2     NUMBER := 40;
   num3     NUMBER := 15;
   largest  NUMBER;
BEGIN
   IF (num1 >= num2) AND (num1 >= num3) THEN
      largest := num1;
   ELSIF (num2 >= num1) AND (num2 >= num3) THEN
      largest := num2;
   ELSE
      largest := num3;
   END IF;

   DBMS_OUTPUT.PUT_LINE('The largest number is: ' || largest);
END;
```

## OUTPUT
![image](https://github.com/user-attachments/assets/646eb6bb-70da-47bf-9d5f-0a8167b48771)

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
