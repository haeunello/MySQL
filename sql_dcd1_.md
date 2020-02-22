SQL DCD(Data Control Language) : 사용자 확인, 추가, 비밀번호 변경, 삭제 
----------------------------------------------------------------------------
  + [Window OS] use 'MySQL 8.0 Command Line Client - Unicode' 
  + There is a database called 'mysql' in MySQL.
  + There is a way to use CMD with editing the system path (C:\Program Files\MySQL\MySQL Server 8.0\bin).

### 1. how to check the users
  + 사용자 비밀번호 입력
  + 데이터베이스 안의 테이블 확인
   ~~~
   use mysql;
   show tables;
   ~~~
  + 'user'테이블에서 사용자 정보 확인 
   ~~~
   select * from user;
   ~~~
### 2. how to create new userid
  + 로컬에서만 접속 가능한 사용자(new1) 추가
   ~~~
   create user 'new1'@localhost identified by '비밀번호';
   ~~~
  + 모든 호스트에서 접속 가능한 사용자(new1) 추가
   ~~~
   create user 'new1'@'%'identified by '비밀번호';
   ~~~
### 3. how to change the password and delete existing user
  + 사용자 비밀번호 변경
   ~~~
   SET PASSWORD FOR 'new1'@'%' = '새로운 비밀번호';
   ~~~
  + 사용자 삭제
   ~~~
   use mysql;
   drop user 'new1'@'%';
   ~~~
  
