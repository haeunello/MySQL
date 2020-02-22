SQL DCD(Data Control Language) : MySQL 접속 허용 관련 설정 
---------------------------------------------------------
  + [Window OS] use 'MySQL 8.0 Command Line Client - Unicode' 
  + There is a database called 'mysql' in MySQL.
  + There is a way to use CMD with editing the system path (C:\Program Files\MySQL\MySQL Server 8.0\bin).

### 1. 'user1' 사용자에게 현재 부여된 권한 확인 
~~~
SHOW GRANTS for 'user1'@'%';
~~~
### 2. 'user1' 사용자에게 권한 부여 
  + 'ecommerce' database의 'product' table에 대한 모든 권한을 부여하는 경우
  + [ecommerce.product] 부분을 필요에 따라 변경할 수 있음 
  ~~~
  #특정 데이터베이스의 특정 테이블에 대한 모든 권한 부여
  GRANT ALL ON ecommerce.product TO 'user1'@'%';
  
  #특정 데이터베이스에 대한 모든 권한 부여
  GRANT ALL ON ecommerce.* TO 'user1'@'%';
  
  #모든 데이터베이스에 대한 모든 권한 부여
  GRANT ALL ON *.* TO 'user1'@'%';
  ~~~
  + 특정 권한만 주고 싶은 경우 (부여할 권한은 commea로 연결함)
  ~~~
  GRANT SELECT,INSERT ON ecommerce.* TO 'user1'@'%';
  ~~~
  
  
