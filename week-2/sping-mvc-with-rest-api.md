# Spring MVC로 구현

## Controller 구현

```java
package com.mark.api.rest.demo.controllers;

import com.mark.api.rest.demo.exceptions.PostNotFound;
import org.springframework.http.HttpStatus;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/posts")
public class PostController {

    @GetMapping("/")
    public String list() {
        return "게시물 목록";
    }

    @GetMapping("/{id}")
    public String detail(@PathVariable("id") String id) {
        return "게시물 상세: " + id;
    }

    @PostMapping("/")
    @ResponseStatus(HttpStatus.CREATED)
    public String create(@RequestBody String body) {
        return "게시물 생성: " + body;
    }

    @PatchMapping("/{id}")
    public String update(@PathVariable("id") String id, @RequestBody String body) {
        return "게시물 수정: " + id + " with " + body;
    }

    @DeleteMapping("/{id}")
    public String delete(@PathVariable("id") String id) {
        return "게시물 삭제: " + id;
    }

    @ExceptionHandler(PostNotFound.class)
    @ResponseStatus(HttpStatus.NOT_FOUND)
    public String postNotFound(){
        return "게시물을 찾을 수 없습니다.\n";
    }
}
```

## 주요 기능

### @RestController

* @Controller + @ResponseBody

### @RequestMapping

* 클래스 레벨에 사용하면 해당 클래스의 모든 메소드에 URI 적용
* 메소드 레벨에 사용하면 해당 메소드에 URI 적용

### @GetMapping

* @RequestMapping(method = RequestMethod.GET)과 동일

### @PostMapping

* @RequestMapping(method = RequestMethod.POST)과 동일

### @PatchMapping

* @RequestMapping(method = RequestMethod.PATCH)과 동일

### @DeleteMapping

* @RequestMapping(method = RequestMethod.DELETE)과 동일

### @ExceptionHandler

* 해당 예외가 발생하면 해당 메소드를 실행

### @ResponseStatus

* 해당 메소드의 응답 코드를 지정
