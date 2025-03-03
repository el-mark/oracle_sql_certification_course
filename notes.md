# SQL Commands
SQL in no case sensitive

## SELECT Clause
```SQL
select job from emp;
select distinct job from emp;*
```

*Distinct(not repeated rows)

## WHERE Clause
```SQL
select *
from emp
where job = 'MANAGER'
and sal >= 2850
and sal <= 2950;
```

## Operators
<, >, <=, >=, =, 1=

## WHERE, AND, OR
```SQL
select * from emp
where sal > 900
and job = 'CLERK'
or job = 'SALESMAN';

select ENAME from emp
where sal >= 2000
and job != 'MANAGER'
AND job != 'SALESMAN';

select ENAME, HIREDATE from emp
where DEPTNO = 20 or DEPTNO = 30;

select ENAME, HIREDATE from emp
join dept on emp.deptno = dept.deptno
where loc = 'CHICAGO' or loc = 'DALLAS';
```

## BETWEEN, IN and NULL
```SQL
select ENAME, HIREDATE from emp
where DEPTNO in (20, 30);

select ENAME, HIREDATE from emp
JOIN dept on emp.deptno = dept.deptno
where loc in ('CHICAGO', 'DALLAS');

select * from emp
where sal > 1300
and job not in ('CLERK', 'SALESMAN');

select * from emp
where sal between 1300 and 2000;

select * from emp
where hiredate not between '01/01/1981' and '12/09/1982';

select * from emp
where comm is null;

select * from emp
where comm is not null;

select * from emp
where comm is null
and (sal between 1100 and 5000)
and sal <> 3000;

select * from emp
where comm is null
and (sal > 1100 and sal < 5000)
and sal != 3000;
```

## Operator Precedence
```SQL
select * from emp
where (comm is null or comm = 0)
and (sal > 1100 and sal < 5000)
and sal != 3000;

select * from emp
where job = 'SALESMAN'
and (comm = 300 or comm > 1000);

select * from emp
where job like '%M%'
```

## Ordering Concatenating and Aliasing
```SQL
select ename "Employee Name", sal as Salary, comm Commission
from emp;

select 'Hello, my name is ' || ename as "Concatenated Value"
from emp;

select ename || ' makes $' || sal || ' per month'
as "Concatenated Salary"
from emp;

select ename, sal
from emp
order by ename;

select ename, sal
from emp
order by sal desc;
```
