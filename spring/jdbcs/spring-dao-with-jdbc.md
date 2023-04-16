# Spring DAO with JDBC

## 조회

* 조회는 `query` 메서드를 사용한다.

```java
    public List<Post> findAll(){
        List<Post> posts = new ArrayList<>();

        var query = "SELECT * FROM posts";

        jdbcTemplate.query(query, resultSet ->{
            while(resultSet.next()){
                var id = resultSet.getString("id");
                var title = resultSet.getString("title");
                var post = new Post(id, title);
                posts.add(post);
            }
        });

        return posts;
    }
```

## 변경

* 변경은 `update` 메서드를 사용한다.

수정

```java
    public void update(Post post){
        var query = "UPDATE posts SET title = ? WHERE id = ?";
        jdbcTemplate.update(query, post.getTitle(), post.getId());
    }
```

삽입

```java
    public void add(Post post){
        var query = "INSERT INTO posts (id, title) VALUES (?, ?)";
        jdbcTemplate.update(query, post.getId(), post.getTitle());
    }
```

삭제

```java
    public void delete(Post post){
        var query = "DELETE FROM posts WHERE id = ?";
        jdbcTemplate.update(query, post.getId());
    }
```
