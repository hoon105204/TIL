# SET OPERATION

## UNION

```mysql
-- SET OPERATION
-- [UNION] : 두 개 이상의 SELECT한 결과를 합쳐 RESULT SET을 구하는 명령어
-- 			중복되는 결과는 한번만 보여준다.
-- [UNION ALL] : 중복이 있어도 내용 그대로 조회해 준다.
-- (주의) UNION 되는 다수의 SELECT는 컬럼이 같아야 한다 (내용이 달라도 수가 같으면 합쳐짐)

select EMP_ID, EMP_NAME, DEPT_CODE, SALARY
from EMPLOYEE 
where DEPT_CODE = 'D5'
union -- select 2개를 합침
select EMP_ID, EMP_NAME, DEPT_CODE, SALARY
FROM EMPLOYEE 
where SALARY >3000000;
```

<img src=".\image\DB05_01union.png" alt="DB05_01union" style="zoom:100%;" />

## JOIN

```mysql
-- [JOIN]
-- 두개 이상의 테이블을 하나로 합쳐 사용하는 명령 구문
-- 컬럼을 통해 키값을 찾아 <테이블> 데이터를 매칭
-- [ JOIN <테이블> ON (<컬럼> = <컬럼>) ] 컬럼명이 다를때
-- [ JOIN <테이블> USING(컬럼)] 컬럼명이 같을때

-- employee 테이블과 DEPARTMENT 테이블을 합치며
-- 기준은 DEPT_CODE = DEPT_ID 일때
select EMP_NAME, JOB_CODE, DEPT_CODE, DEPT_TITLE
from employee
join DEPARTMENT on (DEPT_CODE = DEPT_ID);

select EMP_ID, EMP_NAME, JOB_CODE, JOB_NAME
from employee e 
join JOB using(JOB_CODE); -- 컬럼명이 같을때 USING 이용
```

```mysql
-- (INNER) JOIN : 조건에 만족하는 데이터만 선택. 조건에 만족하지 않는 데이터는 제거
-- OUTER JOIN
-- - LEFT OUTER JOIN : 첫번째 테이블 기준으로 만족하지 않는 데이터라도 유지, NULL 데이터가 붙는다
-- - RIGHT OUTER JOIN : 두번째 테이블 ...
select EMP_NAME, DEPT_CODE, DEPT_ID, DEPT_TITLE
from EMPLOYEE 
left outer join DEPARTMENT on(DEPT_CODE = DEPT_ID);

select EMP_NAME, DEPT_CODE, DEPT_ID, DEPT_TITLE
from EMPLOYEE 
RIGHT outer join DEPARTMENT on(DEPT_CODE = DEPT_ID);

-- JOIN에 계산식도 들어갈 수 있음
-- employee의 SALARY 값이 SAL_GRADE의 MIN_SAL 값과 MAX_SAL 값 사이에 있으면 그 데이터와 합침
select EMP_NAME, DEPT_CODE, SALARY, E.SAL_LEVEL
from employee E
join SAL_GRADE S on ( SALARY between MIN_SAL and MAX_SAL);
```

<img src=".\image\DB05_02join.png" alt="DB05_02join" style="zoom:100%;" />

```mysql
-- SELF JOIN
-- 직원의 정보와 직원을 관리하는 매니저의 정보를 조회
-- 컬럼명이 동일하다보니 테이블 별칭을 이용하여 구분지어 줘야함
select E.EMP_ID "사번", E.EMP_NAME "사원명", E.MANAGER_ID "관리자 사번", M.EMP_NAME "관리자명"
from EMPLOYEE E
left join employee M on (E.MANAGER_ID = M.EMP_ID);

-- 다중 JOIN (순서가 중요!)
select EMP_NAME, DEPT_TITLE, LOCAL_NAME
from employee e 
join department d on (DEPT_CODE = DEPT_ID)
join LOCATION on (LOCATION_ID = LOCAL_CODE);
```

**코드 실습**

```mysql
-- 실습
-- 직급이 대리이면서, 아시아 지역에서 근무하는 사원 조회
-- 사번, 사원명, 직급명, 부서명, 근무지역명, 급여
select EMP_ID 사번, EMP_NAME 사원명, JOB_NAME 직급명, DEPT_TITLE 부서명, LOCAL_NAME 근무지역명, SALARY 급여
FROM EMPLOYEE E
LEFT JOIN JOB USING(JOB_CODE)
left join department on (DEPT_CODE = DEPT_ID)
left join location on (LOCATION_ID = LOCAL_CODE)
where JOB_NAME ='대리' and LOCAL_NAME like 'ASIA%';
-- WHERE 절을 쓰지 않고 JOIN을 이용해 조건에 맞는 데이터가 아니면 제거해 나갈수 있음
select EMP_ID 사번, EMP_NAME 사원명, JOB_NAME 직급명, DEPT_TITLE 부서명, LOCAL_NAME 근무지역명, SALARY 급여
FROM EMPLOYEE E
LEFT JOIN JOB USING(JOB_CODE)
join JOB J ON(E.JOB_CODE = J.JOB_CODE AND JOB_NAME='대리')
join department on (DEPT_CODE = DEPT_ID)
join location on (LOCATION_ID = LOCAL_CODE AND LOCAL_NAME LIKE 'ASIA%');
```

