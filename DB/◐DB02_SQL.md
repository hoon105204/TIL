# SQL

\- 구조화된 질의언어(Structured Query Language)

- **DLL 데이터 정의 언어** (Data Definition Language) : DB 스키마 정의, 조작
  \- **CREATE** : 데이터베이스, 테이블, 뷰(view), 프로시저(procedure) 등을 **생성**

  ```mysql
  CREATE DATABASE 데이터베이스;     -- 데이터베이스 생성
  
  ```

  \- **ALTER** : **수정**
  \- **DROP** : **삭제**
  	\* View : 다른 테이블/뷰 에 있는 데이터를 보여주기 위해 사용(수정 불가)
  	\* Procedure : 특정 작업에 필요한 Query들을 함수처럼 사용

- **DML 데이터 조작 언어**(Data Manipulation Language)
  \- **SELECT** : 데이터 **읽기**

  ```mysql
  SELECT 컬럼 FROM 테이블;     -- 테이블에서 컬럼 조회
  ```

  \- **INSERT** : 데이터 **삽입**
  \- **UPDATE** : 데이터 **수정**
  \- **DELETE** : 데이터 **삭제**

- **DCL 데이터 제어 언어**(Data Control Language)
  \- **COMMIT **: 데이터, 트랜잭션 **저장**
  \- **ROLLBACK** : 데이터, 트랜잭션 **취소** (가장 마지막 COMMIT으로 되돌아감)
  \- **GRANT** : DB 권한 부여
  \- **REVOKE** : DB 권한 삭제
      \* TCL (Transaction Contraoll Language) : COMMIT, ROLLBACK



**TIP** DBeaver 사용
\- Alt + x : 드래그한 부분실행
\- Ctrl + Enter : 커서위치 실행