## 3. ASSIGNMENT ON WHERE CLAUSE

1. WAQTD THE ANNUAL SALARY OF THE EMPLOYEE WHOSE NAME IS SMITH.
```SQL
SELECT SAL*12 "SMITH'S ANNUAL SALARY" 
FROM EMP
WHERE ENAME = 'SMITH'; 

-- OUTPUT:
SMITH'S ANNUAL SALARY
-------------
         9600
```
---
2. WAQTD THE NAMES OF THE EMPLOYEES WORKING AS CLERK.
```SQL
SELECT ENAME "CLERK NAMES"
FROM EMP
WHERE JOB = 'CLERK';

-- OUTPUT:
CLERK NAME
----------
SMITH
ADAMS
JAMES
MILLER
```
---
3. WAQTD THE SALARY OF THE EMPLOYEES WHO ARE WORKING AS SALESMAN.
```SQL
SELECT SAL "SALESMAN SALARY"
FROM EMP
WHERE JOB = 'SALESMAN';

-- OUTPUT:
SALESMAN SALARY
---------------
           1600
           1250
           1250
           1500
```
---
4. WAQTD THE DETAILS OF THE EMPLOYEES WHO EARN MORE THAN 2000.
```SQL
SELECT EMP.* 
FROM EMP 
WHERE SAL > 2000;

-- OUTPUT:
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20
      7839 KING       PRESIDENT            17-NOV-81       5000                    10
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20

6 rows selected.
```
---
5. WAQTD THE DETAILS OF THE EMPLOYEE WHOSE NAME IS JONES.
```SQL
SELECT * FROM EMP       
WHERE ENAME = JONES;

-- OUTPUT:
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20
```
---

6. WAQTD THE DETAILS OF THE EMPLOYEES WHO WERE HIRED AFTER 01-JAN-81.
```SQL
SELECT * FROM EMP 
WHERE HIREDATE > '01-JAN-81';
SQL> SELECT * FROM EMP WHERE HIREDATE > '01-JAN-81';

     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20
      7839 KING       PRESIDENT            17-NOV-81       5000                    10
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30
      7876 ADAMS      CLERK           7788 23-MAY-87       1100                    20
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10

13 rows selected.
```
---
7. WAOTD THE NAME AND SALARY ALONG WITH THE ANNUAL SALARY IF THE ANNUAL SALARY IS MORE THAN 12000.
```SQL
SELECT ENAME NAME, SAL "MONTHLY SALARY", SAL*12 "ANNUAL SALARY"
FROM EMP
WHERE SAL*12 > 12000;

-- OUTPUT:
NAME       MONTHLY SALARY ANNUAL SALARY
---------- -------------- -------------
ALLEN                1600         19200
WARD                 1250         15000
JONES                2975         35700
MARTIN               1250         15000
BLAKE                2850         34200
CLARK                2450         29400
SCOTT                3000         36000
KING                 5000         60000
TURNER               1500         18000
ADAMS                1100         13200
FORD                 3000         36000
MILLER               1300         15600

12 rows selected.
```
---

8. WAQTD THE EMPLOYEE NUMBER OF THE EMPLOYEES WHO ARE WORKING IN DEPT 30.
```SQL
SELECT EMPNO "EMPOLYEE NO" 
FROM EMP
WHERE DEPTNO = 30;

-- OUTPUT:
EMPOLYEE NO
-----------
       7499
       7521
       7654
       7698
       7844
       7900

6 rows selected.
```
---

9. WAQTD THE EMPLOYEE NAME AND HIRE DATE IF THEY WERE HIRED BEFORE THE YEAR 1981.
```SQL
SELECT ENAME NAME, HIREDATE  "HIRED BEFORE 1981" 
FROM EMP 
WHERE HIREDATE < '01-JAN-81';

-- OUTPUT:
NAME       HIRED BEF
---------- ---------
SMITH      17-DEC-80
```
---

10. WAQTD THE DETAILS OF THE EMPLOYEES WORKING AS MANAGER.
```SQL
SELECT * 
FROM EMP 
WHERE JOB = 'MANAGER';

-- OUTPUT:
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10
```
---
11. WAQTD THE NAME AND SALARY OF THE EMPLOYEE IF THE EMPLOYEE EARNS A COMMISSION OF 1400.
```SQL
SELECT ENAME NAME, SAL SALARY
FROM EMP
WHERE COMM = 1400;

-- OUTPUT:
NAME           SALARY
---------- ----------
MARTIN           1250
```
---

12. WAQTD THE DETAILS OF THE EMPLOYEES HAVING COMMISSION MORE THAN THEIR SALARY.
```SQL
SELECT *
FROM EMP
WHERE COMM > SAL;

-- OUTPUT:
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30
```
---
13. WAQTD THE EMPLOYEE NUMBERS OF THE EMPLOYEES HIRED BEFORE THE YEAR 1987.
```SQL
SELECT EMPNO "EMPLOYEE NO" 
FROM EMP
WHERE HIREDATE < '01-JAN-1987';

-- OUPUT:
EMPLOYEE NO
-----------
       7369
       7499
       7521
       7566
       7654
       7698
       7782
       7839
       7844
       7900
       7902
       7934
12 rows selected.
```

14. WAQTD THE DETAILS OF THE EMPLOYEES WORKING AS AN ANALYST.
```SQL
SELECT * 
FROM EMP 
WHERE JOB = 'ANALYST';

-- OUTPUT:
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20
```
---

15. WAQTD THE DETAILS OF THE EMPLOYEES EARNING MORE THAN 2000 PER MONTH.
```SQL
SELECT *
FROM EMP
WHERE SAL > 2000;

-- OUTPUT:
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20
      7839 KING       PRESIDENT            17-NOV-81       5000                    10
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20

6 rows selected.
```