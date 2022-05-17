# VIEW (뷰)

```mysql
-- VIEW(뷰)
create view V_EMP
as 
select EMP_ID, EMP_NAME, DEPT_CODE from EMPLOYEE;

select * from v_emp;


-- 사번, 이름, 직급명, 부서명, 근무지역을 조회
-- 그 결과를 V_RES_EMP 라는 뷰를 만들고 해당 뷰를 통해 결과 조회
-- 1) 서브쿼리 준비
select EMP_ID, EMP_NAME, JOB_NAME, DEPT_TITLE, LOCAL_NAME
from employee e 
left join department d on(DEPT_CODE = DEPT_ID)
left join job j USING(JOB_CODE)
left join location l ON(LOCATION_ID = LOCAL_CODE);
-- 2) 뷰 생성
-- drop view v_res_emp ;
create or REPLACE view V_RES_EMP(사번, 이름, 직급명, 부서명, 근무지역)
as 
select EMP_ID, EMP_NAME, JOB_NAME, DEPT_TITLE, LOCAL_NAME
from employee e 
left join department d on(DEPT_CODE = DEPT_ID)
left join job j USING(JOB_CODE)
left join location l ON(LOCATION_ID = LOCAL_CODE);

select * from V_RES_EMP;

show create view V_EMP;

-- 만들어진 VIEW(V_RES_EMP)를 이용하여
-- 사번이 205인 직원 조회하기
select *
from v_res_emp vre 
where 사번 = 205;

-- 뷰 삭제
drop view v_res_emp;

-- 컬럼별 별칭을 붙일 수 있음
create or replace view V_EMP(사번, 사원명, 부서코드)
as
select EMP_ID, EMP_NAME, DEPT_CODE
from EMPLOYEE;

-- 뷰에는 연산, 함수 결과도 포함하여 저장 가능
-- 사번, 이름, 성별, 근무년수 조회
-- 1) 서브쿼리 작성
select EMP_ID 사번, EMP_NAME 이름,
	   if(SUBSTR(EMP_NO, 8, 1) = 1, '남', '여') 성별,
	   EXTRACT(year from NOW()) - EXTRACT(year from hire_date) 근무년수
from EMPLOYEE;
-- 2) 뷰 작성
create or replace view V_EMP(사번, 이름, 성별, 근무년수)
as
select EMP_ID 사번, EMP_NAME 이름,
	   if(SUBSTR(EMP_NO, 8, 1) = 1, '남', '여') 성별,
	   EXTRACT(year from NOW()) - EXTRACT(year from hire_date) 근무년수
from EMPLOYEE;

select * from V_EMP;


-- 뷰에 데이터 삽입, 수정 삭제하기
create or replace view V_JOB
as 
select * from JOB;

select * from V_JOB;
select * from JOB;

-- 뷰를 통한 데이터 추가(원본도 바뀜)
insert into V_JOB VALUES('J8', '인턴');

-- 뷰를 통한 데이터 수정
update V_JOB
set JOB_NAME = '알바'
where JOB_CODE = 'J8';

-- 뷰를 통한 데이터 삭제
delete from V_JOB
where JOB_CODE = 'J8';
```

