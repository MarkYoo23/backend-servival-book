# Collection Pattren

## 패턴의 사용 방법

* 리소스의 이름에 복수형을 반드시 붙인다!

### 사례 X

```text
/the-first-post
```

### 사례 O

```text
/posts
```

```text
/posts/{id}
```

## 리소스의 구분

```text
/posts/{id}
```

에서

```text
/posts/1
```

-> URI

```text
1
```

-> 리소스의 ID

## 기능의 구현

* 디덱터리 구성
* 필터링 구성

### 댓글 사례

#### 사례 1

```text
/posts/{post_id}/comments
```

* 디렉터리처럼 구성

#### 사례 2

```text
/comments?post_id={post_id}
```

* 이렇게 쓰면 Post ID를 이용해 필터링한다는 의미

## 특수 케이스

* 단수형 사용
  * 그룹이 아닌 경우라면 그냥 단수형을 써도 된다.

### 세션

```text
/session
```

* 세션은 하나만 유지된다

### 에디터

```text
/edit?something
```

* 필터링으로 구성 가능하다.

```text
/pages/edit-post/{page-id}
```

* 좀더 Collection Pattern에 맞게 일관성 있게 처리해줄 수도 있다.