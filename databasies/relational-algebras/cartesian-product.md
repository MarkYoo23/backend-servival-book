# Catesian Product

## 예시

### 표현식

* σ = Selection
* × = Cartesian Product

### 전제 조건

테이블

```sql
CREATE TABLE people
(
    name character varying(50) NOT NULL,
    age integer NOT NULL,
    gender character varying(50) NOT NULL,
    CONSTRAINT people_pkey PRIMARY KEY (name)
)

CREATE TABLE items
(
    name character varying(50) NOT NULL,
    item_name character varying(50) NOT NULL,
    useage character varying(50) NOT NULL,
    CONSTRAINT items_pkey PRIMARY KEY (name)
)
```

기본 데이터

```sql
INSERT INTO people(name, age, gender) VALUES ('a', '10', 'F');
INSERT INTO people(name, age, gender) VALUES ('b', '20', 'M');
INSERT INTO people(name, age, gender) VALUES ('c', '30', 'M');

INSERT INTO items(name, item_name, useage) VALUES ('a', 'item1', 'item 1 use');
INSERT INTO items(name, item_name, useage) VALUES ('b', 'item2', 'item 2 use');
INSERT INTO items(name, item_name, useage) VALUES ('c', 'item3', 'item 3 use');
```

## 곱집합 표현

### 곱집합 조회 쿼리

```sql
SELECT * FROM people, items;
```

### 곱집합 결과

|name|age|gender|name-2|item_name|useage    |
|----|---|------|------|---------|----------|
|a   |10 |F     |a     |item1    |item 1 use|
|a   |10 |F     |b     |item2    |item 2 use|
|a   |10 |F     |c     |item3    |item 3 use|
|b   |20 |M     |a     |item1    |item 1 use|
|b   |20 |M     |b     |item2    |item 2 use|
|b   |20 |M     |c     |item3    |item 3 use|
|c   |30 |M     |a     |item1    |item 1 use|
|c   |30 |M     |b     |item2    |item 2 use|
|c   |30 |M     |c     |item3    |item 3 use|

### 곱집합 특징

* row의 수는 9개이다.
* column의 두 테이블의 모든 column을 합친 것이다.

### 곱집합 해설

계산 해 보자면

* people 테이블의 a는 items 테이블의 a, b, c와 와 대응한다.
* people 테이블의 b는 items 테이블의 a, b, c와 와 대응한다.
* people 테이블의 c는 items 테이블의 a, b, c와 와 대응한다.

그렇다면 총 9개의 row 가 생성된다.

## colum 이름이 중복 되는 경우

```sql
SELECT R.name, S.money FROM R, S;
```

### 조인 하는 경우

```sql
SELECT * FROM R, S 
```

## 곱집합 중복 제거 표현

### 곱집합 중복 제거 쿼리

```sql
SELECT
 people.name,
 item_name
FROM 
 people, items
where 
 people.name = items.name
```

### 곱집합 중복 제거 결과

| name | item_name |
| ---- | --------- |
| a    | item1     |
| b    | item2     |
| c    | item3     |

### 곱집합 중복 제거 특징

* person.name, items.name 이 동일한것을 이용하여 제거 한다.
* 수식 : σ people.name = items.name (people × items)
* 두 테이블을 모두 체크한다. (2회 순회)

## 곱집합 조인

### 곱집합 조인 쿼리

```sql
SELECT
 people.name,
 item_name
FROM 
 people
JOIN
 items ON people.name = items.name
```

### 곱집합 조인 결과

| name | item_name |
| ---- | --------- |
| a    | item1     |
| b    | item2     |
| c    | item3     |

### 곱집합 조인 특징

* 어라? 결과 자체는 곱집합에서 중복 제거와 같다.
* people 테이블을 기준으로 items 테이블에서 조건에 따라 테이블을 만든다.
* 곱집합의 중복 제거보다 성능이 좋다. (1회만 순회)

## LEFT OUTER JOIN

* items 에서 c를 삭제하고 실행해 보자.

### LEFT OUTER JOIN 쿼리

```sql
SELECT
 people.name,
 item_name
 FROM 
 people
LEFT OUTER JOIN 
 items ON people.name = items.name
```

### LEFT OUTER JOIN 결과

| name | item_name |
| ---- | --------- |
| a    | item1     |
| b    | item2     |
| c    | null      |

### LEFT OUTER JOIN 특징

* items 테이블에 c가 없기 때문에 null이 나온다.
* 일반 조인임.

## RIGHT OUTER JOIN

* items 에서 c를 삭제하고 실행해 보자.

### RIGHT OUTER JOIN 쿼리

```sql
SELECT
 people.name,
 item_name
 FROM 
 people
RIGHT OUTER JOIN 
 items ON people.name = items.name
```

### RIGHT OUTER JOIN 결과

| name | item_name |
| ---- | --------- |
| a    | item1     |
| b    | item2     |

### RIGHT OUTER JOIN 특징

* items 테이블에 존재하는것만 표기된다.
