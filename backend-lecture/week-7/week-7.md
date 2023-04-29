# Week-7

## ORM

* JPA
  * JPA Entity
* Jakarta EE

## Hibernate

* Hibernate
* 데이터 모델 / 객체 모델
* entityManager
* 트랜잭션
* JPQL

## Relationship Mapping

* [DDD Aggregate](https://jaehoney.tistory.com/223)
  * 데이터 베이스의 정규화 처럼 단순화된 모델의 집합.
  * Aggregate는 하나의 논리적인 단위로서, 하나의 Aggregate에 속한 Entity들은 하나의 Transaction으로 처리되어야 한다.

## Spring Data JPA

* Spring Data JPA
* Dao 와 Repository 차이
  * Dao : .Net Context = 데이터베이스와 직접 연결을 하는 객체
  * Repository : 데이터베이스를 조작하는 방법을 정의하는 인터페이스?
* JPA Repository와 DDD의 Repository
  * JPA Repository : Spring 에 포함된 유틸리티
  * DDD Repository : Domain Layer 에서 사용하는 인터페이스
* Spring AOP
  * 객체형태로 컬럼을 제약하는 행위
* @Transactional
  * 행동에 트랜잭션을 걸어준다. 근데 불필요한 범위까지 트랜잭션 걸던데???

## 기타

* rombok 컴파일 오류 해결 [블로그](https://linux.systemv.pe.kr/spring-boot-error-constructor-in-class-cannot-be-applied-to-given-types-%EC%98%A4%EB%A5%98/)
