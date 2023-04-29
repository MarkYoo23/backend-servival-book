# Domain Driven Development

## 정의

* 도메인 이란?
  * 사람들이 처리하는 물리적인 업무를 업무 전문가가 데이터를 처리하는 방법이다.

* 도메인 주도 개발
  * 전문가가 데이터를 처리하는 방식으로 소프트웨어를 개발하는 방법.
  * 이를 위해서 도메인이 활동할 환경을 조성하는데, 이를 레이어드 아키텍처로 분리 하였다.

## 레이어드 아키텍처

* 정의
  * 도메인 주도 개발을 위해 도메인이 활동할 환경을 조성할때, 어떠한 구조가 가장 효율적인가?
    * [참고](https://dev-coco.tistory.com/166) 에서 잘 설명해 두었다.

* 레이어드 아키텍처의 구조
  * Presentation Layer
    * (= Controller)
  * Application Layer
    * (= Service : 상호작용이 트랜잭션으로 보호됨, DTO : 이 상호작용의 결과를 반환, ...)
  * Domain Layer
    * (= Entity : 고유한 ID를 가진 모델 요소, Aggregate : 핵심 데이터를 처리하기 위한 구조로 엔티티와 동작이 합쳐져 있는 요소이다, ...)
  * Infrastructure Layer
    * (= Repository : 데이터베이스에 접근하는 객체 : 엔티티나 집합체를 실제로 어떻게 저장하고 조회할지를 구현 해 준다.)

## 닷넷 에서의 특징

* 특징
  * [레이어특징](https://learn.microsoft.com/ko-kr/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/net-core-microservice-domain-model)
    * Presentation Layer 을 Application 과 같이 구현한다 (=API)
    * Domain Layer 은 자바와 유사하게 사용.
    * Infrastructure Layer 은 자바 처럼 Hibernate 같은 편리함은 없고, 직접 Domain Entity 와 DB Entity(=Table)의 매핑을 진행 하여야 한다.

* 참고
  * [공식 문서 - 마이크로 서비스 관련](https://learn.microsoft.com/ko-kr/dotnet/architecture/microservices/)

## 자바 에서의 특징

* 특징
  * 위의 예제와 같이 구현되나, 자바에서는 Infrastructure Layer 에서 Repository 를 구현할때, JPA 를 사용하여 편리하게 구현할 수 있다.

* 참고
  * [mploed 의 예제](https://github.com/mploed/ddd-aggregate-example)

## 의문점

* 백기선님(자바 개발자 중에 유명한 분이라고 한다)의 수강생은 좀더 다르게 표현하였다.
  * Presentation Layer
    * (= Controller, dto)
  * Application Layer
    * (= Service : 상호작용이 트랜잭션으로 보호됨)
  * Domain Layer
  * Infrastructure Layer
* 해석에 차이가 있는건가?

* 닷넷의 [공식 예제](https://github.com/dotnet-architecture/eShopOnContainers) 에서는 Presentation Layer + Application 레이어가 필요에 따라 통합되어 있다.

## 도메인 주도 개발의 역사

* 1970년대
  * 데이터 중심의 시스템
  * 데이터를 중심으로 모델링
  * 데이터를 중심으로 모델링하면 데이터의 중복이 발생한다.
* 1980년대
  * 객체 지향의 시스템
  * 객체를 중심으로 모델링
  * 객체를 중심으로 모델링하면 객체의 중복이 발생한다.
* 1990년대 초반: 에릭 에반스가 DDD 개념을 소개
* 2003년: 에릭 에반스가 "도메인 주도 설계: 소프트웨어의 복잡성을 다루는 방법"이라는 책을 출판 이 책은 DDD를 설명하고 구현하는 방법에 대한 상세한 지침을 제공
* 2004년: 많은 개발자들이 DDD에 대한 관심을 가지게 되며, DDD 커뮤니티가 형성
* 2007년: 에릭 에반스가 "도메인 주도 설계 핵심"이라는 책을 출판 이 책은 DDD를 좀 더 심도있게 다룹니다.
* 2011년: 버버 스태프(Vaughn Vernon)가 "도메인 주도 설계 구현"이라는 책을 출판 이 책은 DDD를 구현하는 방법에 대한 실용적인 가이드를 제공
* 2013년: DDD 커뮤니티에서는 이벤트 소싱(Event Sourcing)과 CQRS(Command Query Responsibility Segregation)와 같은 새로운 패턴이 등장
