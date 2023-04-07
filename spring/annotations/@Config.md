# @Config

## 정의

* = Java Config

## 사용법

```java
    @Bean
    public PostRepository getPostRepository() {
        return new PostRepository();
    }

    @Bean
    public PostService getPostService() {
        return new PostService(new PostRepository());
    }
```

## 특징

* Singletone 으로 등록된다 (한번만 생성됨)
