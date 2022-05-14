# SQL

- 구조화된 질의언어(Structured Query Language)

- CRUD : 데이터 기본 처리 로직

  ```mysql
  -- CREATE : 데이터 추가 / INSERT
  -- READ   : 데이터 조회 / SELECT
  -- UPDATE : 데이터 수정 / UPDATE
  -- DELETE : 데이터 삭제 / DELETE
  ```

## DLL 

- 데이터 정의 언어 (Data Definition Language) : DB 스키마 정의, 조작
  - **CREATE** : 데이터베이스, 테이블, 뷰(view), 프로시저(procedure) 등을 **생성**
  
    View : 다른 테이블/뷰 에 있는 데이터를 보여주기 위해 사용(수정 불가)
    Procedure : 특정 작업에 필요한 Query들을 함수처럼 사용
  
    ```mysql
    CREATE DATABASE 데이터베이스;     -- 데이터베이스 생성
    
    -- 제약조건을 가진 테이블 생성
    create table USER_NOT_NULL( 
        USER_ID VARCHAR(20) UNIQUE, -- 중복 허용 X
        MY_NUM INT auto_increment, -- INSERT 때마다 1씩 자동 증가 옵션
        GENDER VARCHAR(3),
        USER_PONE INT not null, -- NULL값 허용 X (컬럼 레벨)
        USER_NO VARCHAR(20) primary KEY, -- NOT NULL과 UNIQUE 제약조건을 함께걸어 식별자 역할
        constraint CHECK_GENDER CHECK(GENDER in ('M','F')) -- GENDER에 CHECK 제약조건 추가, 제약조건 이름 지정 (테이블 레벨)
    );
    ```
  
  - **ALTER** : **수정**
  
    ```mysql
    -- 제약조건을 추가
    alter table DEPARTMENT add constraint PK_DEPT_DEPTID primary KEY(DEPT_ID);
    
    -- 컬럼 추가
    alter table DEPT_COPY add (LNAME VARCHAR(20));
    
    -- 컬럼 삭제
    alter table DEPT_COPY drop column LNAME;
    ```
  
  - **DROP** : **삭제**
  
    ```mysql
    DROP DATABASE 데이터베이스; -- 데이터베이스 삭제
    
    drop table USER_NOT_NULL; -- 테이블 삭제
    ```
  
    

## DML

- DML 데이터 조작 언어(Data Manipulation Language)
  
  - **SELECT** : 데이터 **읽기**
  
  ```mysql
  -- SELECT : 조회용 SQL
  SELECT * (조회 컬럼) FROM 테이블명 WHERE 조건 ORDER BY 컬럼;
  ```
  
  - **INSERT** : 데이터 **삽입**
  - **UPDATE** : 데이터 **수정**
  - **DELETE** : 데이터 **삭제**

## DCL 

- 데이터 제어 언어(Data Control Language)

  - **COMMIT **: 데이터, 트랜잭션 **저장**

  - **ROLLBACK** : 데이터, 트랜잭션 **취소** (가장 마지막 COMMIT으로 되돌아감)

  - **GRANT** : DB 권한 부여

  - **REVOKE** : DB 권한 삭제
      \* TCL (Transaction Contraoll Language) : COMMIT, ROLLBACK



**TIP** DBeaver 사용
- Alt + x : 드래그한 부분실행
- Ctrl + Enter : 커서위치 실행