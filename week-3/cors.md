# CORS

## [정의](https://developer.mozilla.org/ko/docs/Web/HTTP/CORS)

* Cross-Origin Resource Sharing
* 다른 출처의 리소스를 공유하는 것을 의미
* 다른 출처의 리소스를 공유하기 위해서는 CORS 정책을 준수해야 함
* CORS 정책을 준수하지 않으면 브라우저는 리소스를 차단함

## 동일 출처 정책

* 브라우저는 동일 출처 정책을 적용함
* 즉 http:example.com 에서 요청한 리소스는 http:example.com 에서만 사용 가능
* 별도의 설정이 없으면 다른 출처의 리소스는 사용할 수 없음
* 다른 출처의 리소스를 사용하려면 CORS 정책을 준수해야 함

## JSONP

* <script> 태그는 동일 출처를 따지지 않는다는 점을 이용한 방법

```html
<script>
    window.success = (data) => {
        // 얻은 데이터를 처리하는 코드
        console.log(data);
    }
</script>

<script src="http://server/posts?callback=success"></script>
```

## Access-Control-Allow-Origin

* Back-end, 즉 REST API의 응답 헤더에 “Access-Control-Allow-Origin” 속성을 포함시키면 브라우저는 CORS 정책을 준수한다고 판단하고 리소스를 사용할 수 있음

### 헤더에 포함

```java
@GetMapping
public List<PostDto> list(
    HttpServletResponse response
) {
    response.addHeader("Access-Control-Allow-Origin", "http://localhost:3000");
```

### 메서드 에서 설정

```java
@CrossOrigin(origins = "http://localhost:8080")
@GetMapping("/api/posts")
public List<Post> getPosts() {
    return postRepository.findAll();
}
```

### Controller 에서 설정

```java
@CrossOrigin(origins = "*", allowedHeaders = "*")
@RestController
public class PostController {
    // ...
}
```

### WebMvcConfigurer 에서 설정

```java
@Bean
public WebMvcConfigurer webMvcConfigurer() {
    return new WebMvcConfigurer() {
        @Override
        public void addCorsMappings(CorsRegistry registry) {
            registry.addMapping("/**")
                .allowedMethods("GET", "POST", "PATCH", "DELETE", "OPTIONS")
                .allowedOrigins("http://localhost:3000");
        }
    };
}
```

* .addMapping("/**") : 요청 URL이 모든 경로에 대해 아래 CORS 정책 적용(method, origin)
* .allowedMethods("GET", "POST", "PATCH", "DELETE", "OPTIONS") : GET, POST, PATCH, DELETE, OPTIONS 요청에 대해 CORS 정책을 적용
* .allowedOrigins("http://localhost:3000") : http://localhost:3000 에서 요청한 리소스에 대해 CORS 정책을 적용
