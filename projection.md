## SQL QUEIRES ON PROJECTION
**(ORACLE SCOTT DB - EMP & DEPT TABLE):**

1. WAQTD ALL THE DETAILS FROM THE EMPLOYEE TABLE.
```sql
SELECT * FROM EMP;

-- OUTPUT:
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7369 SMITH      CLERK           7902 17-DEC-80        800                    20
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

14 rows selected.
```
---
2. WAQTD NAMES OF ALL THE EMPLOYEES.
```SQL
SELECT ENAME 
FROM EMP;

-- OUTPUT:
ENAME
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

3. WAQTD NAME AND SALARY GIVEN TO ALL THE EMPLOYEES.
```SQL
SELECT ENAME, SAL FROM EMP;

-- OUTPUT
SQL> SELECT ENAME, SAL FROM EMP;

ENAME             SAL
---------- ----------
SMITH             800
ALLEN            1600
WARD             1250
JONES            2975
MARTIN           1250
BLAKE            2850
CLARK            2450
SCOTT            3000
KING             5000
TURNER           1500
ADAMS            1100
JAMES             950
FORD             3000
MILLER           1300

14 rows selected.
```
---
4. WAQTD NAME AND COMMISSION GIVEN TO ALL THE EMPLOYEES.
```SQL
SELECT ENAME, COMM 
FROM EMP;
-- OUTPUT
ENAME            COMM
---------- ----------
SMITH
ALLEN             300
WARD              500
JONES
MARTIN           1400
BLAKE
CLARK
SCOTT
KING
TURNER              0
ADAMS
JAMES
FORD
MILLER

14 rows selected. 
```
---
5. WAQTD EMPLOYEE ID AND DEPARTMENT NUMBER OF ALL THE EMPLOYEES IN EMP TABLE.
```SQL
SELECT EMPNO, DEPTNO 
FROM EMP;

-- OUTPUT:
     EMPNO     DEPTNO
---------- ----------
      7369         20
      7499         30
      7521         30
      7566         20
      7654         30
      7698         30
      7782         10
      7788         20
      7839         10
      7844         30
      7876         20
      7900         30
      7902         20
      7934         10

14 rows selected.
```
---
6. WAQTD ENAME AND HIREDATE OF ALL THE EMPLOYEES.
```SQL
SELECT ENAME, HIREDATE 
FROM EMP;

-- OUTPUT:
SQL> SELECT ENAME, HIREDATE FROM EMP;

ENAME      HIREDATE
---------- ---------
SMITH      17-DEC-80
ALLEN      20-FEB-81
WARD       22-FEB-81
JONES      02-APR-81
MARTIN     28-SEP-81
BLAKE      01-MAY-81
CLARK      09-JUN-81
SCOTT      19-APR-87
KING       17-NOV-81
TURNER     08-SEP-81
ADAMS      23-MAY-87
JAMES      03-DEC-81
FORD       03-DEC-81
MILLER     23-JAN-82

14 rows selected.
```
---
7. WAQTD NAME AND DESIGNATION OF ALL THE EMPLPOYEES.
```SQL
SELECT ENAME, JOB 
FROM EMP;

-- OUTPUT:
ENAME      JOB
---------- ---------
SMITH      CLERK
ALLEN      SALESMAN
WARD       SALESMAN
JONES      MANAGER
MARTIN     SALESMAN
BLAKE      MANAGER
CLARK      MANAGER
SCOTT      ANALYST
KING       PRESIDENT
TURNER     SALESMAN
ADAMS      CLERK
JAMES      CLERK
FORD       ANALYST
MILLER     CLERK

14 rows selected.
```
---
8. WAQTD NAME, JOB AND SALARY GIVEN ALL THE EMPLOYEES.
```SQL
SELECT ENAME, JOB, SAL 
FROM EMP;

-- OUTPUT:
ENAME      JOB              SAL
---------- --------- ----------
SMITH      CLERK            800
ALLEN      SALESMAN        1600
WARD       SALESMAN        1250
JONES      MANAGER         2975
MARTIN     SALESMAN        1250
BLAKE      MANAGER         2850
CLARK      MANAGER         2450
SCOTT      ANALYST         3000
KING       PRESIDENT       5000
TURNER     SALESMAN        1500
ADAMS      CLERK           1100
JAMES      CLERK            950
FORD       ANALYST         3000
MILLER     CLERK           1300

14 rows selected.
```
---
9. WAQTD DNAMES PRESENT IN DEPARTMENT TABLE.
```SQL
SELECT DNAME FROM DEPT;

