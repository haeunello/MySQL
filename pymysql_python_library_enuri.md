Handling small database with PyMySQL using enuri web page 
----------------------------------------------------------
  + 'enuri' Database is referring to [ENURI CPU & Cooler web page](http://www.enuri.com/list.jsp?cate=070701).
  +  PyMySQL python library is used.

## 1. Check existing databases and create a new one
### 1-1. to check existing databases
~~~
sql ='''
SHOW DATABASES
'''
cursor.execute(sql)
result = cursor.fetchall()
print(result)
~~~
### 1-2. to create new DB called 'enuri'
~~~
sql ='''
CREATE DATABASE enuri
'''
cursor.execute(sql)

sql ='''
USE enuri
'''
cursor.execute(sql)
~~~
## 2. Create 'product' table
  + columns in 'product' table :
    - product_ID : (primary key) int, unsigned, not null, auto_increment
    - product_name : varchar(100), not null
    - product_num : varchar(20), not null
    - model_type : varchar(50), not null
~~~
sql = '''
CREATE TABLE product(
    product_ID INT UNSIGNED NOT NULL AUTO_INCREMENT,
    product_name VARCHAR(100) NOT NULL,
    model_num VARCHAR(20) NOT NULL,
    model_type VARCHAR(50) NOT NULL,
    PRIMARY KEY(product_ID)
    )
'''
cursor.execute(sql)
db.commit()
~~~
## 3. Insert data in 'product' table 
### 3-1. to insert a Top 10 List based on the web page
~~~  
sql_list = [
'''INSERT INTO product VALUES(34128722,'i5','9400F','커피레이크')''',
'''INSERT INTO product VALUES(32119847,'i7','9700K','커피레이크')''',
'''INSERT INTO product VALUES(35912378,'i5','9600KF','커피레이크')''',
'''INSERT INTO product VALUES(38566402,'i7','9700','커피레이크')''',
'''INSERT INTO product VALUES(32119845,'i5','9600K','커피레이크')''',
'''INSERT INTO product VALUES(35913093,'i7','9700KF','커피레이크')''',
'''INSERT INTO product VALUES(37471002,'i5','9700F','커피레이크')''',
'''INSERT INTO product VALUES(41033611,'셀러론','G4930','커피레이크')''',
'''INSERT INTO product VALUES(32119849,'i9','9900K','커피레이크')''',
'''INSERT INTO product VALUES(37117677,'i3','9100F','커피레이크')''']

for sql in sql_list:
    cursor.execute(sql)

db.commit()
~~~
### 3-2. to review data 
~~~
sql = '''
SELECT * FROM product
'''
cursor.execute(sql)
result = cursor.fetchall()

for record in result:
    print(record)

db.close()
~~~

#### :page_facing_up: More about [Handling small database with PyMySQL using enuri web page](https://nbviewer.jupyter.org/gist/haeunello/749b7d78f03913f0e7559b21330f7d81): jupyter file on jupyter nbviewer.  

