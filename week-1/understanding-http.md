# HTTP 이해하기

## HTTP 정의

* 분석
  * Hypertext :  한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트
  * Transfer : 전달
  * Protocol : 규약
* 정의 : 문서간의 정보를 주고 받는 통신 규약
* 레퍼런스
  * 'https://developer.mozilla.org/ko/docs/Web/HTTP'
  * 'https://developer.mozilla.org/ko/docs/Web/HTTP/Overview'
  * 'https://developer.mozilla.org/ko/docs/Web/HTTP/Messages'

## OSI 7 계층과 HTTP

* 구조
  * 2계층 : 데이터 링크 : Mac address
  * 3계층 : 네트워크 : IP address
  * 4계층 : 전송 : TCP, UDP (Port)
  * 7계층 : 응용 : HTTP, TLS
* HTTP의 위치
  * 7계층 : 응용

## HTTP의 특성

* 메시지 교환 방법
  * 리소스(서비스)
    * 대표적으로 URL
    * 'https://developer.mozilla.org/ko/docs/Web/HTTP/Basics_of_HTTP/Identifying_resources_on_the_Web'
  * 교환 방법
    1. 클라이언트 $\rightarrow$ 요청 $\rightarrow$ 서버
    2. 서버에서 데이터 처리
    3. 클라이언트 $\leftarrow$ 응답 $\leftarrow$ 서버
    * 2나 3의 과정이 없는경우, 클라이언트는 응답을 받을 수 없었음. (Timeout 으로 처리함)
* 무상태
  * HTTP는 각각 요청이 독립적이다 (=데이터를 계속해서 주고받아야 함)
      1. 쿠키가 요청 응답시 계속해서 주고 받음
      2. 세션 형태로 Key만 주고 받을 수도 있음
      3. Local Storage 형태도 가능
* 메시지 형태(Http Message)
  * 사람이 읽을수 있는 형태로 작성됨
  * 요청 응답이 같은 구조
    |항목|설명|내부|
    |:---|:---|:---|
    |Start Line| HTTP Request Message의 시작|HTTP method, Request target(req,res), HTTP version|
    |[Headers](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers)|해당 request에 대한 추가 정보 |General header, Request header, Response header, ...|
    |Empty Line|...||
    |Body|HTTP Request가 전송하는 데이터|바이너리(사람이 읽을 필요 없는 데이터), 파일, Json, ...|
* 메시지 요청 Method([Reference](https://developer.mozilla.org/ko/docs/Web/HTTP/Methods))
    |항목|설명|
    |:---|:---|
    |GET|Read|
    |HEAD|GET without body(=상태 코드만 받겠다)|
    |POST|Submit ([멱등성](https://developer.mozilla.org/ko/docs/Glossary/Idempotent))|
    |PUT|Update(+Create) ⇒ Overwrite|
    |PATCH|Update (partial) (멱등성X)|
    |DELETE|Delete|
    |OPTIONS|지원 확인([설명](https://velog.io/@awesome-hong/HTTP-Options-%EC%9A%94%EC%B2%AD%EC%9D%80-%EB%AD%98%EA%B9%8C))|
* 메시지 응답 Method([Reference](https://developer.mozilla.org/ko/docs/Web/HTTP/Status))
    |항목|설명|
    |:---|:---|
    |1xx | 정보 ⇒ 우리가 직접 쓰는 일은 드믐.|
    |2xx | 성공 ⇒ 200 OK, 201 Created, 204 No Content|
    |3xx | 리다이렉션 ⇒ 304 Not Modified가 특수한 형태로 자주 보임.|
    |4xx | 클라이언트 쪽 문제 ⇒ 404 Not Found (없는 데이터를 요청 했다.)|
    |5xx | 서버 쪽 문제 ⇒ 500 Internal Server Error(데이터 처리 중 오류가 발생하였다)|
