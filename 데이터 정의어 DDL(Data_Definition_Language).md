<img src="https://capsule-render.vercel.app/api?type=waving&color=auto&height=200&section=header&text=DDL&fontSize=90" />

## DDL Data Definition Language 데이터 정의어
데이터베이스 객체를 정의하고 조작하는데 사용되는 명령어 집합 

CREATE: 테이블, 뷰, 인덱스 등 데이터베이스 객체를 생성합니다.
ALTER: 이미 존재하는 테이블, 뷰, 인덱스 등 데이터베이스 객체를 수정합니다.
DROP: 데이터베이스 객체를 삭제합니다.
TRUNCATE: 테이블에서 모든 데이터를 삭제합니다.
RENAME: 데이터베이스 객체의 이름을 변경합니다.
COMMENT: 데이터베이스 객체에 대한 주석을 추가합니다.

## CREATE
테이블 , 데이터베이스 등 DB 객체를 생성하는 명령어

데이터베이스 생성
```sql
CREATE DATABASES;
```

테이블 생성
```sql
CREATE TABLE 테이블명 (
  컬럼명 타입 조건,
  컬럼명 타입 조건
);
```

### 제약조건
NOT NULL : NULL 비허용
```sql
CREATE TABLE mytable (id INT NOT NULL, name VARCHAR(50));
```

UNIQUE : 중복 값 비허용
```sql
CREATE TABLE mytable (
id INT UNIQUE KEY, name VARCHAR(50));
```

PRIMARY KEY : 기본키로 지정 ( 기본키는 테이블 당 한개 , NOT NULL , UNIQUE 의 특성을 둘다 지님)
```sql
CREATE TABLE mytable (
  id INT PRIMARY KEY,
  name VARCHAR(50));
```

FOREGIN KEY : 외래키 ( 중복되지 않는 값이어야 한다. UNIQUE OR UNIQUE를 포함한 PRIMARY KEY)
```sql
CREATE TABLE orders (
  order_id INT PRIMARY KEY, 
  customer_id INT, FOREIGN KEY (customer_id) REFERENCES customers(customer_id));
```
CHECK : 특정 조건을 줘서 그 조건에 만족하는 값만 들어올 수 있게 한다.
```sql
CREATE TABLE mytable (
  age INT CHECK (age >= 18));
```
INDEX : 인덱스 지정
```sql
CREATE TABLE mytable (
  id INT, name VARCHAR(50),INDEX(id));
```
auto_increment : 자동으로 증가하는 숫자 생성 주로 기본키에 사용
```sql
CREATE TABLE mytable (
   id INT PRIMARY KEY AUTO_INCREMENT,
   name VARCHAR(50),
   age INT
);
```
