# 10주차

## 어플리케이션 수준의 보안

* 의미
  * 어플리케이션 수준 = 통신을 할 때, 어플리케이션의 표현 계층에서 보안을 하는 것

* 항목
  * 인증(Authentication) & 인가(Authorization)
  * Http state less : http 통신은 상태를 보존하지 않는 통신이기때문에 항상 서로 가지고 있는 정보를 통해 확인을 하여야 한다.
  * 쿠키(Cookie) & 로컬 스토리지(Local Storage)
  * Intercepter & Filter
  * 암호화 & 복호화
    * 단방향 암호화
    * 양방향 암호화
    * 해시 알고리즘
    * Salt 의 필요성

## 인증

* Identifier
* **[PostgreSQL](https://www.postgresql.org/)**
* OAuth 2.0
  * 별도로 정리됨.
* Bearer Token 옵션
  * 별도로 정리됨
* SecurityFilterChain
  * 필터 => 필터는 Http 요청시 마다 실행되는 절차.
* `@Configuration`
  * 설정 파일 불러오는 부분
* `@EnableWebSecurity`
  * ..?
* Filter vs OncePerRequestFilter
* FilterChain
* SecurityContext

## 로그인 & 로그아웃

* CSRF(Cross Site Request Forgery***)
  * 사용자가 의도하지 않은 요청을 보내는 공격 기법
* 자바 Date vs LocalDateTime
  * 자바 Date는 deprecated 되었음.
  * LocalDateTime은 자바 8부터 지원
* Epoch Time
  * 1970년 1월 1일 0시 0분 0초를 기준으로 경과한 시간을 초 단위로 나타낸 것
* Spring Security PasswordEncoder
* Argon2
  * 단방향 암호화 알고리즘
  * 2020년 10월 기준으로 가장 안전한 알고리즘

## 회원가입

* TSID(Time-Sorted Unique Identifiers)

## JWT

* JWT
  * 별도 정리됨
* Claims*based identity
  * 별도 정리됨
* 대칭키 암호화 / 공개키 암호화
  * 별도 정리됨
* `@Secured`
  * ?
