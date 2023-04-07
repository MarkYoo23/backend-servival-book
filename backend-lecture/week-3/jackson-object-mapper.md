# Jackson Object Mapper

## 기본

```json
{
    "title": "title",
    "content": "content"
}
```

```java
@Data
public class PostDto
{
    private long id;
    private String title;
    private String content;

    public PostDto(long id, String title, String content)
    {
        this.id = id;
        this.title = title;
        this.content = content;
    }

    // 아래와 같이 직접 프로퍼티를 지정 할 수 있다.
    @JsonProperty("title")
    public String getTitle()
    {
        return title;
    }
}
```

## How to use

```java

@RestController
@RequestMapping("/posts")
public class PostController{

    @Autowired
    private ObjectMapper objectMapper;

    // spring boot가 알아서 jackson을 사용해서 json으로 변환해준다. 
    @GetMapping
    public List<PostDto> getPosts(){
        List<PostDto> postDtos = List.of(
            new PostDto(1L, "title1", "content1"),
            new PostDto(2L, "title2", "content2"),
        )

        return postDtos;
    }

    // 직접 jackson을 사용해서 json으로 변환 해 주었다.
    @GetMapping("/{id}")
    public String detail(@PathVariable String id) throws JacksonException {
        PostDto postDto = new PostDto(id, "제목", "내용");
        return objectMapper.writeValueAsString(postDto);
    }
}
```

* 우리가 Jackson을 바로 쓸 수 있는 건 Spring Boot가 Jackson을 지원하기 때문. 변환 또한 Spring Boot가 알아서 해주기 때문에 실제로는 아주 쉽고 자연스럽게 쓸 수 있다.