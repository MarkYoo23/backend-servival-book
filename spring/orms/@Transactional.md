# @Transactional

## 정의

* 행동에 트랜잭션을 걸어 데이터 손상을 방지

## 예시

```java
@Transactional
@Service
public class CreatePostService {
    private final PostRepository postRepository;

    @Autowired
    public CreatePostService(PostRepository postRepository) {
        this.postRepository = postRepository;
    }

    public PostReadDto execute(PostCreateDto dto) {
        var model = new Post(PostId.gene(), dto.getTitle(), dto.getAuthor(), new MultilineText(dto.getContent()));
        postRepository.save(model);

        return new PostReadDto(model);
    }
}
```

## 문제점?

```java
@Transactional
@Service
public class UpdatePostService {
    private final PostRepository postRepository;

    @Autowired
    public UpdatePostService(PostRepository postRepository) {
        this.postRepository = postRepository;
    }

    public PostReadDto execute(String postId, PostUpdateDto reqBody) throws PostNotFoundException {

        var optionalModel = postRepository.findById(postId);
        if(optionalModel.isEmpty()){
            throw new PostNotFoundException();
        }

        var model = optionalModel.get();
        model.setTitle(reqBody.getTitle());
        model.getContent().appendText(reqBody.getContent());

        postRepository.save(model);

        return new PostReadDto(model);
    }
}
```

* 위와 같이 '조회' 부분에서 트랜잭션은 불필요하다.
* 트랜잭션은 '변경' 부분에서만 필요하다.
* 그렇다면 이걸 어떻게 해결할까?

## 해결

```java
package kr.megaptera.assignment.applications;

import jakarta.transaction.Transactional;
import kr.megaptera.assignment.dtos.posts.PostReadDto;
import kr.megaptera.assignment.dtos.posts.PostUpdateDto;
import kr.megaptera.assignment.exceptions.PostNotFoundException;
import kr.megaptera.assignment.models.posts.Post;
import kr.megaptera.assignment.repositories.PostRepository;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class UpdatePostService {
    private final PostRepository postRepository;

    @Autowired
    public UpdatePostService(PostRepository postRepository) {
        this.postRepository = postRepository;
    }

    public PostReadDto execute(String postId, PostUpdateDto reqBody) throws PostNotFoundException {

        var optionalModel = postRepository.findById(postId);
        if(optionalModel.isEmpty()){
            throw new PostNotFoundException();
        }

        var model = optionalModel.get();
        model.setTitle(reqBody.getTitle());
        model.getContent().appendText(reqBody.getContent());

        update(model);

        return new PostReadDto(model);
    }

    @Transactional
    public void update(Post post){
        postRepository.save(post);
    }
}
```

* 위와 같이 트랜잭션 범위를 제한함으로서 문제를 해결할 수 있다.
* [참고자료](https://kapentaz.github.io/spring/Spring-Transaction-%EC%A0%81%EC%9A%A9-%EB%B2%94%EC%9C%84-%EC%A0%9C%EC%96%B4-%EB%B0%A9%EB%B2%95/#)