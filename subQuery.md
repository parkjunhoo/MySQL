
MySQL에서 서브쿼리(subquery)란, SELECT, INSERT, UPDATE 또는 DELETE 문 안에 포함된 
또 다른 SELECT 문으로, 하나의 SQL 문 내에서 다른 SQL 문을 포함할 수 있는 기능입니다. 서브쿼리는 외부 쿼리와 연관되어 결과를 생성하는데 사용됩니다.

```sql
SELECT [컬럼명]
FROM [테이블명]
WHERE [컬럼명] [연산자] (SELECT [컬럼명] FROM [테이블명] WHERE [조건]);
```


수업시간 연습문제 :
3.각 부서(department_id)별로 최고 연봉(salary)를 받는 사원의 사번(employee_id), 성(last_name)과 연봉(salary)을 조회하시오. 단 조회결과는
연봉의 내림차순으로 정렬되어 나타나야 합니다.
```sql
select employee_id , last_name , salary , department_id
from employees e
where salary = (select max(salary) from employees where e.department_id = department_id group by department_id)
order by salary desc;
```
