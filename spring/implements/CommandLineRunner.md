# CommandLineRunner

## 목적

* Spring Boot에서 애플리케이션을 실행할 때 특정 코드를 실행할때 사용한다.

## 사용법

```java
@Component
public class AppRunner implements CommandLineRunner {
 
    @Override
    public void run(String... args) throws Exception {
        // 실행할 코드
    }
}
```
