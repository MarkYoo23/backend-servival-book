
# Spring Encoding

## 문제점

스프링은 한글 인코딩 문제가 발생함

## 해결 방법

application.properties 파일에 관련 설정 추가.

```text
// 스프링의 기본값은 UTF-8 이다
server.servlet.encoding.charset=UTF-8

// 강제로 인코딩을 UTF-8로 설정해 주지않으면, 스프링에서는 인코딩을 하지 않는다.
server.servlet.encoding.force=true
```
