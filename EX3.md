# EX 3 SubQueries, Views and Joins 


## Create employee Table
```sql
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
## Insert the values
```sql
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```

## Create department table
```sql
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
## Insert the values in the department table
```sql
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.


### QUERY:
```sql
CREATE VIEW details AS SELECT ENAME FROM EMP WHERE SALARY >(select SALARY from EMP where EMPNO=7566);
```

### OUTPUT:
![271343266-bd7ef183-c19b-43d0-9c67-67042eef1d8f](https://github.com/sivabalan28/EX-3-SubQueries-Views-and-Joins/assets/113497347/b1aef6bd-b9cd-44c4-ac58-760217a2f8ec)


### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
```sql
 CREATE VIEW minimum AS select ENAME,JOB,SALARY from EMP where SALARY =(select MIN(SALARY) from EMP);
```

### OUTPUT:
![271343365-1b23ec5d-167c-4cbc-922a-08f76a6a0e3f](https://github.com/sivabalan28/EX-3-SubQueries-Views-and-Joins/assets/113497347/54ec33b0-2a75-47a5-b19e-0df2b1877c68)


### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
```sql
select ENAME,JOB from EMP where  DEPTNO=10 AND JOB='SALESMAN';
```

### OUTPUT:
![271343466-59eaede9-211a-4dfa-b163-c54027ef35b5](https://github.com/sivabalan28/EX-3-SubQueries-Views-and-Joins/assets/113497347/d9478868-18ce-41f5-b884-c26e1733668b)


### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
```sql
create view empv5 as select EMPNO,ENAME,JOB from EMP where DEPTNO=10;
```

### OUTPUT:
![271343552-f2fe871f-c3d2-497c-a563-9961f0187178](https://github.com/sivabalan28/EX-3-SubQueries-Views-and-Joins/assets/113497347/5137c22f-32a5-4e85-8db3-c6119d8714f2)

### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
```sql
create view empv30 AS select EMPNO,ENAME,SALARY from EMP where DEPTNO=30;
```

### OUTPUT:
![271343613-4cb2d8f2-96ef-4086-989d-d4b479ef333b](https://github.com/sivabalan28/EX-3-SubQueries-Views-and-Joins/assets/113497347/85245629-f3c5-43ea-9b33-41a158fec594)

### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
```sql
update EMP set SALARY=SALARY*1.1 WHERE JOB='clerk';

create view empv5 as select EMPNO,ENAME,SALARY,JOB from EMP;
```

### OUTPUT:
![271343687-0b32c3c3-fb49-4129-822c-4d7b1961a59d](https://github.com/sivabalan28/EX-3-SubQueries-Views-and-Joins/assets/113497347/255f3e4f-3d47-4ea0-96ca-bc8ba7d0d9c0)

## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
```sql
select s.name,c.cust_name,s.city from salesman1 as s ,customer1 as c where s.city=c.city;
```

### OUTPUT:
![271343845-04fc7139-1c13-48a7-a8f7-2cdee11905d0](https://github.com/sivabalan28/EX-3-SubQueries-Views-and-Joins/assets/113497347/4421ad0f-5f50-4db1-a2cb-db3d3040d4d8)

### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.


### QUERY:
```sql
select s.name,c.cust_name,c.city,s.commission from salesman1 as s inner join customer1 as c on s.city=c.city where s.commission>0.13;
```

### OUTPUT:
![271343905-23ad5fa8-18c3-4503-a7b8-34e723fbd5c3](https://github.com/sivabalan28/EX-3-SubQueries-Views-and-Joins/assets/113497347/17732299-9278-4ead-a4b6-0c0bff04c427)

### Q9) Perform Natural join on both tables

### QUERY:
```sql
 select s.name,c.cust_name,c.city,s.commission from salesman1 as s natural join customer1 as c where s.commission>0.13;
```

### OUTPUT:
![271344099-3b320e99-72de-4acb-9f2a-4dd824af4ff7](https://github.com/sivabalan28/EX-3-SubQueries-Views-and-Joins/assets/113497347/ec4c82a7-3b0c-4da1-9ba4-34e038ff3ec0)


### Q10) Perform Left and right join on both tables

### QUERY:
```sql
select s.name,c.cust_name,c.city,s.commission from salesman1 as s left join customer1 as c on s.salesman_id=c.salesman_id where s.commission>0.13;

select s.name,c.cust_name,c.city,s.commission from salesman1 as s right join customer1 as c on s.salesman_id=c.salesman_id where s.commission>0.13;
```

### OUTPUT:
![271344262-8e16563a-6ee0-48d8-aeea-99551b711de5](https://github.com/sivabalan28/EX-3-SubQueries-Views-and-Joins/assets/113497347/fa3fc15c-599b-4817-be08-71c31334971b)
