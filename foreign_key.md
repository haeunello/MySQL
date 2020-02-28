Foreign Key (왜래키)
----------------------
### 1. How to set a foreign key when create a table : 
#### 1.1 Basic steps to create a DB amd table
~~~
#newDB 생성 및 활성화 
DROP DATABASE IF EXISTS commerceDB;
CREATE DATABASE commerceDB DEFAULT CHARSET = uft8 COLLATE = utf8_bin;
USE commerceDB;

#사용자 정보를 담은 테이블 생성
CREATE TABLE userinfo (
  userID CHAR(8) NOT NULL PRIMARY KEY,
  username VARCHAR(10) NOT NULL,
  birthYear INT NOT NULL,
  address CHAR(2) NOT NULL,
  usernum1 CHAR(3),
  usernum2 CHAR(8),
  height SMALLINT,
  mDATE DATE
  ) DEFAULT CHARSET = utf8 COLLATE = utf8_bin;
 ~~~
 #### 1.2 The way to set a foreign key
 ~~~
 CREATE TABLE purchaseinfo(
  num INT AUTO_INCREMENT NOT NULL PRIMARY KEY,
  userID CHAR(8) NOT NULL,
  prodName CHAR(4),
  groupName CHAR(4),
  price INT NOT NULL,
  amount SMALLINT NOT NULL,
  
  #foreign key(외래키) 설정 : 참조할 테이블 명과 필드명 입력
  FOREIGN KEY (userID) REFERENCES userinfo(userID)
  ) DEFAULT CHARSET = utf8 COLLATE = utf8_bin;
  ~~~
#### 1.3 Data Insertion
~~~
INSERT INTO userinfo VALUES('KDD', '김댕댕', 1987, '서울', '011', '11111111', 182, '2008-8-8');
INSERT INTO userinfo VALUES('LDE', '이둘이', 1979, '경남', '011', '22222222', 173, '2012-4-4');
INSERT INTO userinfo VALUES('KSE', '김삼이', 1971, '전남', '019', '33333333', 177, '2007-7-7');
INSERT INTO userinfo VALUES('CSE', '최사이', 1950, '경기', '011', '44444444', 166, '2009-4-4');
INSERT INTO userinfo VALUES('LOE', '임오이', 1979, '서울', NULL, NULL, 186, '2013-12-12');
INSERT INTO userinfo VALUES('YIE', '윤일이', 1963, '서울', '016', '66666666', 182, '2009-9-9');
INSERT INTO userinfo VALUES('CDE', '조둘이', 1960, '경남', NULL, NULL, 170, '2005-5-5');
INSERT INTO userinfo VALUES('CCE', '최칠이', 1972, '경북', '011', '88888888', 174, '2014-3-3');
INSERT INTO userinfo VALUES('LKE', '이구이', 1965, '경기', '016', '99999999', 172, '2010-10-10');
INSERT INTO userinfo VALUES('SSE', '서십이', 1973, '서울', '010', '00000000', 176, '2013-5-5');
INSERT INTO purchaseinfo (userID, prodName, groupName, price, amount) VALUES('KDD', '운동화', '의류', 30, 2);
INSERT INTO purchaseinfo (userID, prodName, groupName, price, amount) VALUES('KDD', '노트북', '전자', 1000, 1);
INSERT INTO purchaseinfo (userID, prodName, groupName, price, amount) VALUES('CSE', '모니터', '전자', 200, 1);
INSERT INTO purchaseinfo (userID, prodName, groupName, price, amount) VALUES('KSE', '모니터', '전자', 200, 5);
INSERT INTO purchaseinfo (userID, prodName, groupName, price, amount) VALUES('KSE', '청바지', '의류', 50, 3);
INSERT INTO purchaseinfo (userID, prodName, groupName, price, amount) VALUES('LOE', '메모리', '전자', 80, 10);
INSERT INTO purchaseinfo (userID, prodName, groupName, price, amount) VALUES('CCE', '책', '서적', 15, 5);
INSERT INTO purchaseinfo (userID, prodName, groupName, price, amount) VALUES('LKE', '책', '서적', 15, 2);
INSERT INTO purchaseinfo (userID, prodName, groupName, price, amount) VALUES('LKE', '청바지', '의류', 50, 1);
INSERT INTO purchaseinfo (userID, prodName, groupName, price, amount) VALUES('LKE', '운동화', '의류', 30, 2);
INSERT INTO purchaseinfo (userID, prodName, groupName, price, amount) VALUES('SSE', '책', '서적', 15, 1);
INSERT INTO purchaseinfo (userID, prodName, groupName, price, amount) VALUES('CDE', '운동화', '의류', 30, 2);
~~~

### 2. How to handle data when there is a foreign key : 
#### 2.1 newDB and tables 
~~~
import pymysql

host_name = 'localhost'
host_port = 3306
username = 'root'
password = '#######'
database_name = 'commerceDB'

db = pymysql.connect(host = host_name, port = host_port, user = username, passwd= password, db= database_name, charset='utf8')
~~~
~~~
#userinfo Table 
SQL = 'select * from userinfo'
df = pd.read_sql(SQL); df
~~~
![외래키1](https://user-images.githubusercontent.com/58417351/75534139-26097f80-5a58-11ea-9f98-c285789c537d.PNG)
~~~
#purchase Table 
SQL = 'select * from purchaseinfo'
df = pd.read_sql(SQL); df
~~~
![외래키2](https://user-images.githubusercontent.com/58417351/75533909-14c07300-5a58-11ea-8d11-9b05a5447a34.PNG)
#### 2.2 Error Occurrence when add a row
~~~ 
cursor = db.cursor()
SQL = 'INSERT INTO purchaseinfo(userID, prodName, groupName, price, amount) VALUES('SES','운동화','의류',30,2)'
cursour.execute(SQL)
db.commit()
~~~
![외래키3](https://user-images.githubusercontent.com/58417351/75537527-a16c3080-5a5a-11ea-9253-9d29a743e510.PNG)
  + 'SES'라는 데이터가 userinfo의 userID를 참조하고 있기 때문에, 해당 테이블과 필드에 'SES'값이 있어야 함 (먼저 입력해줘야 함)
  + 현재 상황과 반대로 purchaseinfo 테이블에 관계된 userinfo에 있는 값을 삭제할 때 에러 발생
  + 데이터 무결성: 두 테이블 관계에 있어서, 데이터의 정확성을 보장하는 제약 조건을 넣음, 즉 foreign key는 제약 조건 중 하나
  + 실무에서는 비즈니스 로직이 다양하기 때문에, 꼭 필요한 경우에만 사용!

