## 2. ASSIGNMENT ON EXPRESSION & ALIAS

1. WAQTD NAME OF THE EMPLOYEE ALONG WITH THEIR ANNUAL SALARY.
```SQL
SELECT ENAME AS "NAME" , SAL*12 AS "ANNUAL SALARY" 
FROM EMP;

-- OUTPUT:
NAME       ANNUAL SALARY
---------- -------------
SMITH               9600
ALLEN              19200
WARD               15000
JONES              35700
MARTIN             15000
BLAKE              34200
CLARK              29400
SCOTT              36000
KING               60000
TURNER             18000
ADAMS              13200
JAMES              11400
FORD               36000
MILLER             15600

14 rows selected.
```
---
2. WAQTD ENAME AND JOB FOR ALL THE EMPLOYEE ALONG WITH HALF TERM SALARY.
```SQL
SELECT ENAME AS NAME, JOB, SAL*6 AS "HALF-TERM SALARY"
FROM EMP;

-- OUTPUT:
NAME       JOB       HALF-TERM SALARY
---------- --------- ----------------
SMITH      CLERK                 4800
ALLEN      SALESMAN              9600
WARD       SALESMAN              7500
JONES      MANAGER              17850
MARTIN     SALESMAN              7500
BLAKE      MANAGER              17100
CLARK      MANAGER              14700
SCOTT      ANALYST              18000
KING       PRESIDENT            30000
TURNER     SALESMAN              9000
ADAMS      CLERK                 6600
JAMES      CLERK                 5700
FORD       ANALYST              18000
MILLER     CLERK                 7800

14 rows selected.
```
---
3. WAQTD ALL THE DETAILS OF THE EMPLOYEES ALONG WITH AN ANNUAL BONUS OF 2000.
```SQL
SELECT EMP.*, SAL*12 + 2000 AS "ANNUAL SALARY WITH 2000 BONUS" 
FROM EMP; 

-- OUTPUT:
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO ANNUAL SALARY WITH 2000 BONUS
---------- ---------- --------- ---------- --------- ---------- ---------- ---------- -----------------------------
      7369 SMITH      CLERK           7902 17-DEC-80        800                    20                         11600
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30                         21200
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30                         17000
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20                         37700
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30                         17000
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30                         36200
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10                         31400
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20                         38000
      7839 KING       PRESIDENT            17-NOV-81       5000                    10                         62000
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30                         20000
      7876 ADAMS      CLERK           7788 23-MAY-87       1100                    20                         15200
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30                         13400
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20                         38000
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10                         17600

14 rows selected.
```
---
4. WAQTD NAME, SALARY AND SALARY WITH A HIKE OF 10%
```SQL
SELECT ENAME AS NAME, SAL AS SALARY, SAL + SAL*0.1 AS "SALARY WITH 10% HIKE"
FROM EMP;

-- OUTPUT:
NAME           SALARY SALARY WITH 10% HIKE
---------- ---------- --------------------
SMITH             800                  880
ALLEN            1600                 1760
WARD             1250                 1375
JONES            2975               3272.5
MARTIN           1250                 1375
BLAKE            2850                 3135
CLARK            2450                 2695
SCOTT            3000                 3300
KING             5000                 5500
TURNER           1500                 1650
ADAMS            1100                 1210
JAMES             950                 1045
FORD             3000                 3300
MILLER           1300                 1430

14 rows selected.
```
---

5. WAQTD NAME AND SALARY WITH DEDUCTION OF 25%
```SQL
SELECT ENAME NAME, SAL-SAL*.25 "SALARY WITH 25% DEDUCTION"
FROM EMP;

-- OUTPUT:
NAME       SALARY WITH 25% DEDUCTION
---------- -------------------------
SMITH                            600
ALLEN                           1200
WARD                           937.5
JONES                        2231.25
MARTIN                         937.5
BLAKE                         2137.5
CLARK                         1837.5
SCOTT                           2250
KING                            3750
TURNER                          1125
ADAMS                            825
JAMES                          712.5
FORD                            2250
MILLER                           975

14 rows selected.
```
---

