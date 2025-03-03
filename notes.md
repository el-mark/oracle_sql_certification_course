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

code_for_combining_where_and_or_operators
