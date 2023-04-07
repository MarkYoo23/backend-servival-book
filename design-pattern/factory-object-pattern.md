# Factory Object Pattern

## 링크

* [Wiki](https://en.wikipedia.org/wiki/Factory_(object-oriented_programming)

## 용어 정리

* 주로 Factory Object 를 뜻함.

## 역사

* Gof 디자인 패턴 에서 등장: 1995년

## 동기

* 프로토타입 기반 프로그래밍에서 파생된 패턴
* 응용 프로그램에 클래스가 종속되지 않도록 관리할 필요가 발생

## 특징

* 생성 패턴
* 객체를 직접 만들지 않고, 객체를 생성하는 책임만 가진 객체를 만들어서 쓴다.
* SRP(Single Responsibility Principle) 을 준수한다.

## 실제 사용 사례

* [Spring Bean](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-factory)
  * BeanFactory 를 통해 Bean 을 생성한다.

* [Spring AOP](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#aop-introduction-factory)
  * ProxyFactoryBean 을 통해 Proxy 를 생성한다.

* [.Net DI](https://learn.microsoft.com/en-us/dotnet/core/extensions/dependency-injection)
  * DI 를 통해 객체를 생성한다.

## 예시

### 일반

```java
// 객체를 생성하는 책임만 가진 객체
public class Factory {
    public Product create() {
        return new ProductA();
    }
}
```

### With singleton

```java
public class PostRepositoryFactory {

  private static PostRepositoryFactory instance;

  public PostRepository create(){
    if(instance == null){
      instance = new PostRepositoryFactory();
    }

    return instance;
  }
}
```

## 관계

* Layered Architecture : 구현을 위해 사용
