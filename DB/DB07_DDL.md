# DDL(Data Definition Language)

## Create table

```mysql
-- 테이블 생성
drop table MEMBER;
CREATE table MEMBER(
	MEMBER_NO INT,		-- 회원번호
	MEMBER_ID VARCHAR(20), -- 회원아이디
	MEMBER_PW VARCHAR(20), -- 회원 비밀번호
	MEMNBER_NAME VARCHAR(15) COMMENT '회원이름'
);
```

## 제약 조건(Constraints)

```mysql
-- 테이블 생성 할 때 컬럼에 값을 기록하는 것에 대한 제약사항을 설정 조건
-- NOT NULL : 컬럼에 NULL값 허용하지 않음, 필수 입력 사항 설정
-- UNIQUE : 중복 값을 허용하지 않음
-- CHECK : 지정한 입력사항 외에는 받지 못하게 막는 조건 (EX. 남/여, 0보다 큰값)
-- PRIMARY KEY : NOT NULL + UNIQUE 테이블 내에서 해당 행을 인식할 수 있는 고유 값
-- FOREIGN KEY : 다른 테이블에서 저장된 값을 연결 지어서 참조로 가져오는 데이터에 지정하는 제약조건

-- 테이블의 설정조건을 확인
select * from INFORMATION_SCHEMA.TABLE_CONSTRAINTS
where CONSTRAINT_SCHEMA = 'multi';

-- 제약조건을 가진 테이블 생성
create table USER_NOT_NULL( 
    USER_ID VARCHAR(20) UNIQUE, -- 중복 허용 X
    MY_NUM INT auto_increment, -- INSERT 때마다 1씩 자동 증가 옵션
    GENDER VARCHAR(3) not null, -- 제약조건 여러개 적용 가능
    USER_PONE INT not null, -- NULL값 허용 X (컬럼 레벨)
    USER_NO VARCHAR(20) primary KEY, -- NOT NULL과 UNIQUE 제약조건을 함께걸어 식별자 역할
    constraint CHECK_GENDER CHECK(GENDER in ('M','F')) -- GENDER에 CHECK 제약조건 추가, 제약조건 이름 지정 (테이블 레벨)
);
```



```mysql
-- [FOERIGN KEY] : 외래키, 외부키, 참조키
-- 다른 테이블의 컬럼값을 참고하여 참조하는 테이블의 값만을 허용

-- 예시
-- (GRADE_CODE, GRADE_NAME)의 값이 4개인 USER_GRADE 테이블 생성
create table USER_GRADE(
	GRADE_CODE INT primary key,
	GRADE_NAME VARCHAR(30) not NULL
);

insert into USER_GRADE VALUES(1, '일반회원');
insert into USER_GRADE VALUES(2, 'VIP');
insert into USER_GRADE VALUES(3, 'VVIP');
insert into USER_GRADE VALUES(4, 'VVVIP');
```

![DB07_01FoerignKey](.\image\DB07_01FoerignKey.png)

```mysql
-- USER_GRADE를 참조하는 테이블 생성
create table USER_FOERIGN_KEY(
	USER_NO INT primary KEY,
	USER_ID VARCHAR(20),
	USER_PASS VARCHAR(20),
	GENDER VARCHAR(1) CHECK(GENDER in('M','F')),
	GRADE_CODE INT,
	constraint FK_GRADE_CODE foreign KEY(GRADE_CODE) -- GRADE_CODE를 제한시킬건데
	references USER_GRADE(GRADE_CODE)				 -- USER_GRADE 테이블에 있는 GRADE_CODE를 참조한다
);

insert into USER_FOERIGN_KEY VALUES(1, 'USER01', 'PASS01', 'F', 2);
insert into USER_FOERIGN_KEY VALUES(2, 'USER02', 'PASS02', 'M', 4);
insert into USER_FOERIGN_KEY VALUES(3, 'USER03', 'PASS03', 'M', 1);
insert into USER_FOERIGN_KEY VALUES(4, 'USER04', 'PASS04', 'F', 3);
```

![DB07_01FoerignKey2](.\image\DB07_01FoerignKey2.png)

```mysql
select * from USER_GRADE;
-- 행이 참조를 당하고 있으면 일반적으로 DELETE 행삭제가 불가능
-- SQL Error [1451] [23000]: Cannot delete or update a parent row: a foreign key constraint fails

-- 삭제 옵션
-- ON DELETE CASCADE : 자식 테이블의 데이터도 삭제
drop table USER_FOERIGN_KEY;

create table USER_FOERIGN_KEY(
	USER_NO INT primary KEY,
	USER_ID VARCHAR(20),
	USER_PASS VARCHAR(20),
	GENDER VARCHAR(1) CHECK(GENDER in('M','F')),
	GRADE_CODE INT,
	constraint FK_GRADE_CODE foreign KEY(GRADE_CODE)
	references USER_GRADE(GRADE_CODE) on delete cascade -- 삭제 옵션을 달아줌
);

-- 업데이트 옵션
-- ON UPDATE CASCADE : 자식 테이블의 데이터도 업데이트 
drop table USER_FOERIGN_KEY;
create table USER_FOERIGN_KEY(
	USER_NO INT primary KEY,
	USER_ID VARCHAR(20),
	USER_PASS VARCHAR(20),
	GENDER VARCHAR(1) CHECK(GENDER in('M','F')),
	GRADE_CODE INT,
	constraint FK_GRADE_CODE foreign KEY(GRADE_CODE)
	references USER_GRADE(GRADE_CODE) on delete cascade on update cascade -- 삭제와 업데이트 옵션을 달아줌
);
```

## ALTER

```mysql
-- [ALTER] : 테이블같은 객체를 수정

-- 제약조건을 추가할 수 있음(어떤 테이블의 어떤 컬림인지)
alter table DEPARTMENT add constraint PK_DEPT_DEPTID primary KEY(DEPT_ID);
alter table EMPLOYEE add constraint foreign KEY(DEPT_CODE) references DEPARTMENT(DEPT_ID);
alter table EMPLOYEE add constraint foreign KEY(SAL_LEVEL) references SAL_GRADE(SAL_LEVEL);

alter table EMPLOYEE add CHECK(ENT_YN in ('Y', 'N'));

alter table EMPLOYEE add UNIQUE(EMP_NO);

-- 컬럼 추가
alter table DEPT_COPY add (LNAME VARCHAR(20));
alter table DEPT_COPY add (LNAME VARCHAR(20) default '한국'); -- default 적용 가능

-- 컬럼 삭제
alter table DEPT_COPY drop column LNAME;

desc DEPT_COPY;
```

