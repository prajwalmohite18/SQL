## ASSIGNMENT ON CO-RELATED SUBQUERY

1. WAQTD NAME AND SALARY WHO IS EARNING 5TH MAXIMUM SALARY.
```SQL
SELECT OE.ENAME "NAME", OE.SAL "5TH MAX SALARY" 
FROM EMP OE
WHERE (SELECT COUNT(DISTINCT IE.SAL) 
            FROM EMP IE 
            WHERE IE.SAL > OE.SAL
    ) = 4;

-- OUTPUT
NAME       5TH MAX SALARY
---------- --------------
CLARK                2850
```
---
2. WAQTD DETAILS OF THE EMP WHO IS EARNING 4TH MINIMUM SALARY.
```SQL
SELECT OE.*
FROM EMP OE 
WHERE (SELECT COUNT(DISTINCT IE.SAL) 
            FROM EMP IE 
            WHERE IE.SAL < OE.SAL
       ) = 3;

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30
```
---
3. WAQTD DETAILS OF THE EMP WHO ARE EARNING TOP 5 MINIMUM SALARIES.
```SQL
SELECT OE.*
FROM EMP OE
WHERE (SELECT COUNT(DISTINCT IE.SAL) 
            FROM EMP IE 
            WHERE IE.SAL < OE.SAL
       ) <= 4;

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7369 SMITH      CLERK           7902 17-DEC-80        800                    20
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30
      7876 ADAMS      CLERK           7788 23-MAY-87       1100                    20
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10

6 rows selected.
```
---
4. WAQTD NAME AND SALARY OF THE EMP WHO ARE EARNING TOP 3 MINIMUM & TOP 3 MAXIMUM SALARIES.
```SQL
SELECT OE.ENAME NAME, OE.SAL SALARY
FROM EMP OE
WHERE (SELECT COUNT(DISTINCT IE1.SAL) 
            FROM EMP IE1 
            WHERE IE1.SAL < OE.SAL) <= 2
OR (SELECT COUNT(DISTINCT IE2.SAL) 
        FROM EMP IE2 
        WHERE IE2.SAL > OE.SAL) <= 2
ORDER BY SAL;

-- OUTPUT
NAME           SALARY
---------- ----------
SMITH             800
JAMES             950
ADAMS            1100
JONES            2975
SCOTT            3000
FORD             3000
KING             5000

7 rows selected.
```
---
5. WAQTD 1ST , 2ND , 4TH , 6TH , 7TH MAXIMUM SALARIES.
```SQL
SELECT DISTINCT SAL "1ST, 2ND, 4TH, 6TH, 7TH SALARY"
FROM EMP OE
WHERE (SELECT COUNT(DISTINCT IE.SAL) FROM EMP IE WHERE IE.SAL > OE.SAL) = 0
OR (SELECT COUNT(DISTINCT IE.SAL) FROM EMP IE WHERE IE.SAL > OE.SAL) = 1
OR (SELECT COUNT(DISTINCT IE.SAL) FROM EMP IE WHERE IE.SAL > OE.SAL) = 3
OR (SELECT COUNT(DISTINCT IE.SAL) FROM EMP IE WHERE IE.SAL > OE.SAL) = 5
OR (SELECT COUNT(DISTINCT IE.SAL) FROM EMP IE WHERE IE.SAL > OE.SAL) = 6
ORDER BY SAL DESC; 

-- OUTPUT
1ST, 2ND, 4TH, 6TH, 7TH SALARY
------------------------------
                          5000
                          3000
                          2850
                          1600
                          1500

```
---
6. WAQTD THE SALARY OF EMP WHO ARE EARNING TOP 3 MAXIMUM SALARIES.
```SQL
SELECT DISTINCT OE.SAL "TOP 3 SALARY"
FROM EMP OE
WHERE (SELECT COUNT(DISTINCT IE.SAL) 
            FROM EMP IE 
            WHERE IE.SAL > OE.SAL) <=2
ORDER BY SAL DESC;

-- OUTPUT
TOP 3 SALARY
------------
        5000
        3000
        2975
```
---
7. WAQTD 2,6 MAXIMUM SALARIES AND 8,4 MINIMUM SALARIES.
```SQL
SELECT * 
FROM(
        SELECT DISTINCT OE.SAL "2, 6 MAX SAL AND 8, 4 MIN SAL"
        FROM EMP OE
        WHERE (SELECT COUNT(DISTINCT IE.SAL) 
                    FROM EMP IE 
                    WHERE IE.SAL > OE.SAL) IN (1,5) 
        ORDER BY SAL DESC
    )
UNION ALL
SELECT *
FROM(
        SELECT DISTINCT OE.SAL 
        FROM EMP OE
        WHERE (SELECT COUNT(DISTINCT IE.SAL) 
                    FROM EMP IE 
                    WHERE IE.SAL < OE.SAL) IN (7,3) 
    );

-- OUTPUT
2, 6 MAX SAL AND 8, 4 MIN SAL
-----------------------------
                         3000
                         1600
                         2450
                         1250
```
---
8. WAQTD 16TH MAXIMUM SALARY.
```SQL
SELECT OE.SAL
FROM EMP OE
WHERE (SELECT COUNT(DISTINCT SAL) 
            FROM EMP IE 
            WHERE IE.SAL > OE.SAL
      ) = 15;

-- OUTPUT
no rows selected
```
---
9. WAQTD FIRST MAXIMUM SALARY AND FIRST MINIMUM SALARY.
```SQL
SELECT OE.SAL
FROM EMP OE
WHERE (SELECT COUNT(DISTINCT IE.SAL) 
            FROM EMP IE 
            WHERE IE.SAL > OE.SAL
      ) = 0
OR (SELECT COUNT(DISTINCT IE.SAL) 
        FROM EMP IE 
        WHERE IE.SAL < OE.SAL
    ) = 0;

-- OUTPUT
       SAL
----------
       800
      5000
```
---