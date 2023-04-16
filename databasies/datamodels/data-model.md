# 제목

## 동기

* 분석가가 하드웨어 의 모든 부분에 대한 문제를 구성할 수 있도록 하는 표기법 이 필요

## 특징

* 데이터 의 요소를 구성 하고 요소 간의 관계 및 실제 엔터티 의 속성과의 관계 를 표준화하는 추상 모델

크게 3가지로 구분

* Conceptual Data Model
* Logical Data Model
* Physical Data Model

## 역사

* 데이터 처리 문제의 정보 및 시간 특성을 지정하는 정확하고 추상적인 방법" 을 주장한 Young and Kent 에 의해 1958 등장
* 1960년대에 데이터 모델링이 정보 시스템 (MIS) 에 사용
* 1970년대에 엔터티-관계 모델링은 새로운 유형의 개념적 데이터 모델링으로 등장했으며 원래는 1976년 Peter Chen 에 의해 공식화
* 1997년에 그들은 Fully Communication Oriented Information Modeling FCO-IM 방법을 공식화

## 실제 사용 사례

```java
@Data
public class UserEntity {
    // Table의 Row와 매핑되는 객체
    private String id;
    private String name;
    private String email;
    private String password;
}
```

## 참고 자료

* [wikipedia](https://en.wikipedia.org/wiki/Data_model)
