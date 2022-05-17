# TCL(Transaction Control Language)

```mysql
-- TCL : 트랜잭션 제어어, 데이터 처리의 최소 작업 단위
-- 하나의 트랜잭션으로 이루어진 작업은 반드시 작업 내용이 모두 성공하여 저장되거나, 실패시 모두 이전으로 복구되어야한다
-- COMMIT, ROLLBACK (+ SAVEPOINT, ROLLBACK TO)
```

```mysql
create table USER_TBL(
	USER_NO INT unique,
	USER_ID VARCHAR(20) not null unique,
	USER_PW VARCHAR(30) not null
);

desc USER_TBL;

insert into USER_TBL VALUES(1,'TEST01','PASS01');
insert into USER_TBL values(2, 'TEST02','PASS02');
select * from USER_TBL;

commit; -- 현재까지 작업한 DML내용을 DB에 반영함

insert into USER_TBL VALUES(3, 'TEST03', 'PASS03');
select * from USER_TBL;

rollback;
select * from USER_TBL;

insert into USER_TBL VALUES(3, 'TEST03', 'PASS03');

savepoint SP1; -- 세이브포인트 지정

insert into USER_TBL VALUES(4, 'TEST04', 'PASS04');
select * from user_TBL;

rollback to SP1; -- 세이브 포인트로 롤백
select * from USER_TBL; 

rollback; -- 커밋 시점으로 롤백
select * from user_TBL;
```

