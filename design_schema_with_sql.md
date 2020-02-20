 Design schema with sql
-----------------------------

### 1. Create a database called 'mydata'
  + check the exising databases before create a new one.
  + activate 'mydata' database to use it.
  + To delete the database(called 'mydata'), 'DROP DATABASE IF EXISTS mydata;' can be used.
~~~  
#to check databases
SHOW DATABASES;

#to make a new database called 'mydata'
CREATE DATABASE mydata;

#to use the database 
USE mydata;
~~~

### 2. Create a table called 'mytable' in 'mydata'
  + 'relation' is considered the same as 'table'
  + 'column name' + 'datatype' + 'unsigned(to positive)'+ 'about null value'+ 'auto_increment'
~~~
CREATE TABLE mytable(
  no INT UNSIGNED NOT NULL AUTO_INCREMENT,
  name CHAR(20) NOT NULL,
  age TINYINT,
  phone VARCHAR(20),
  email VARCHAR(30) NOT NULL,
  address VARCHAR(50),
  PRIMARY KEY(no)
);

#to check tables in the database
SHOW TABLES;

#to check the details in the table called 'mytable'
DESC mytable;
~~~

### 3. Change columns information in the table 
  + There are many ways to change columns information.
  + ADD COLUMN, MODIFY COLUMN, CHANGE COLUMN, DROP COLUMN
~~~
#to add column
ALTER TABLE mytable ADD COLUMN model_type VARCHAR(10) NOT NULL;

#to change the data type of the column
ALTER TABLE mytable MODIFY COLUMN name VARCHAR(10) NOT NULL;

#to change name of the coulmn (name -> model_name)
ALTER TABLE mytable CHANGE COLUMN name model_name VARCHAR(10);

#to delete the column
ALTER TABLE mytable DROP COLUMN age;
~~~
### 4. Additional details
  + RDBMS(Relational Database Management System, 관계형 데이터베이스 관리시스템) 
  + 데이터베이스의 한 종류로 가장 많이 사용됨, '테이블'로 이해할 수 있음
  + 테이블은 칼럼(칼럼Column=필드Field=속성Attribute)의 열과 로우(로우Row=레코드Record=튜플Tuple)로 이루어짐
  + 각 테이블마다 Primary Key가 존재하며, Primary Key에는 null값이 허용되지 않으며, unique value로 구성되어야 함 
  + DB Schema : 데이터베이스의 테이블 구조, 형식, 관계등의 정보를 formal language로 기술한 것




