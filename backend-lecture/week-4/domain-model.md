# Domain Model

## 도메인 모델의 계층형 아키텍처

### 도메인 모델의 계층형 아키텍처 용어의 정리

* [도메인 모델 - 위키](https://ko.wikipedia.org/wiki/%EB%8F%84%EB%A9%94%EC%9D%B8_%EB%AA%A8%EB%8D%B8)

### 도메인 모델의 계층형 아키텍처 역사

* 2003년 11월 1일 : Eric Evans가 '도메인 모델'을 소개

### 도메인 모델의 계층형 아키텍처 특징

* Application Layer
  * 도메인 객체의 협력자에게 작업을 위임

* Domain Layer
  * 일반적인 객체! - 행위 위주의 객체이다.
  * Unit test를 작성 하기 적합한 존재이다.

* Infrastructure Layer
  * 데이터의 저장이 일어나는 계층이다.

* [DDD .Net 예시](https://learn.microsoft.com/ko-kr/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/ddd-oriented-microservice)

### 실제 사용 예시

#### Application Layer

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

#### Domain Layer

```java
public class SampleService{
    
    @Autowired
    private SampleRepository sampleRepository;

    public Sample getSample(int id){
        var sample = sampleRepository.findById(id);
        return sample;
    }
}
```

#### Infrastructure Layer

```java
public class SampleRepository{
    
    public Sample findById(int id){
        var sample = new Sample();
        sample.setId(id);
        sample.setName("sample");
        return sample;
    }
}
```

#### 실무에서 발생한 문제점

* 전 회사에서는 AnemicDomainModel 패턴을 주로 사용하였고, Model은 Entity 에서 상속 받아, 데이터를 주로 복사하여 전달하는 DTO 역할로 사용을 많이 하였다.
* 그렇다면 복잡성과, 데이터를 주고 받는 부분에서 효율을 생각하면.
  * Entity 가 DTO 역할을 동시에 하고
  * Model 은 Entity의 데이터를 처리 해 주며
  * Service는 Model을 절차 지향적으로 처리 하여, 각 Repository 에 전달 하는 형태가 가장 좋은것인가?
* 수업에서 따르면 Manager(메모리 데이터관리 객체) => Model => DAO => Repository 형태가 된다.
  * 캐싱을 할때 이때까지는, Manager(메모리 관리 객체) / Repository(DB 관리 객체) 형태로 사용하였다. 이것은 잘못 된 것이다.
  * Repository 하나가 캐싱 & DB 관리를 동시에 하고, Manager은 모델 영역으로 넘어가, 데이터를 가공, 처리 하는 역할을 하는것이 맞는것이다.

* 전 회사에서 Model 이 너무 많은 기능을 처리 함으로서 오히려 코드가 어려워지고 여러 오류가 발생하였다. (Inventory Management System) 예를 들어 InventoryStateRaw가 (Rack - Container - Sample 의 소스) 서비스를 통과 하면서, Auto Position 등의 너무 많은 기능을 넣다보니, 코드가 복잡해지고 오류가 발생하였다. 이는 Model Class 가 너무 많은 기능을 가져가게 되었고, Domain 모델이 가질 수 있는 안좋은 부분 같다. 이를 Service가 AnemicDomainModel 절차 지향적으로 처리함으로서 처리한다면 이득이 좀 더 되는것 아닐까? 싶다.

* Do you have an Anemic or Rich Domain Model? 에서 예시로 보여준 Service가 좀더 풍부하게 Repository를 다루며 Entity Model을 처리해 가는것이 정답 아닐까?

* IMS 도 서비스가 상태 전환을 이루어 내는 것만 메서드에서 처리했으면 좋았을것을.
  * 이전 구조 : 인벤토리 데이터 --> 인벤토리 상태
  * 이후 구조 : 인벤토리 데이터 --> 인벤토리 변경 요청 --> 인벤토리 상태

```C#
public class InventoryRawService{
    public InventoryStateRaw Parse(byte[] bytes){
        ...
    }
}

public class InventoryParseService{
    public IInventoryChangeRequest Parse(InventoryStateRaw raw){
        ...
    }
}

public class InventoryService{
    public void AppendRequest(IInventoryChangeRequest request){
        ...
    }
    ...
}
```

위와 같이 상태와 절차마다 각 서비스가 나누어서 처리하도록 하면 역할이 줄어들고, 코드가 간결해 질것 같다.


## 참고

* [AnemicDomainModel (안티패턴)](https://martinfowler.com/bliki/AnemicDomainModel.html)
* [Do you have an Anemic or Rich Domain Model?](https://dev.to/crovitz/have-you-anemic-or-rich-domain-model-2ala)
* [오브젝트 (강력 추천)](https://wikibook.co.kr/object/)

마켓컬리 사례:

* [Database Driven Development에서 진짜 DDD로의 선회 -1-](https://helloworld.kurly.com/blog/road-to-ddd/)
* [Database Driven Development에서 진짜 DDD로의 선회, 이벤트 스토밍 -2-](https://helloworld.kurly.com/blog/event-storming/)