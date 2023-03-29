<img src="https://capsule-render.vercel.app/api?type=waving&color=auto&height=200&section=header&text=DDL&fontSize=90" />

## DDL Data Definition Language 데이터 정의어
데이터베이스 객체를 정의하고 조작하는데 사용되는 명령어 집합 <br>

CREATE: 테이블, 뷰, 인덱스 등 데이터베이스 객체를 생성합니다.<br>
ALTER: 이미 존재하는 테이블, 뷰, 인덱스 등 데이터베이스 객체를 수정합니다.<br>
DROP: 데이터베이스 객체를 삭제합니다.<br>
TRUNCATE: 테이블에서 모든 데이터를 삭제합니다.<br>
RENAME: 데이터베이스 객체의 이름을 변경합니다.<br>
COMMENT: 데이터베이스 객체에 대한 주석을 추가합니다.<br>

<hr>

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
<hr>

## ALTER

ALTER 명령어는 테이블의 구조를 변경하는 데 사용

테이블 이름 변경하기

```sql
ALTER TABLE old_table_name RENAME new_table_name;
```

테이블에 새로운 컬럼 추가하기

```sql
ALTER TABLE table_name ADD column_name data_type;
```

테이블의 컬럼 이름 변경하기

```sql
ALTER TABLE table_name CHANGE old_column_name new_column_name data_type;
```

테이블의 컬럼 삭제하기

```sql
ALTER TABLE table_name DROP column_name;
```

테이블의 컬럼 순서 변경하기

```sql
ALTER TABLE table_name MODIFY column_name data_type AFTER another_column_name;
```


테이블의 기본키(primary key) 설정하기

```sql
ALTER TABLE table_name ADD PRIMARY KEY (column_name);
```

테이블의 외래키(foreign key) 설정하기

```sql
ALTER TABLE table_name ADD CONSTRAINT constraint_name FOREIGN KEY (column_name) REFERENCES foreign_table_name (foreign_column_name);
```

<br>
위와 같은 ALTER 명령어를 사용하여 테이블 구조를 변경할 수 있습니다. 이 때, 테이블이나 컬럼에 대한 변경 사항이 크다면, 데이터의 백업을 해 두는 것이 좋습니다.
