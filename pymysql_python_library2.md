MySQL with PyMySQL python library2 ; Focusing on CRUD
---------------------------------------------------------------
1. [Data Insertion](#1-data-insertion)
2. [Data Retrieval](#2-data-retrieval) 
3. [Data Modification](#3-data-modification)
4. [Data Deletion](#4-data-deletion)

### 1. Data Insertion
  + declaration of cursor object : cursor = db.cursor()
  + execution of SQL : cursor.execute(sql)
  + confirmation of the reflection : db.commit()
  
#### 1-1. to insert only one row
~~~
import pymysql
db = pymysql.connect(host='localhost', port=3306, user='root', passwd='#####', db='ecommerce', charset='utf8')
cursor = db.cursor()

#하나의 row만 삽입하는 경우
sql = '''
    INSERT INTO product VALUES(
    '189842449','요즘에/봄신상10%할인/청바지/슬랙스/빅사이즈',32900,9900,69,'F');
    '''
cursor.execute(sql)
db.commit()
~~~
#### 1-2. to insert many rows 
~~~
import pymysql
db = pymysql.connect(host='localhost', port=3306, user='root', passwd='#####', db='ecommerce', charset='utf8')
cursor = db.cursor()

#여러 개의 row 삽입하는 경우, 반복 수만큼 execute()수행해야 함 
for index in range(1,11):
    product_code = 18984244 + index +1
    sql = '''INSERT INTO product VALUES(
    '''+str(product_code)+''','요즘에/봄신상10%할인/청바지/슬랙스/빅사이즈',32900,9900,69,'F');
    '''
    print(sql)
    cursor.execute(sql)

#마지막에 한 번만 commit 해주면 됨    
db.commit()
~~~

### 2. Data Retrieval
  + declaration of cursor object : cursor = db.cursor()
  + execution of SQL : cursor.execute(sql)
  + use cursor.fetch() method 
    - fetchall() : Fetch all the rows 
    - fetchmany(size=None) : Fetch several rows 
    - fetchone() : Fetch the first row 
    
#### 2-1. to fetch every row
~~~
import pymysql
db = pymysql.connect(host='localhost', port=3306, user='root', passwd='#####', db='ecommerce', charset='utf8')
cursor = db.cursor()

sql = 'SELECT * FROM product'
cursor.execute(sql)

#하나의 row가 tuple 형태로 반환 
result = cursor.fetchall()
for record in result:
  print(record)

db.close()
~~~
#### 2-2. to fetch the first row
~~~
import pymysql
db = pymysql.connect(host='localhost', port=3306, user='root', passwd='#####', db='ecommerce', charset='utf8')
cursor = db.cursor()

sql = 'SELECT * FROM product'
cursor.execute(sql)

result = cursor.fetchone()
print(result)

db.close()
~~~
### 3. Data Modification
  + declaration of cursor object : cursor = db.cursor()
  + execution of SQL : cursor.execute(sql)
  + confirmation of the reflection : db.commit()
~~~
import pymysql
db = pymysql.connect(host='localhost', port=3306, user='root', passwd='#####', db='ecommerce', charset='utf8')
cursor = db.cursor()

sql = '''
    UPDATE product SET 
    TITLE = '루나샵 봄신상티셔츠 5900원~ 맨투맨/원피스/박스티',
    ORI_PRICE = 32900, 
    DISCOUNT_PRICE = 9900, 
    DISCOUNT_PERCENT = 69
    WHERE PRODUCT_CODE = '18984246'
'''
cursor.execute(sql)

db.commit()
db.close()
~~~
### 4. Data Deletion
  + declaration of cursor object : cursor = db.cursor()
  + execution of SQL : cursor.execute(sql)
  + confirmation of the reflection : db.commit()
~~~
import pymysql
db = pymysql.connect(host='localhost', port=3306, user='root', passwd='#####', db='ecommerce', charset='utf8')
cursor = db.cursor()

sql='''
    DELETE FROM product WHERE PRODUCT_CODE = '18984247'
'''
cursor.execute(sql)

db.commit()
db.close()
~~~

 #### :page_facing_up: More about [MySQL with PyMySQL python library2](https://nbviewer.jupyter.org/gist/haeunello/4935478ddcc556670fa9faa9c0317209): jupyter file on jupyter nbviewer.  
