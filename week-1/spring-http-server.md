<!-- markdownlint-disable MD033 -->
# Spring HTTP Server

## [소스](https://github.com/MarkYoo23/Toy_JavaHttp/pull/3)

## [Spring](https://docs.spring.io/spring-framework/docs/current/reference/html/overview.html#overview)

* Spring은 Java 언어를 위한 오픈 소스 애플리케이션 프레임워크.

* Spring은 애플리케이션 개발을 위한 다양한 서비스를 제공한다.

  * 의존성 주입(Dependency Injection)
  * AOP(Aspect Oriented Programming)
  * 트랜잭션 관리
  * 웹 애플리케이션 개발을 위한 MVC, REST API, WebSocket 등의 기능 제공
  * 데이터 액세스 기술과의 통합
  * 테스트 지원

## [Spring Boot](https://docs.spring.io/spring-boot/docs/current/reference/html/)

* Spring Boot는 Spring 프레임워크를 사용하는 애플리케이션을 쉽게 만들 수 있도록 도와주는 프레임워크이다.

* Spring Boot는 다음과 같은 특징을 가진다.

  * 스프링 애플리케이션을 쉽게 만들 수 있도록 도와준다.
  * 스프링 애플리케이션을 만들 때 필요한 많은 설정을 자동으로 해준다.
  * 스프링 애플리케이션을 만들 때 필요한 의존성을 자동으로 추가해준다.
  * 스프링 애플리케이션을 만들 때 필요한 많은 라이브러리들을 제공한다.

## [Sping Initalizer](https://start.spring.io/)

* Spring Boot 프로젝트를 쉽게 만들 수 있도록 도와주는 사이트이다.
* Spring Boot 프로젝트를 만들 때 필요한 의존성을 선택할 수 있다.

## Web Server

* Web Server
  * 클라이언트의 요청을 받아 정적인 파일을 제공한다
    * (HTML, CSS, Image)
  * 동적인 파일을 생성하여 제공하는 역할을 한다.
    * (Javascript)
* Web Application Server
  * 동적인 컨텐츠를 처리해주는 역할을한다.
    * (JSP, ...)
  * Tomcat
    * Java Servlet, JavaServer Pages(JSP), WebSocket 등을 실행할 수 있는 환경을 제공
    * Spring Boot는 기본적으로 Tomcat을 내장하고 있다.

## MVC

* MVC(Model-View-Controller)
  * Model
    * 데이터를 담고 있는 객체
  * View
    * 사용자에게 보여지는 화면
  * Controller
    * 사용자의 요청을 처리하는 객체
    * Model과 View를 연결해주는 역할을 한다.

## [Spring MVC](https://docs.spring.io/spring-framework/docs/current/reference/html/web.html#mvc)

* Spring MVC는 Spring 프레임워크에서 제공하는 MVC 프레임워크이다.

## JAVA Annotation

* 코드에 메타데이터를 추가하는 방법

### 인터페이스 생성

```java
@interface ExampleAnnotation {
    String method();
}
```

### Annotation 사용

```java
@interface ExampleAnnotation {
("This method does something useful.")
public void myMethod() {
    // ...
}
```

## Spring Annotation

### @RestController

* @RestController는 @Controller와 @ResponseBody를 합친 것과 같다.

#### @Controller

* @Controller는 Spring MVC에서 Controller를 의미한다.

#### @ResponseBody

* @ResponseBody는 메서드의 리턴값을 HTTP Response Body에 직접 쓰겠다는 의미이다.

### @RequestMapping

* URL을 컨트롤러의 메서드와 매핑할 때 사용
* 클래스나 메서드 선언부에 @RequestMapping과 함께 URL을 명시하여 사용

#### @GetMapping

* @GetMapping은 @RequestMapping(method = RequestMethod.GET)과 같다.

