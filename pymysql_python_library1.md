MySQL with PyMySQL python library1 ; connection and execution
---------------------------------------------------------------

### 1. Connect to MySQL DB server
  + install PyMySQL python library
  + use pymysql.connect() method to connect DB server
  + parameters
    - host : server address / host='localhost' : my PC
    - port : server port number
    - user : mysql ID
    - passwd: passward of mysql ID
    - db: the name of DB
    - charset = 'utf8' to use Hangul
  + cursor : control structure of database
  ~~~
 #import library 
 import pymysql
 
 #접속(connection) 객체 선언
 db = pymysql.connect(host='localhost', port=3306, user='root', passwd='#####', db='ecommerce', charset='utf8')
 
 #실제 명령을 받을 수 있는 상태를 얻기위해 cursor 객체 선언
 cursor = db.cursor()
 ~~~
 ### 2. Execute sql using cursor object
 
  + use cursor.execute() method 
  + after execution (INSERT, UPDATE,DELETE,etc), connetion object.commit() method should be used 
  
  ~~~
  sql = '''
      CREATE TABLE product(
        PRODUCT_CODE VARCHAR(20) NOT NULL,
        TITLE VARCHAR(200) NOT NULL,
        ORI_PRICE INT,
        DISCOUNT_PRICE INT,
        DISCOUNT_PERCENT INT,
        DELIVERY VARCHAR(2),
        PRIMARY KEY (PRODUCT_CODE)
        );
   '''
   #실행
   cursor.execute(sql)
   
   #실행한 작업에 대한 검증을 마친 후 DB에 commit 
   db.commit()
   
   #작업을 마친 후 DB 연결을 닫음 
   db.close()
   ~~~
    
 #### :page_facing_up: More about [MySQL with PyMySQL python library1](https://nbviewer.jupyter.org/gist/haeunello/f86c0e1438bb3b031dd8e4ceac1ea299): jupyter file on jupyter nbviewer.  
 
 
 
