## ASSIGNMENT ON LOGICAL OPERATOR

**LOGICAL OPERATORS**
-  AND
- OR 
- NOT


1. WAQTD DETAILS OF THE EMPLOYEES WORKING AS CLERK AND EARNING LESS THAN 1500.
```SQL
-- USED AND OPERATOR
SELECT EMP.*
FROM EMP 
WHERE JOB = 'CLERK'
AND SAL < 1500;

# OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7369 SMITH      CLERK           7902 17-DEC-80        800                    20
      7876 ADAMS      CLERK           7788 23-MAY-87       1100                    20
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10

```
---
2. WAQTD NAME AND HIREDATE OF THE EMPLOYEES WORKING AS MANAGER IN DEPT 30.
```SQL
SELECT ENAME NAME, HIREDATE
FROM EMP 
WHERE JOB = 'MANAGER'
AND DEPTNO = 30;

-- OUTPUT
NAME       HIREDATE
---------- ---------
BLAKE      01-MAY-81
```
---
3. WAQTD DETAILS OF THE EMP ALONG WITH ANNUAL SALARY IF THEY ARE WORKING IN DEPT 30 AS SALESMAN AND THEIR ANNUAL SALARY HAS TO BE GREATER THAN 14000.
```SQL
SELECT EMP.*, (SAL*12) "ANNUAL SALARY"
FROM EMP
WHERE DEPTNO  = 30
AND JOB = 'SALESMAN'
AND (SAL*12) > 14000;

-- OUTPUT
    EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO ANNUAL SALARY
---------- ---------- --------- ---------- --------- ---------- ---------- ---------- -------------
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30         19200
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30         15000
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30         15000
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30         18000
```
---
4. WAQTD ALL THE DETAILS OF THE EMP WORKING IN DEPT 30 OR AS ANALYST.
```SQL
-- USED OR OPERATOR
SELECT EMP.*
FROM EMP
WHERE DEPTNO = 30 
OR JOB = 'ANALYST';

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20

8 rows selected.
```
---
5. WAQTD NAMES OF THE EMPLOYEES WHOSE SALARY IS LESS THAN 1100 AND THEIR DESIGNATION IS CLERK.
```SQL
SELECT ENAME NAME
FROM EMP
WHERE SAL < 1100
AND JOB = 'CLERK';

-- OUTPUT
NAME
----------
SMITH
JAMES
```
---
6. WAQTD NAME AND SAL, ANNUAL SAL AND DEPTNO IF DEPTNO IS 20 EARNING MORE THAN 1100 AND ANNUAL SALARY EXCEEDS 12000.
```SQL
SELECT ENAME NAME, SAL "MONTHLY SALARY", (SAL*12) "ANNUAL SALARY", DEPTNO "DEPT NO"
FROM EMP 
WHERE DEPTNO = 20
AND SAL > 1100
AND (SAL*12) > 12000;

-- OUTPUT
NAME       MONTHLY SALARY ANNUAL SALARY    DEPT NO
---------- -------------- ------------- ----------
JONES                2975         35700         20
SCOTT                3000         36000         20
FORD                 3000         36000         20
```
---
7. WAQTD EMPNO AND NAMES OF THE EMPLOYEES WORKING AS MANAGER IN DEPT 20.
```SQL
SELECT EMPNO "EMP NO", ENAME "NAME"
FROM EMP
WHERE JOB = 'MANAGER'
AND DEPTNO = 20;

-- OUTPUT
    EMP NO NAME
---------- ----------
      7566 JONES
```
---
8. WAQTD DETAILS OF EMPLOYEES WORKING IN DEPT 20 OR 30.
```SQL
SELECT * 
FROM EMP
WHERE DEPTNO = 20 OR DEPTNO = 30;

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7369 SMITH      CLERK           7902 17-DEC-80        800                    20
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30
      7876 ADAMS      CLERK           7788 23-MAY-87       1100                    20
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20

11 rows selected.
```
---
9. WAQTD DETAILS OF EMPLOYEES WORKING AS ANALYST IN DEPT 20.
```SQL
SELECT * 
FROM EMP 
WHERE JOB = 'ANALYST'
AND DEPTNO = 20;

-- OUTPUT

     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20
```
---
10.  WAQTD DETAILS OF EMPLOYEE WORKING AS PRESIDENT WITH SALARY OF RUPEES 4000.
```SQL
SELECT *
FROM EMP 
WHERE JOB = 'PRESIDENT' AND SAL = 4000;

-- OUTPUT
no rows selected
```
---
11. WAQTD NAMES AND DEPTNO , JOB OF EMPS WORKING AS CLERK IN DEPT 10 OR 20.
```SQL
SELECT ENAME NAME, DEPTNO "DEPT NO", JOB
FROM EMP
WHERE JOB = 'CLERK' AND (DEPTNO = 10 OR DEPTNO = 20);

-- OUTPUT
NAME          DEPT NO JOB
---------- ---------- ---------
SMITH              20 CLERK
ADAMS              20 CLERK
MILLER             10 CLERK
```
---
12. WAQTD DETAILS OF EMPLOYEES WORKING AS CLERK OR MANAGER IN DEPT 10.
```SQL
SELECT *
FROM EMP
WHERE (JOB = 'CLERK' OR JOB = 'MANAGER') AND DEPTNO = 10;

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10
```
---
13. WAQTD NAMES OF EMPLOYEES WORKING IN DEPT 10 , 20 , 30 , 40.
```SQL
SELECT ENAME NAME
FROM EMP
WHERE DEPTNO = 10 OR DEPTNO = 20 OR DEPTNO = 30 OR DEPTNO = 40;

-- OUTPUT
NAME
----------
SMITH
ALLEN
WARD
JONES
MARTIN
BLAKE
CLARK
SCOTT
KING
TURNER
ADAMS
JAMES
FORD
MILLER

14 rows selected.
```
---
14.  WAQTD DETAILS OF EMPLOYEES WITH EMPNO 7902, 7839.
```SQL
SELECT *
FROM EMP
WHERE EMPNO = 7902 OR EMPNO = 7839;

-- OUTPUT

     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7839 KING       PRESIDENT            17-NOV-81       5000                    10
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20
```
---
15. WAQTD DETAILS OF EMPLOYEES WORKING AS MANAGER OR SALESMAN OR CLERK.
```SQL
SELECT *
FROM EMP
WHERE JOB = 'SALESMAN' OR JOB = 'MANAGER' OR JOB = 'CLERK';

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7369 SMITH      CLERK           7902 17-DEC-80        800                    20
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30
      7876 ADAMS      CLERK           7788 23-MAY-87       1100                    20
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10

11 rows selected.
```
---
16. WAQTD NAMES OF EMPLOYEES HIRED AFTER 81 AND BEFORE 87.
```SQL
SELECT ENAME NAME
FROM EMP
WHERE HIREDATE > '31-DEC-81' AND HIREDATE < '01-JAN-87';

-- OUTPUT
NAME
----------
MILLER
```
---
17. WAQTD DETAILS OF EMPLOYEES EARNING MORE THAN 1250 BUT LESS THAN 3000.
```SQL
SELECT *
FROM EMP
WHERE SAL > 1250 AND SAL < 3000;

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10

6 rows selected.
```
---
18. WAQTD NAMES OF EMPLOYEES HIRED AFTER 81 INTO DEPT 10 OR 30.
```SQL
SELECT ENAME NAME
FROM EMP
WHERE HIREDATE > '31-DEC-1981' AND (DEPTNO = 10 OR DEPTNO = 30);

-- OUTPUT 
SQL> SELECT ENAME NAME
  2  FROM EMP
  3  WHERE HIREDATE > '31-DEC-1981' AND (DEPTNO = 10 OR DEPTNO = 30);

NAME
----------
MILLER
```
---
19. WAQTD NAMES OF EMPLOYEES ALONG WITH ANNUAL SALARY FOR THE EMPLOYEES WORKING AS MANAGER OR CLERK INTO DEPT 10 OR 30.
```SQL
SELECT ENAME NAME, (SAL*12) "ANNUAL SALARY"
FROM EMP
WHERE (JOB = 'MANAGER' OR JOB = 'CLERK') AND (DEPTNO = 10 OR DEPTNO = 30);

-- OUTPUT
NAME       ANNUAL SALARY
---------- -------------
BLAKE              34200
CLARK              29400
JAMES              11400
MILLER             15600
```
---
20. WAQTD ALL THE DETAILS ALONG WITH ANNUAL SALARY IF SAL IS BETWEEN 1000 AND 4000 ANNUAL SALARY MORE THAN 15000.
```SQL
SELECT EMP.*, (SAL*12) "ANNUAL SALARY" 
FROM EMP
WHERE SAL > 1000 AND SAL < 4000 AND (SAL*12) > 15000;

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO ANNUAL SALARY
---------- ---------- --------- ---------- --------- ---------- ---------- ---------- -------------
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30         19200
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20         35700
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30         34200
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10         29400
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20         36000
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30         18000
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20         36000
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10         15600

8 rows selected.
```
---