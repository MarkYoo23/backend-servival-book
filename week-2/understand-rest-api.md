# Rest API 의 이해

## 작업의 분류

### 업무 영역

* Frontend
  * 사용자에 가까운 부분
  * 웹 프로그램 (ex : HTML, CSS, JavaScript 등을 이용한 프로그램 개발)
  * 윈도우 프로그램 (ex : WinForm, WPF 등의 프로그램 개발)
* Backend
  * 사용자에게서 먼 부분
  * 서버(ex : Tomcat 등의 WAS 위에 작동하는 Java Servlet, Spring 등의 웹 어플리케이션)

* 시스템의 구분
  * Tier : 물리적 구분
    * 클라이언트 컴퓨터와 서버 컴퓨터를 구분
  * Layer : 논리적 구분
    * 클라이언트 프로그램과 서버 프로그램을 구분

### 업무 영역을 연결 하는 방법

* 업무 영역을 연결해야 하는 이유
  * Frontend 와 Backend 는 서로 다른 프로그램이다.
  * Frontend 와 Backend 는 서로 다른 프로그램이기 때문에 서로 통신을 해야 한다.
  * 서로 통신을 하기 위해서는 통신 규약이 필요하다.
  
* 웹 통신 기술
  * 통신 규약
    * REST API
      * Representational State Transfer
      * '프로토콜'이 아님
        * 권장 사항의 구현 여부는 개발자에게 달려 있다
      * REST는 유연한 구현을 제공하는 가이드라인 세트
      * REST API는 경량화되어 있기 때문에 사물 인터넷(IoT), 모바일 애플리케이션 개발, 서버리스(servreless) 컴퓨팅과 같이 보다 새로운 컨텍스트에 이상적
    * SOAP
      * World Wide Web Consortium(W3C)에서 유지관리하는 공식 '프로토콜'
        * 권장 사항의 구현이 강제되어 있다.
      * SOAP는 XML 메시징과 같은 특정 요건이 있는 프로토콜
      * SOAP 웹 서비스는 많은 기업에서 필요로 하는 기본 보안과 트랜잭션 컴플라이언스를 제공하지만, 이로 인해 좀 더 무거운 경향
  * GraphQL
    * GraphQL은 애플리케이션 프로그래밍 인터페이스(API)를 위한 쿼리 언어
    * 서버측 런타임으로 클라이언트에게 요청한 만큼의 데이터를 제공
    * 개발자가 단일 API 호출로 다양한 데이터 소스에서 데이터를 끌어오는 요청을 구성할 수 있도록 지원
    * GraphQL은 Javascript 요청, API Gateway 형태로 많이 사용
  * Tomcat
    * WAS
    * 웹 어플리케이션을 동작 시켜줄 수 있는 서버
  * 자바 서블릿
    * ???

## GOF의 디자인 패턴

* 객체 지향을 위한 패턴.
* (TODO)추가 설명 적기

## API

* API - Application Programming Interface

* 인터페이스 효과
  * 통신
  * 명세
  * 정보 은닉
  * 캡슐화
  * 실행(implementation)
    * 프트웨어나 하드웨어 시스템을 설계한 후에 그것을 실제로 만들어내는 과정을 의미

## Rest

### 명칭

* Representational State Transfer

### 제약 조건

* Starting with the Null Style
* Client-Server
* Stateless
* Cacheable
* Uniform Interface
* Layered System
* Code on Demand (optional)

### Uniform Interface

* 균일한 인터페이스
* 일반성 원칙 --> 아키텍처 단순화, 가시성 향상
* 독립적인 진화를 장려
* 대용량 하이퍼미디어 데이터 전송에 효율적으로 설계
* 필딩 제약 조건
  * 인터페이스 제약 
    * URI 등으로 리소스를 식별할 수 있다.
    * 표현으로 리소스를 조작한다.
    * 메시지는 자기서술적이기 때문에 여러 레이어에서 처리/변환 가능
    * 하이퍼미디어를 통한 애플리케이션 상태 전이
  * 리소스 / 표현 구분
    * 리소스 : URI로 식별되는 것
    * 표현 → Data + Metadata + Meta-metadata
      * Data : 리소스의 상태
      * Metadata : 데이터에 대한 설명
      * Meta-metadata : 메타데이터에 대한 설명
    * HATEOAS
      * 표현에 선택 가능한 상태 전환이 포함 = 하이퍼 링크
      * API 문서를 참조해서 상태 전환을 강제
      * Richardson Maturity Model
