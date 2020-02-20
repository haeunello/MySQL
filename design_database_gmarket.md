Design a small database using gmarket web page  
-----------------------------------------------

### 1. Create a database and tables
  + 'ecommerce' Database is referring to [GMARKET Bestsellers web page](http://corners.gmarket.co.kr/Bestsellers?viewType=G&groupCode=G01).
  + There are two tables, 'product' table and 'ranking' table. 
  + Tables were created without 'foreign keys'.
~~~
CREATE DATABASE ecommerce;
USE ecommerce;

CREATE TABLE product(
    PRODUCT_CODE VARCHAR(20) NOT NULL,
    TITLE VARCHAR(200) NOT NULL,
    ORI PRICE INT,
    DISCOUNT_PERCENT INT,
    DELIVERY VARCHAR(2),
    PRIMARY KEY (PRODUCT_CODE)
    );
DESC product;

CREATE TABLE ranking(
    ID INT UNSIGNED NOT NULL AUTO_INCREMENT,
    CATEGORY VARCHAR(50),
    SUBCATEGORY VARCHAR(50),
    RANKING INT NOT NULL,
    PRODUCT_CODE VARCHAR(20) NOT NULL,
    PRIMARY KEY (ID)
    );
DESC ranking;
~~~
### 2. Enter data into the tables
  + Five rows were entered into each table. 
~~~
INSERT INTO product VALUES(
'189842449','요즘에/봄신상10%할인/청바지/슬랙스/빅사이즈',32900,9900,69,'F');
INSERT INTO product VALUES(
'1725467202','루나샵 봄신상티셔츠 5900원~ 맨투맨/원피스/박스티',32900,9900,69,'F');
INSERT INTO product VALUES(
'166590202','[트라이] 여성팬티/여자팬티/팬티/여성속옷/여자속옷/면',33000,9900,70,'F');
INSERT INTO product VALUES(
'856191474','기모 맨투맨 티셔츠 오버핏 남자여자 단체티 빅사이즈',33000,10000,69,'F');
INSERT INTO product VALUES(
'1744240513','[지오다노] (현대백화점) 지오다노 C 119921/119522/118911 치노팬츠/슬랙스 3종 택1',29000,24070,17,'F');

SELECT * FROM product; 

INSERT INTO ranking VALUES(
1,'여성의류','바지/레깅스',1,'189842449');
INSERT INTO ranking VALUES(
2,'여성의류','티셔츠',2,'1725467202');
INSERT INTO ranking VALUES(
3,'언더웨어','여성 팬티',3,'166590202');
INSERT INTO ranking VALUES(
4,'남성의류','맨투맨/후드티',4,'856191474');
INSERT INTO ranking VALUES(
5,'브랜드 진/캐쥬얼','팬츠',5,'1744240513');

SELECT * FROM ranking;
~~~

<div>
<img height = '100' img width='500' src= 'https://user-images.githubusercontent.com/58417351/74925773-2c747780-5418-11ea-83dd-2819614b4af3.PNG'>
<img height = '100' img width='300' src= 'https://user-images.githubusercontent.com/58417351/74925798-3ac29380-5418-11ea-9cdb-8dfdec5a6d1b.PNG'>
</div>


