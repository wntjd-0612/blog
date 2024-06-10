---
title: 싱글톤 패턴
description: 싱글톤 패턴을 알아보자
slug: cs1
date: 2024-06-09 00:00:00+0000
image: thumb.png
categories:
    - CS

tags:
    - 2
    - cs
    - python
weight: 1
---
# 디자인 패턴
## 디자인 패턴이란?
- 프로그램을 설계할 때 발생했던 문제점들을 객체 간에 상호 관계등을 이용하여 하나의 규약처럼 만들어 놓은 것을 의미합니다.

## 싱글톤 패턴
- 싱글톤 패톤은 하나의 클래스의 오직 하나의 인스턴트만 가지는 패턴입니다
 - 보통 데이터베이스연결 모듈에 자주 사용합니다.
- 하나의 인스턴트를 만들어 놓고 해당 인스턴트를 다른 모듈들이 공유하며 사용하기 때문에 인스턴트를 생성할 때 드는 비용이 줄어드는 장점이 있습니다
- 의존성이 높아진다는 단점이 있습니다.

## python의 싱글톤 패턴
```python
obj1 = {"a": 27}
obj2 = {"a": 27}

print(obj1 is obj2)
# False
print(obj1 == obj2)
# True
```
앞의 코드에서 볼 수 있듯이 obj1과 obj2는 다른 인스턴스를 가집니다.[^1]
```py
class Singleton(object):
    def __new__(cls, *args, **kwargs):
        if not hasattr(cls, "_instance"):         # Foo 클래스 객체에 _instance 속성이 없다면
            print("__new__ is called\n")
            cls._instance = super().__new__(cls)  # Foo 클래스의 객체를 생성하고 Foo._instance로 바인딩
        return cls._instance                      # Foo._instance를 리턴

    def __init__(self):
        print("__init__ is called\n")

s1 = Singleton()
s2 = Singleton()
print(s1)
print(s2)
```
위 코드를 실행하면 아래와 같이 출력됩니다. `__new__ is called`라는 문구가 한 번 출력됐음을 확인할 수 있고 s1과 s2라는 변수가 같은 주소의 객체를 바인딩하고 있음을 확인할 수 있습니다.

## 데이터베이스 연결모듈
그래서 이런 싱글톤을 어디다 쓸까?

보통 데이터베이스 연결 모듈에 많이 쓴다.[^2]
mongoDB와 연결하기 위해서 `pymongo`라이브러리를 사용해야합니다.
```bash
pip install pymongo
```


```python
from pymongo import MongoClient

class SingletonDB:
    _instance = None

    def __new__(cls, uri: str, db_name: str):
        if cls._instance is None:
            cls._instance = super(SingletonDB, cls).__new__(cls)
            cls._instance._initialize(uri, db_name)
        return cls._instance

    def _initialize(self, uri: str, db_name: str):
        self.client = MongoClient(uri)
        self.database = self.client[db_name]

    def get_client(self) -> MongoClient:
        return self.client

    def get_database(self):
        return self.database

    def close(self):
        self.client.close()

# 사용 예제
uri = "mongodb://localhost:27017/"
db_name = "example_db"

db1 = SingletonDB(uri, db_name)
db2 = SingletonDB(uri, db_name)

# 두 객체가 동일한지 확인
print(db1 is db2)  # True

# 데이터베이스 작업 예시
collection = db1.get_database()["users"]
collection.insert_one({"name": "Alice"})

result = collection.find_one({"name": "Alice"})
print(result)  # {"_id": ObjectId(...), "name": "Alice"}

# 연결 닫기
db1.close()

```
mysql도 한번 봐보자
```bash
pip install mysql-connector-python
```

```py
import mysql.connector
from mysql.connector import MySQLConnection

class SingletonDB:
    _instance = None

    def __new__(cls, host: str, user: str, password: str, database: str):
        if cls._instance is None:
            cls._instance = super(SingletonDB, cls).__new__(cls)
            cls._instance._initialize(host, user, password, database)
        return cls._instance

    def _initialize(self, host: str, user: str, password: str, database: str):
        self.connection = mysql.connector.connect(
            host=host,
            user=user,
            password=password,
            database=database
        )
        self.cursor = self.connection.cursor()

    def get_connection(self) -> MySQLConnection:
        return self.connection

    def get_cursor(self):
        return self.cursor

    def execute_query(self, query: str, params=None):
        self.cursor.execute(query, params)
        self.connection.commit()

    def fetch_all(self) -> list:
        return self.cursor.fetchall()

    def close(self):
        self.cursor.close()
        self.connection.close()

# 사용 예제
db1 = SingletonDB(host='localhost', user='your_username', password='your_password', database='your_database')
db2 = SingletonDB(host='localhost', user='your_username', password='your_password', database='your_database')

# 두 객체가 동일한지 확인
print(db1 is db2)  # True

# 데이터베이스 작업 예시
db1.execute_query('CREATE TABLE IF NOT EXISTS users (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(255))')
db1.execute_query('INSERT INTO users (name) VALUES (%s)', ("Alice",))

db1.execute_query('SELECT * FROM users')
result = db1.fetch_all()
print(result)  # [(1, 'Alice')]

# 연결 닫기
db1.close()
```

## 싱글톤 패턴의 단점


싱글톤은 TDD(Test Driven Development)를 할때 걸림돌이 된다.TDD할때 단위 케스트를 주로 하는데,단위 테스트는 테스트가 서로 독립적이여야 한다.
하지만 싱글톤은 미리 생성된 하나의 인스턴트를 기반으로 구현하는 것이기 때문에 테스트마다 독립적인 인스턴트를 만들기 어렵다,



[^1]: 값은 같다!
[^2]: 처음에 말했다.
