# 데이터베이스 언어(DDL, DML, DCL, TCL)

# SQL (Structured Query Language)

- 구조적인 질의 언어
- DDL, DML, DCL 으로 나눌 수 있다.

# DDL (Data Definition Language)

- 데이터베이스 스키마를 정의하거나 조직하기 위해 사용.
- SHCEMA, DOMAIN, TABLE, VIEW, INDEX를 다음명령어로 정의, 변경, 삭제한다.

    → CREATE : 정의

    → ALTER : 수정

    → DROP : 삭제

    → TRUNCATE : 내용삭제

truncate → 테이블의 내용만 제거

drop → 테이블 자체를 제거

# DML (Data Manipulation Language)

- 데이터를 조작(조회, 추가, 변경, 삭제)하기 위해 사용.
- 사용자가 응용프로그램과 데이터베이스 사이의 실질적인 데이터 처리를 위해 주로 사용.

    → SELECT : 조회

    → INSERT : 추가

    → DELETE : 삭제

    → UPDATE : 변경

### DQL (Data Query Language)

일부 DML에서 SELECT만 따로 분리해서 표현

# DCL (Data Control Language)

- 데이터를 제어하는 언어이다.
- 데이터의 보안, 무결성, 회복, 병행 수행제어 등을 정의하는데 사용.

    → COMMIT : 트랜잭션의 작업 결과를 반영

    → ROLLBACK : 트랜잭션의 작업을 취소 및 원래대로 복구

    → GRANT : 사용자에게 권한 부여

    → REVOKE : 사용자 권한 취소

### TCL (Transaction Control Language)

일부 DCL에서 COMMIT과 ROLLBACK만 따로 분리하여 표현
