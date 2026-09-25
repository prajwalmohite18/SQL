## ASSIGNMENT ON SUB-QUERY CASE1

1. WAQTD THE NAME OF EMPLOYEES EARNING MORE THAN 'ADAMS'.
```SQL
SELECT ENAME "NAME"
FROM EMP
WHERE SAL > (SELECT SAL 
            FROM EMP 
            WHERE ENAME = 'ADAMS' )

-- OUTPUT
NAME
----------
ALLEN
WARD
JONES
MARTIN
BLAKE
CLARK
SCOTT
KING
TURNER
FORD
MILLER

11 ROWS SELECTED.
```
---
2. WAQTD NAME AND SALARY OF THE EMPLOYEES LESS THAN 'KING'.
```SQL
SELECT ENAME NAME, SAL SALARY
FROM EMP
WHERE SAL < (SELECT SAL 
            FROM EMP 
            WHERE ENAME = 'KING');

-- OUTPUT
AME           SALARY
---------- ----------
SMITH             800
ALLEN            1600
WARD             1250
JONES            2975
MARTIN           1250
BLAKE            2850
CLARK            2450
SCOTT            3000
TURNER           1500
ADAMS            1100
JAMES             950
FORD             3000
MILLER           1300

13 ROWS SELECTED.
```
---
3. WAQTD NAME AND DEPTNO OF THE EMPLOYEES IF THEY ARE WORKING IN THE SAME DEPARTMENT AS 'JONES'.
```SQL
SELECT ENAME NAME, DEPTNO
FROM EMP
WHERE DEPTNO = (SELECT DEPTNO 
                    FROM EMP 
                    WHERE ENAME = 'JONES');

-- OUTPUT
NAME           DEPTNO
---------- ----------
SMITH              20
JONES              20
SCOTT              20
ADAMS              20
FORD               20

-- OR (WITHOUT DISPLAYING JONES NAME)
SELECT ENAME NAME, DEPTNO
FROM EMP
WHERE DEPTNO = (SELECT DEPTNO 
                    FROM EMP 
                    WHERE ENAME = 'JONES')
AND ENAME <> 'JONES';
NAME           DEPTNO
---------- ----------
SMITH              20
SCOTT              20
ADAMS              20
FORD               20
```
---
4. WQTD NAME AND JOB OF ALL THE EMPLOYEES WORKING IN THE SAME DESIGNATION AS 'JAMES'.
```SQL
SELECT ENAME NAME, JOB
FROM EMP
WHERE JOB = (SELECT JOB
                FROM EMP
                WHERE ENAME = 'JAMES');

-- OUTPUT
NAME       JOB
---------- ---------
SMITH      CLERK
ADAMS      CLERK
JAMES      CLERK
MILLER     CLERK
```
---
5. WAQTD EMPLOYEE NO AND NAME ALONG WITH ANNUAL SALARY OF ALL THE EMPLOYEES IF THEIR ANNUAL SALARY IS GREATER THAN WARD'S ANNUAL SALARY.
```SQL
SELECT EMPNO "EMPLOYEE NO", ENAME NAME, (SAL*12) "ANNUAL SALARY"
FROM EMP
WHERE (SAL*12) > (SELECT (SAL*12)
                    FROM EMP
                    WHERE ENAME = 'WARD');

-- OUTPUT
EMPLOYEE NO NAME       ANNUAL SALARY
----------- ---------- -------------
       7499 ALLEN              19200
       7566 JONES              35700
       7698 BLAKE              34200
       7782 CLARK              29400
       7788 SCOTT              36000
       7839 KING               60000
       7844 TURNER             18000
       7902 FORD               36000
       7934 MILLER             15600

9 ROWS SELECTED.
```                
---
6. WAQTD NAME AND HIREDATE OF THE EMPLOYEES IF THEY ARE HIRED BEFORE SCOTT.
```SQL
SELECT ENAME NAME, HIREDATE 
FROM EMP
WHERE HIREDATE < (SELECT HIREDATE
                    FROM EMP
                    WHERE ENAME = 'SCOTT');

-- OUTPUT
NAME       HIREDATE
---------- ---------
SMITH      17-DEC-80
ALLEN      20-FEB-81
WARD       22-FEB-81
JONES      02-APR-81
MARTIN     28-SEP-81
BLAKE      01-MAY-81
CLARK      09-JUN-81
KING       17-NOV-81
TURNER     08-SEP-81
JAMES      03-DEC-81
FORD       03-DEC-81
MILLER     23-JAN-82

12 ROWS SELECTED.
```
---
7. WAQTD NAME AND HIREDATE OF THE EMPLOYEES IF THEY ARE HIRED AFTER 'PRESIDENT'.
```SQL
SELECT ENAME, HIREDATE 
FROM EMP 
WHERE HIREDATE < (SELECT HIREDATE 
                    FROM EMP 
                    WHERE JOB = 'PRESIDENT');

-- OUTPUT
ENAME      HIREDATE
---------- ---------
SMITH      17-DEC-80
ALLEN      20-FEB-81
WARD       22-FEB-81
JONES      02-APR-81
MARTIN     28-SEP-81
BLAKE      01-MAY-81
CLARK      09-JUN-81
TURNER     08-SEP-81

8 ROWS SELECTED.
```
---
8. WAQTD NAME AND SALARY OF THE EMPLOYEE IF THEY ARE EARNING SALARY LESS THAN THE EMPLOYEE WHOSE EMPNO IS 7876.
```SQL
SELECT ENAME, SAL "SALARY" 
FROM EMP
WHERE SAL < (SELECT SAL 
                FROM EMP
                WHERE EMPNO = '7876');

-- OUTPUT
ENAME          SALARY
---------- ----------
SMITH             800
JAMES             950
```
---
9. WAQTD ALL THE DETAILS OF EMPLOYEES IF THE EMPLOYEES ARE HIRED BEFORE 'MILLER'.
```SQL
SELECT *
FROM EMP 
WHERE HIREDATE < (SELECT HIREDATE 
                    FROM EMP
                    WHERE ENAME = 'MILLER');
    
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
      7839 KING       PRESIDENT            17-NOV-81       5000                    10
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20

11 ROWS SELECTED.
```
---
10. WAQTD NAME AND EMPNO OF THE EMPLOYEE IF EMPLOYEES ARE EARNING MORE THAN 'ALLEN';
```SQL
SELECT ENAME NAME, EMPNO "EMPLOYEE NO" 
FROM EMP
WHERE SAL > (SELECT SAL 
                FROM EMP 
                WHERE ENAME = 'ALLEN');

-- OUTPUT
NAME       EMPLOYEE NO
---------- -----------
JONES             7566
BLAKE             7698
CLARK             7782
SCOTT             7788
KING              7839
FORD              7902
```
---
11. WAQTD NAME AND SALARY OF ALL THE EMPLOYEES WHO ARE EARNING MORE THAN 'MILLER' BUT LESS THAN 'ALLEN'.
```SQL
SELECT ENAME NAME, SAL "SALARY"
FROM EMP
WHERE SAL > (SELECT SAL 
                        FROM EMP 
                        WHERE ENAME = 'MILLER') 
AND SAL < (SELECT SAL 
      FROM EMP 
      WHERE ENAME = 'ALLEN');

-- OUTPUT
NAME           SALARY
---------- ----------
TURNER           1500
```
---
12. WAQTD ALL THE DETAILS OF THE EMPLOYEES WORKING IN DEPARTMENT 20 AND WORKING IN THE SAME DESIGNATION AS 'SMITH'.
```SQL
SELECT * 
FROM EMP
WHERE DEPTNO = 20 AND JOB = (SELECT JOB 
                              FROM EMP
                              WHERE ENAME = 'SMITH');

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7369 SMITH      CLERK           7902 17-DEC-80        800                    20
      7876 ADAMS      CLERK           7788 23-MAY-87       1100                    20

-- OR 
-- THIS QUERY WILL GIVE DETAILS BY EXCLUDING SMITH
SELECT * 
FROM EMP
WHERE DEPTNO = 20 
AND JOB = (SELECT JOB 
            FROM EMP
            WHERE ENAME = 'SMITH')
AND ENAME <> 'SMITH';
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7876 ADAMS      CLERK           7788 23-MAY-87       1100                    20

```
---
13. WAQTD ALL THE DETAILS OF THE EMPLOYEES WORKING AS MANAGER IN THE SAME DEPARTMENT AS 'TURNER'.
```SQL
SELECT *
FROM EMP
WHERE JOB = 'MANAGER' 
AND DEPTNO = (SELECT DEPTNO 
                  FROM EMP
                  WHERE ENAME = 'TURNER');

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
```
---
14. WAQTD NAME AND HIREDATE OF THE EMPLOYEES HIRED AFTER 1980 AND BEFORE KING.
```SQL
SELECT ENAME NAME, HIREDATE 
FROM EMP
WHERE HIREDATE > '31-DEC-1980' 
AND HIREDATE < (SELECT HIREDATE 
                  FROM EMP 
                  WHERE ENAME = 'KING');

-- OUTPUT
NAME       HIREDATE
---------- ---------
ALLEN      20-FEB-81
WARD       22-FEB-81
JONES      02-APR-81
MARTIN     28-SEP-81
BLAKE      01-MAY-81
CLARK      09-JUN-81
TURNER     08-SEP-81

7 rows selected.
```
---
15. WAQTD NAME AND SAL ALONG WITH ANNUAL SAL FOR ALL EMPLOYEES WHOS SAL IS LESS THAN BLAKE AND MORE THAN 3500.
```SQL
SELECT ENAME NAME, SAL SALARY, (SAL*12) "ANNUAL SALARY"
FROM EMP
WHERE SAL < (SELECT SAL 
                  FROM EMP
                  WHERE ENAME = 'BLAKE')
AND SAL >  3500;

-- OUTPUT
no rows selected
```
---
16. WAQTD ALL THE DETAILS OF EMPLOYEES WHO EARN MORE THAN SCOTT BUT LESS THAN KING.
```SQL
SELECT *
FROM EMP
WHERE SAL > (SELECT SAL 
                  FROM EMP 
                  WHERE ENAME = 'SCOTT') 
AND SAL < (SELECT SAL 
                  FROM EMP 
                  WHERE ENAME = 'KING');

-- OUTPUT
no rows selected
```
---
17. WAQTD NAME OF THE EMPLOYEES WHOSE NAME STARTS WITH 'A' AND WORKS IN THE SAME DEPT AS BLAKE.
```SQL
SELECT ENAME NAME
FROM EMP
WHERE ENAME LIKE 'A%' 
AND DEPTNO = (SELECT DEPTNO 
                  FROM EMP
                  WHERE ENAME = 'BLAKE');

-- OUTPUT
NAME
----------
ALLEN
```
---
18. WAQTD NAME AND COMM IF EMPLOYEES EARN COMISSION AND WORK IN THE SAME DESIGNATION AS SMITH.
```SQL
SELECT ENAME NAME, COMM COMMISSION
FROM EMP
WHERE COMM IS NOT NULL
AND JOB = (SELECT JOB 
            FROM EMP 
            WHERE ENAME = 'SMITH');

-- OUTPUT
no rows selected
```
---
19. WAQTD DETAILS OF ALL THE EMPLOYEES WORKING AS CLERK IN THE SAME DEPT AS TURNER.
```SQL
SELECT * 
FROM EMP
WHERE JOB = 'CLERK'
AND DEPTNO = (SELECT DEPTNO 
                  FROM EMP
                  WHERE ENAME = 'TURNER');

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30
```
---
20. WAQTD ENAME, SAL AND DESIGNATION OF THE EMPLOYEES WHOSE ANNUAL SALARY IS MORE THAN SMITH AND LESS THAN KING.
```SQL
SELECT ENAME NAME, SAL SALARY, JOB 
FROM EMP
WHERE (SAL*12) > (SELECT (SAL*12) 
                        FROM EMP
                        WHERE ENAME = 'SMITH')
AND (SAL*12) < (SELECT (SAL*12) 
                        FROM EMP
                        WHERE ENAME = 'KING');

-- OUTPUT
NAME           SALARY JOB
---------- ---------- ---------
ALLEN            1600 SALESMAN
WARD             1250 SALESMAN
JONES            2975 MANAGER
MARTIN           1250 SALESMAN
BLAKE            2850 MANAGER
CLARK            2450 MANAGER
SCOTT            3000 ANALYST
TURNER           1500 SALESMAN
ADAMS            1100 CLERK
JAMES             950 CLERK
FORD             3000 ANALYST
MILLER           1300 CLERK

12 rows selected.
```
---