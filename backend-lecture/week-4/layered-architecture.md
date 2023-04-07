# Layered Architecture

## Separation of Concerns

* 번역 : 관심사의 분리

### 용어의 정리

* 링크
  * [위키](https://ko.wikipedia.org/wiki/%EA%B4%80%EC%8B%AC%EC%82%AC_%EB%B6%84%EB%A6%AC)
  * [MSDN](https://msdn.microsoft.com/ko-kr/library/ff649690.aspx)
* 요약
  * 계층 구조를 통해 관심사를 분리하는 것
    * 관심사 : 어떤 특정한 문제를 해결하기 위해 필요한 것
  * 결론 : 문제를 해결 하는 것(행위)를 특정 레이어(혹은 객체) 에 위임(구현) 함으로서 각 레이어의 자유도를 높힌다.

### 역사

* 객체 지향의 등장(1960)
  * [Smalltalk(1960)](https://en.wikipedia.org/wiki/Smalltalk) 에서 소개
  * 인물 : [Alan Kay](https://en.wikipedia.org/wiki/Alan_Kay)
  * 주요 개념 : 객체 지향
  * 주요 관심사를 분리한 객체들의 집합으로 프로그램을 구성하는 것이란 개념이 생김

* C언어의 등장(1972)
  * 모듈러 프로그래밍이 가능 해 짐(Dennis Ritchie 와 Ken Thompson 의 공동 개발)

* 파르나스의 모듈식 설계 원칙(1972)
  * 논문 : [On the Criteria to Be Used in Decomposing Systems into Modules(1972)](https://www.cs.umd.edu/class/spring2003/cmsc838p/Design/criteria.pdf) 에서 소개
  * 인물 : [David Parnas](https://en.wikipedia.org/wiki/David_Parnas)
  * 주요 개념 : 정보 은닉
  * 아마 모듈식 설계가 이 시점의 주 관심사 였을것으로 추정된다.

* 모듈식 설계의 등장(1970년대 후반 ~ 1980년대 초반)
  * 모듈화의 이점을 설명하고 모듈화를 위한 기법들을 제시했다.

* 대중화(1990 ~ 현재)
  * [Managing Complexity in Software Engineering(1990)](https://books.google.co.kr/books?id=uXtHeZt8ZowC&pg=PA5&dq=%22separation+of+concerns%22&hl=en&sa=X&ei=WQ_aUNn5DYjNiwLS54GADQ&redir_esc=y#v=onepage&q=%22separation%20of%20concerns%22&f=false)
  * [What Every Engineer Should Know About Software Engineering(2007)](https://books.google.co.kr/books?id=pFHYk0KWAEgC&pg=PA85&dq=%22separation+of+concerns%22&hl=en&sa=X&ei=WQ_aUNn5DYjNiwLS54GADQ&redir_esc=y#v=onepage&q=%22separation%20of%20concerns%22&f=false)
  * [Microsoft® Application Architecture Guide(2009)](https://books.google.co.kr/books?id=D9on897Ep7AC&pg=PT54&dq=%22separation+of+concerns%22+%22layered+design%22&hl=en&sa=X&ei=0xPaUKKJMITmiwKhiYDYCA&redir_esc=y)

### 특징

* 다층 구조 형태
  * [위키](https://ko.wikipedia.org/wiki/%EB%8B%A4%EC%B8%B5_%EA%B5%AC%EC%A1%B0)
  * 여러 층으로 이루어진 구조에서 데이터를 서로 주고 받도록 설계.

* 계층 형태
  * [정리](https://github.com/ahastudio/til/blob/main/architecture/layered-architecture.md#%EC%A0%84%ED%86%B5%EC%A0%81%EC%9D%B8-3%EA%B3%84%EC%B8%B5)
  * 전통적인 3계층
    * Presentation(UI + Controller) - Domain- Data
  * 에릭 에반스의 DDD
    * UI - Application - Domain - Infrastructure
    * 하위 레이어는 상위 레이어에 의존
    * 어플리케이션 레이어가 모든 기능 목록을 드러내고, 도메인 레이어의 협력 진입점을 만들어 낸다.

### 실제 사용 사례 & 경험

* DDD 기본 레이어 구조를 차용 하여 실무에서 개발
  * Application - Domain - Infrastructure 으로 데이터를 주고 받도록 사용
* 통신으로 연결된 온도 센서, 모터 드라이버 에서 통신을 담당하는 부분을 Nuget(라이브러리)화 하여 사용
  * 통신 부분을 모듈화 하여 사용
  * 통신 부분을 Nuget 으로 배포 하여 사용
  * 통신 부분을 테스트 하기 위해 통신 부분을 Mocking 하여 테스트

## 기타 개념

### Identifier

* 번역 : 식별
* 사용 이유 : 데이터의 고유한 값을 식별하기 위해 사용
* [위키](https://ko.wikipedia.org/wiki/%EC%8B%9D%EB%B3%84%EC%9E%90)

#### UUID

* [위키](https://ko.wikipedia.org/wiki/%EB%B2%94%EC%9A%A9_%EA%B3%A0%EC%9C%A0_%EC%8B%9D%EB%B3%84%EC%9E%90)
* Universally Unique Identifier

#### ULID

* [Github](https://github.com/ulid/spec)
* Universally Unique Lexicographically Sortable Identifier

#### TSID

* [Github](https://github.com/f4b6a3/tsid-creator)
* Time-Sorted Unique Identifiers
