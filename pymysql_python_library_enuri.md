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