-- OUTPUT:
DNAME
--------------
ACCOUNTING
RESEARCH
SALES
OPERATIONS
```
---
10. WAQTD DNAME AND LOCATION PRESENT IN DEPT TABLE.
```SQL
SELECT DNAME, LOC 
FROM DEPT;

-- OUTPUT:
DNAME          LOC
-------------- -------------
ACCOUNTING     NEW YORK
RESEARCH       DALLAS
SALES          CHICAGO
OPERATIONS     BOSTON
```
---
11. WAQTD ALL THE DETAILS ALONG WITH EMPLOYEE_NAME.
```SQL
SELECT EMP.*, ENAME 
FROM EMP;

-- OUTPUT:
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO ENAME
---------- ---------- --------- ---------- --------- ---------- ---------- ---------- ----------
      7369 SMITH      CLERK           7902 17-DEC-80        800                    20 SMITH
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30 ALLEN
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30 WARD
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20 JONES
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30 MARTIN
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30 BLAKE
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10 CLARK
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20 SCOTT
      7839 KING       PRESIDENT            17-NOV-81       5000                    10 KING
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30 TURNER
      7876 ADAMS      CLERK           7788 23-MAY-87       1100                    20 ADAMS
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30 JAMES
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20 FORD
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10 MILLER

14 rows selected.
```
---
12. WAQTD ALL THE DETAILS ALONG WITH MANAGER, JOB, SALARY.
```SQL
SELECT EMP.*, MGR, JOB, SAL 
FROM EMP;

-- OUTPUT:
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO        MGR JOB              SAL
---------- ---------- --------- ---------- --------- ---------- ---------- ---------- ---------- --------- ----------
      7369 SMITH      CLERK           7902 17-DEC-80        800                    20       7902 CLERK            800
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30       7698 SALESMAN        1600
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30       7698 SALESMAN        1250
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20       7839 MANAGER         2975
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30       7698 SALESMAN        1250
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30       7839 MANAGER         2850
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10       7839 MANAGER         2450
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20       7566 ANALYST         3000
      7839 KING       PRESIDENT            17-NOV-81       5000                    10            PRESIDENT       5000
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30       7698 SALESMAN        1500
      7876 ADAMS      CLERK           7788 23-MAY-87       1100                    20       7788 CLERK           1100
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30       7698 CLERK            950
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20       7566 ANALYST         3000
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10       7782 CLERK           1300

14 rows selected.
```
---
13. WAQTD ALL THE DETAILS ALONG WITH DEPARTMENT NAMES.
```SQL
SELECT DEPT.*, DNAME FROM DEPT;

-- OUTPUT:
    DEPTNO DNAME          LOC           DNAME
---------- -------------- ------------- --------------
        10 ACCOUNTING     NEW YORK      ACCOUNTING
        20 RESEARCH       DALLAS        RESEARCH
        30 SALES          CHICAGO       SALES
        40 OPERATIONS     BOSTON        OPERATIONS
```
---
14. WAQTD NAMES, MANAGER_ID, JOB AND COMMISION OF EMPLOYEES.
```SQL 
SELECT ENAME, MGR, JOB, COMM 
FROM EMP;

-- OUTPUT
ENAME             MGR JOB             COMM
---------- ---------- --------- ----------
SMITH            7902 CLERK
ALLEN            7698 SALESMAN         300
WARD             7698 SALESMAN         500
JONES            7839 MANAGER
MARTIN           7698 SALESMAN        1400
BLAKE            7839 MANAGER
CLARK            7839 MANAGER
SCOTT            7566 ANALYST
KING                  PRESIDENT
TURNER           7698 SALESMAN           0
ADAMS            7788 CLERK
JAMES            7698 CLERK
FORD             7566 ANALYST
MILLER           7782 CLERK

14 rows selected.
```
---
15. WAQTD JOB, SALARY, COMMISION, NAMES OF EMPLOYEES.
```SQL
SELECT JOB, SAL, COMM 
FROM EMP;
JOB              SAL       COMM
--------- ---------- ----------
CLERK            800
SALESMAN        1600        300
SALESMAN        1250        500
MANAGER         2975
SALESMAN        1250       1400
MANAGER         2850
MANAGER         2450
ANALYST         3000
PRESIDENT       5000
SALESMAN        1500          0
CLERK           1100
CLERK            950
ANALYST         3000
CLERK           1300

14 rows selected.
```