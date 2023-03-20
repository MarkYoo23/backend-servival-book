# DTO

## DTO란?

* [Data Transfer Object](https://martinfowler.com/eaaCatalog/dataTransferObject.html)
* 계층(Layer)간 데이터 교환을 위한 객체

### DTO 의 제약 조건

* 프로세스 간의 통신에 사용
* 퍼사드(Facade) 패턴을 사용하여 계층 간의 통신에 사용
* 네트워크에 있는 프로세스 간의 통신에 사용.

### DTO의 역할 및 특성

* 데이터를 담는다.
  * setter와 getter로만 이뤄짐.
  * [JavaBeans](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94%EB%B9%88%EC%A6%88)에서 유래한 [Java Bean](https://docs.spring.io/spring-framework/docs/6.0.x/reference/html/core.html#beans-introduction) 또는 그냥 Bean이라고 부르는 형태에 가까움

* 객체라고 보기 어렵다.(객체로서의 동작을 하지 않는다.)
* 무기력한 도메인 모델 
  * [“무기력한 도메인 모델” 안티패턴](https://martinfowler.com/bliki/AnemicDomainModel.html)

### DTO 의 백엔드 역할

* VO(Value Object)의 역할(= Entity의 역할)
* DTO 는 VO의 역할을 하기도 하고, VO의 역할을 하지 않기도 한다
* DB와 1:1 매핑하는 역할을 한다.

### F/N 와 B/N 사이의 역할

* F/N 에서 B/N으로 DTO를 사용하여 데이터를 전달한다.
* B/N 에서 F/N으로 DTO를 사용하여 데이터를 전달한다.

## IPC

* [Inter Process Communication](https://en.wikipedia.org/wiki/Inter-process_communication)

### IPC의 정의

* 서로 다른 프로세스, 다른 프로그램이 통신 하는 방법
* 예시로, 프론트의 프로그램(사용자 컴퓨터) 와 백엔드의 프로그램(서버 컴퓨터)에서 Tier간 통신 하는 방법을 들 수 있다.

### IPC 기술

* File
  * 가장 기본적인 접근. 원격 환경에서 활용하기 어렵다.
* Socket
  * 파일과 유사하게 읽고 쓸 수 있지만, 원격 환경에서도 활용 가능.
  * HTTP 고수준 프로토콜을 사용하여 접근 난이도를 낮춤
  * REST 를 활용하여 Resource 에 대한 CRUD로 정리
  * RPC(SOAP의 일반적인 활용) 를 이용하여 메소드 호출 형태로 사용 (Java에서는 RMI 형태로 사용)

### IPC의 종류

* RPC
  * [Remote Procedure Call](https://en.wikipedia.org/wiki/Remote_procedure_call)
* RMI
  * [Remote Method Invocation](https://en.wikipedia.org/wiki/Remote_method_invocation)

## 기타

### Jakarta EE

* 기존 JCP 정책이 아닌 오픈소스 기반의 자카르타EE 사양 프로세스(Jakarta EE Specification Process, JESP)라는 개방적이고 중립적인 정책을 채택

### Java Bean

```java

public class PersonBean implements java.io.Serializable
{
    private String name;
    private String address;
    private transient int SSN;
    private int number;

    public String getName()
    {
        return name;
    }

    public void setName(String newName)
    {
        name = newName;
    }

    public String getAddress()
    {
        return address;
    }

    public void setAddress(String newAddress)
    {
        address = newAddress;
    }

    public int getNumber()
    {
        return number;
    }

    public void setNumber(int newNumber)
    {
        number = newNumber;
    }
}
```

* DTO는 Java Bean의 일종이다.

* 엔터프라이즈 Java 에서 다루면 Java Bean 이라고 부른다.
* Spring 에서는 Spring Bean 이라고 부른다.

```C#

public class Person
{
    public string Name { get; set; }
    public string Address { get; set; }
    public int SSN { get; set; }
    public int Number { get; set; }
}
```

* C# 에서 Property Class 라고 부른다.
