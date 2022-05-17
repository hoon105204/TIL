# SUB QUERY

```mysql
-- SUB QUERY
-- 메인쿼리 안에 조건이나 검색을 위한 또 하나의 쿼리를 추가하는 방법

-- 단일 행 서브쿼리 : 결과 값이 1개 나오는 서브쿼리
-- 최소 급여를 받는 사원 정보 조회
select *
from employee e 
where SALARY = (select MIN(SALARY) 
				from EMPLOYEE); -- 결과가 단일행인 select구문을 값으로 이용

-- 다중 행 서브쿼리 : 결과값이 여러 줄 나오는 서브쿼리
-- 각 직급별 최소 급여 사원 정보 조회
select *
from employee e 
where SALARY in(select MIN(SALARY)
				from employee e 
				group by JOB_CODE); -- 결과가 다중행인 select구문을 값으로 이용

-- 다중행 다중열 서브쿼리
-- 여러 컬럼, 여러 로우의 결과를 가져오는 서브쿼리 사용
select *
from employee e 
where (JOB_CODE, SALARY) in (select JOB_CODE, MIN(SALARY)
							from EMPLOYEE
							group by JOB_CODE) -- 결과가 다중행, 다중열인 select구문을 값으로 이용
order by JOB_CODE;
```

**실습 코드**

```mysql
-- 실습 (단일열 서브쿼리 -> 다중열 서브쿼리)
-- 퇴사한 여직원과 같은 직급, 같은 부서에 근무하는 직원정보를 조회

-- 단일열 subQuery
select * from employee e 
where DEPT_CODE = (select DEPT_CODE from EMPLOYEE where ENT_YN = 'Y')
and JOB_CODE  = (select JOB_CODE from EMPLOYEE where ENT_YN = 'Y')
and EMP_ID <> (select EMP_ID from EMPLOYEE where ENT_YN = 'Y');

-- 다중열 subQuery
select * from employee e 
where (DEPT_CODE, JOB_CODE) = (select DEPT_CODE,JOB_CODE from EMPLOYEE where ENT_YN = 'Y')
and EMP_ID != (select EMP_ID from EMPLOYEE where ENT_YN = 'Y');
```

## Inline View(인라인 뷰)

```mysql
-- Inline View(인라인 뷰)
-- FROM 위치에 사용되는 서브쿼리
-- 테이블을 테이블 명으로 조회하는 대신
-- 서브쿼리의 restultSet을 활용하여 데이터 조회
select *
from (
	select EMP_ID, EMP_NAME, DEPT_TITLE, JOB_NAME, NATIONAL_NAME
	from employee e 
	join DEPARTMENT on(DEPT_CODE = DEPT_ID)
	join JOB USING(JOB_CODE)
	join LOCATION ON(LOCATION_ID = LOCAL_CODE)
	join national USING(NATIONAL_CODE)
	) T; -- 조회할 테이블 작성후 테이블 이름을 지정해야 함 (예제는 T로 지정)
```

