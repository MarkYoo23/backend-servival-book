
<!-- markdownlint-disable MD033 -->
# JAVA HTTP Server

## Keywords

### Java HTTP Server

* [소스코드](https://github.com/MarkYoo23/Toy_JavaHttp/pull/2/files)

#### 바인딩

```java
var hiContextFactory = new HiContextFactory();
httpServer.createContext("/hi", hiContextFactory.create());
```

#### 요청 내용 표시

```java
private void displayRequest(HttpExchange exchange) throws IOException {
    System.out.println("method" + exchange.getRequestMethod());
    System.out.println("path" + exchange.getRequestURI().getPath());

    var headers = exchange.getRequestHeaders();

    for (String key : headers.keySet()) {
        var values = headers.get(key);
        System.out.println(key + ": " + values);
    }

    String inputBody = new String(exchange.getRequestBody().readAllBytes());
    System.out.println(inputBody);
}
```

#### 응답 방법

```java
private void sendContent(HttpExchange exchange, String content) throws IOException {
      var contentBytes = content.getBytes();

      exchange.sendResponseHeaders(200, contentBytes.length);

      var outputStream = exchange.getResponseBody();
      outputStream.write(contentBytes);
      outputStream.flush();
  }
```

### Java NIO

* NIO
  * Non-blocking I/O

### Java Lambda expression(람다식)

* 정의
  * Anonymous Function

#### [Example](https://www.w3schools.com/java/java_lambda.asp)

type 1

```java
parameter -> expression
```

type 2

```java
(parameter1, parameter2) -> expression
```

type 3

```java
(parameter1, parameter2) -> { code block }
```

#### Java Functional interface(함수형 인터페이스)

사용한 인터페이스

```java
public interface HttpHandler {
    public abstract void handle (HttpExchange exchange) throws IOException;
}
```

예시 2

```java
@FunctionalInterface
interface CustomInterface<T> {
    // abstract method 오직 하나
    T myCall();

    // default method 는 존재해도 상관없음
    default void printDefault() {
        System.out.println("Hello Default");
    }

    // static method 는 존재해도 상관없음
    static void printStatic() {
        System.out.println("Hello Static");
    }
}
```

* 예외사항
  * default method, static method 사용 가능

* 기타
  * 자바에서 제공하는 기본 함수형 인터페이스도 있음
    * [java.util.function](https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html)

  * @FunctionalInterface 어노테이션은 자바 8부터 추가된 어노테이션