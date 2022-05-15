# SELECT
**SELCET 문의 실행 순서**

```
-- 5: SELECT 컬럼, 계산식, 함수식 AS 별칭, ...
-- 1: FROM 테이블명
-- 2: WHERE 조건
-- 3: GROUP BY 그룹 묶을 컬럼
-- 4: HAVING 그룹에 대한 조건식 
-- 6: ORDER BY 컬럼 | 별칭 | 순서
```

## ODER BY

```mysql
-- [ORDER BY]
-- SELECT를 통해 조회한 행의 결과들을 특정 기준에 맞춰 정렬

select EMP_ID, EMP_NAME "이름", SALARY, DEPT_CODE
from employee
order by 3 desc; -- 3번째 컬럼의 순번으로 정렬
-- order by EMP_NAME desc;  -- 기본은 오름차순(asc), 내림차순(DESC)
-- order by DEPT_CODE desc, EMP_ID; -- 선조건, 후속조건으로 정렬 가능
-- order by 이름 desc; -- 별칭을 통해서 정렬
```

## GROUP BY & HAVING

```mysql
-- [GROUP BY]
-- 지정한 그룹별로 함수 적용하여 결과값 조회

-- 전체 급여 평균
select TRUNCATE(AVG(SALARY), -4) 급여평균
from employee;

-- D1 부서 평균
select TRUNCATE(AVG(SALARY), -4) 급여평균, DEPT_CODE 부서
from employee
where DEPT_CODE = 'D1';

-- 부서별 평균 조회
select DEPT_CODE, TRUNCATE(AVG(SALARY), -4) 급여평균
from EMPLOYEE
where DEPT_CODE is not NULL
group by DEPT_CODE
order by 1;

-- 그룹안에 그룹처리도 가능
select DEPT_CODE, JOB_CODE, SUM(SALARY)
from EMPLOYEE 
group by DEPT_CODE, JOB_CODE;

-- [HAVING]
-- GROUP BY 한 소그룹에 대한 조건을 설정

-- 부서별 급여 평균이 300만원 이상인 부서 조회.
select DEPT_CODE ,
TRUNCATE(AVG(SALARY), -4)
from EMPLOYEE
group by DEPT_CODE 
having AVG(SALARY) > 3000000 -- 그룹바이를 적용한 상태로 적용하는 조건
order by DEPT_CODE;
```

**실습 코드**

```mysql
-- 실습
-- EMPLOYEE 테이블에서
-- 부서별 총 인원, 급여 합계, 급여 평균, 최대급여, 최소급여를 조회
-- 부서코드 오름차순 정렬, TRUNCATE(, -3)처리
select DEPT_CODE "부서코드",
COUNT(*) "부서별 총인원",
TRUNCATE(SUM(SALARY), -3) "급여합계",
TRUNCATE(AVG(SALARY), -3) "급여평균",
MAX(SALARY) "최대급여",
MIN(SALARY) "최소급여"
from employee
group by DEPT_CODE 
order by DEPT_CODE;

-- 실습
-- 부서별 그룹의 급여 합계 중 900만원 초과하는
-- 부서의 부서코드와 급여 합계 조회.
select DEPT_CODE 부서,
TRUNCATE(SUM(SALARY), -4) 급여합계
from EMPLOYEE
group by DEPT_CODE 
having SUM(SALARY) > 9000000
ORDER by DEPT_CODE;

-- 실습
-- EMPLOYEE 테이블에서 직급별 그룹을 편성하여
-- 직급코드, 급여 합계, 급여 평균, 인원수 조회
-- 단, 인원수는 3명을 초과하는 직급만을 조회
-- 조회결과는 인원수 내림차순 조회
select JOB_CODE 직급코드, SUM(SALARY) 급여합계, TRUNCATE(AVG(SALARY),-4) 급여평균, COUNT(*) 인원수
from employee
group by JOB_CODE
HAVING COUNT(*)>3
order by 인원수 desc;

-- 실습
-- 성별에 따른 급여합계, 급여평균, 인원수 조회
-- 단 성별이 여자인경우 F, 남자인 경우 M으로 표현
select 
case 
	when SUBSTR(EMP_NO,8,1)=1 then 'M'
	else 'F' 
end "성별", 
SUM(SALARY) 급여합계, TRUNCATE(AVG(SALARY), -4) 급여평균, COUNT(*) 인원수
from employee
group by SUBSTR(EMP_NO,8,1);
```

