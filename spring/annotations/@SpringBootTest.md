# @SpringBootTest

## 링크

* [Testing](https://docs.spring.io/spring-framework/docs/current/reference/html/testing.html)

## 원문

Spring Boot provides a number of utilities and annotations to help when testing your application. Test support is provided by two modules: spring-boot-test contains core items, and spring-boot-test-autoconfigure supports auto-configuration for tests.

## 번역

Spring Boot는 애플리케이션을 테스트할 때 도움이 되는 다양한 유틸리티와 어노테이션을 제공합니다. 테스트 지원은 두 가지 모듈에 의해 제공됩니다. spring-boot-test에는 핵심 항목이 포함되어 있고 spring-boot-test-autoconfigure는 테스트를 위한 자동 구성을 지원합니다.

## 특징

* 실제 어플리케이션을 자신의 로컬위에 올려서 포트가 Listening 되고, DB와 커넥션이 연결되어 있는 상태에서 테스트를 진행한다.

## 비교 대상

* WebMvcTest  

## 사용 방법

```java
@SpringBootTest(webEnvironment = WebEnvironment.RANDOM_PORT)
class PostFeatureTest {
 @Value("${local.server.port}")
 private int port;
 
 @Autowired
 private TestRestTemplate restTemplate;
 
 @Test
 public void post() {
  String url = "http://localhost:" + port + "/posts";
  
  PostDto postDto = new PostDto("ID", "새 글", "제곧내");
  
  restTemplate.postForLocation(url, postDto);
  
  String body = restTemplate.getForObject(url, String.class);
  
  assertThat(body).contains("새 글");
  assertThat(body).contains("제곧내");
  
  String id = findLastId(body);
  
  restTemplate.delete(url + "/" + id);
  
  body = this.restTemplate.getForObject(url, String.class);
  
  assertThat(body).doesNotContain("새 글");
 }
 
 private String findLastId(String body) {
  Pattern pattern = Pattern.compile("\"id\":\"([^\"]+)\"");
  Matcher matcher = pattern.matcher(body);
  
  String id = ""; 
  while (matcher.find()) {
   id = matcher.group(1);
  }  
  return id;
 }
}
```