6. WAQTD NAME AND SALARY WITH MONTHLY HIKE OF 50.
```SQL
SELECT ENAME NAME, SAL + 50 "SALARY HIKE WITH 50"
FROM EMP;

-- OUTPUT:
NAME       SALARY HIKE WITH 50
---------- -------------------
SMITH                      850
ALLEN                     1650
WARD                      1300
JONES                     3025
MARTIN                    1300
BLAKE                     2900
CLARK                     2500
SCOTT                     3050
KING                      5050
TURNER                    1550
ADAMS                     1150
JAMES                     1000
FORD                      3050
MILLER                    1350

14 rows selected.
```
---

7. WAQTD NAME AND ANNUAL SALARY WITH DEDUCTION OF 10%.
```SQL
SELECT ENAME NAME, SAL*12 - SAL*0.1 "ANNUAL SALARY WITH 10% DEDUCTION"
FROM EMP;

-- OUTPUT:
NAME       ANNUAL SAL WITH 10% DEDUCTION
---------- -----------------------------
SMITH                               9520
ALLEN                              19040
WARD                               14875
JONES                            35402.5
MARTIN                             14875
BLAKE                              33915
CLARK                              29155
SCOTT                              35700
KING                               59500
TURNER                             17850
ADAMS                              13090
JAMES                              11305
FORD                               35700
MILLER                             15470

14 rows selected.
```
---
8. WAQTD TOTAL SALARY GIVEN TO EACH EMPLOYEE (SAL+COMM).
```SQL
SELECT SAL + COALESCE(COMM, 0) 
FROM EMP;

-- OR

SELECT SAL + NVL(COMM, 0) 
FROM  EMP;

-- OUTPUT:
SALARY WITH COMM
----------------
             800
            1900
            1750
            2975
            2650
            2850
            2450
            3000
            5000
            1500
            1100
             950
            3000
            1300

14 rows selected.
```
---
9. WAQTD DETAILS OF ALL THE EMPLOYEES ALONG WITH ANNUAL SALARY(INCLUDING COM).
```SQL
SELECT EMP.*, SAL*12 + NVL(COMM, 0) "ANNUAL SALARY" 
FROM EMP;

-- OUTPUT:
---------- ---------- --------- ---------- --------- ---------- ---------- ---------- -------------
      7369 SMITH      CLERK           7902 17-DEC-80        800                    20          9600
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30         19500
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30         15500
      7566 JONES      MANAGER         7839 02-APR-81       2975                    20         35700
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30         16400
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30         34200
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10         29400
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20         36000
      7839 KING       PRESIDENT            17-NOV-81       5000                    10         60000
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30         18000
      7876 ADAMS      CLERK           7788 23-MAY-87       1100                    20         13200
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30         11400
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20         36000
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10         15600

14 rows selected.
```
---
10. WAQTD NAME AND DESIGNATION ALONG WITH 100 PENALTY IN SALARY.
```SQL
SELECT ENAME NAME, JOB "DESIGNATION", SAL-100 "PENALISED SALARY" 
FROM EMP; 

-- OUTPUT:
NAME       DESIGNATI PENALISED SALARY
---------- --------- ----------------
SMITH      CLERK                  700
ALLEN      SALESMAN              1500
WARD       SALESMAN              1150
JONES      MANAGER               2875
MARTIN     SALESMAN              1150
BLAKE      MANAGER               2750
CLARK      MANAGER               2350
SCOTT      ANALYST               2900
KING       PRESIDENT             4900
TURNER     SALESMAN              1400
ADAMS      CLERK                 1000
JAMES      CLERK                  850
FORD       ANALYST               2900
MILLER     CLERK                 1200

14 rows selected.
```