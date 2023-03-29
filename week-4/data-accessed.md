# Data Accessed

## Refactoring

### 리팩토링 용어의 정리

* [위키](https://ko.wikipedia.org/wiki/%EB%A6%AC%ED%8C%A9%ED%84%B0%EB%A7%81)
* Extract Method : 메서드 추출
* Extract Class  : 클래스 추출

* Presentation Domain Data Layering 용어
  * Presentation : 사용자 인터페이스와 도메인 로직을 연결하는 레이어, 사용자가 요청한 기능을 수행한다.
  * Domain : 도메인 로직을 구현하는 레이어, 비즈니스 로직을 구현한다.
    * Service : 도메인 로직을 구현하는 클래스, 절차지향적이다.
    * Model : 도메인의 데이터 및 동작을 표현하는 레이어, 객체지향적이다.
  * Data: 데이터베이스와 연결하는 레이어, 데이터베이스에 접근한다.
    * DAO : 데이터베이스와 연결하는 클래스, 데이터베이스에 접근한다.
    * DTO : 데이터베이스의 데이터를 담는 클래스

### 리팩토링의 역사

* 1999년 1월 1일 : 마틴 파울러 & 켄트 벡이가 '리팩토링'을 소개

### 리팩토링의 특징

* 외부 동작을 바꾸지 않으면서 내부 구조를 개선하는 방법이다.
* 코드를 읽고 이해하기 쉽게 만들고, 코드를 수정하기 쉽게 만든다.

### 실제 사용 사례

#### Before

SampleController.java

```java
public class SampleController{
    
    private List<Sample> samples;
    
    public Sample getSample(){
        var sample = samples.find(sample -> sample.getId() == 1);
        return sample;
    }
}
```

#### After (역할을 분리)

SampleController.java

```java
public class SampleController{
    
    @Autowired
    private SampleService sampleService;

    public Sample getSample(){
        var sample = sampleService.getSample(1);
        return sample;
    }
}
```
