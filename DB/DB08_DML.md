# DML(Data Manipulation Language)

```mysql
-- SELECT, INSERT, UPDATE, DELETE
-- [CRUD]
-- C : INSERT
-- R : SELECT
-- U : UPDATE
-- D : DELETE
```

## INSERT

```mysql
-- [INSERT] 새로운 행을 특정 테이블에 추가하는 명령어
-- 원하는 값만 입력하여 데이터 추가하기
insert into EMPLOYEE(EMP_ID, EMP_NAME, EMP_NO, EMAIL, PHONE, DEPT_CODE,
					 JOB_CODE, SAL_LEVEL, SALARY, BONUS, MANAGER_ID, HIRE_DATE,
					 ENT_DATE, ENT_YN)
values(500, '김기묵', '900123-1234567', 'KIM_GM@MULTI.KR', '01022223333', 'D1', 'J7', 'S4',
	   3100000, 0.1, '200', NOW(), null, default);

-- 컬럼을 생략하면 모든값을 순서대로 입력해 줘야함
insert into EMPLOYEE VALUES(900, '오민섬', '521008-2331423', 'HO_MS@MULTI.KR', '01011442244', 'D1',
							'J7', 'S3', 4300000, 0.2, '200', NOW(), null, DEFAULT);
```

## INSERT + SUBQUERY

```mysql
-- INSERT + SUBQUERY
-- 기존테이블의 데이터로부터 원하는 데이터를 뽑아 테스트 테이블을 만들어 이용할때 사용
create table EMP_01(
	EMP_ID INT,
	EMP_NAME VARCHAR(20),
	DEPT_TITLE VARCHAR(40)
);

insert into EMP_01 (select EMP_ID, EMP_NAME, DEPT_TITLE
					from employee
					left join DEPARTMENT on(DEPT_CODE = DEPT_ID)
					);
```

## UPDATE

```mysql
-- UPDATE : 해당 테이블의 데이터를 수정하는 명령어
create table DEPT_COPY as select * from department;
UPDATE DEPT_COPY set DEPT_TITLE = '전략기획부' where DEPT_ID = 'D9';
```

**실습 코드**

```mysql
-- 실습
-- EMPLOYEE 주민번호 잘못 표기된 데이터 UPDATE
select EMP_ID, EMP_NO
from employee e 
where SUBSTR(EMP_NO,5,2) >31; -- 결과 EMP_ID가 200, 201, 214 3개가 조회됨
-- 적당한 값으로 수정
update EMPLOYEE set EMP_NO = CONCAT('621230', SUBSTR(EMP_NO,7))
where EMP_ID = 200;
update EMPLOYEE set EMP_NO = CONCAT('621126', SUBSTR(EMP_NO,7))
where EMP_ID = 201;
update EMPLOYEE set EMP_NO = CONCAT('850705', SUBSTR(EMP_NO,7))
where EMP_ID = 214;
```

## DELETE

```mysql
-- [DELETE] 테이블의 행을 삭제하는 명령어
DELETE FROM EMPLOYEE WHERE EMP_ID = 200;

-- DELETE 전체삭제(조심)
delete from EMPLOYEE;
```

