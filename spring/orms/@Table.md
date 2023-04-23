# @Table

## 사용 방법

```java
@Entity
@Table(name = "posts")
@Data
@AllArgsConstructor
@NoArgsConstructor
public class Post {
    @Id
    @Column(name = "id")
    private PostId id;

    @Column(name = "title")
    private String title;

    @Column(name = "author")
    private String author;

    @Column(name = "content")
    private MultilineText content;
}
```

## 해석

* @Table 은 데이터베이스의 Table 과 1:1로 매핑된다.
* @Table 의 name 속성을 통해 매핑할 테이블의 이름을 지정할 수 있다.
* @Id 를 통해 Primary Key 를 지정할 수 있다.
* @Column 을 통해 테이블의 컬럼과 매핑할 수 있다.

## 결론

* @Entity 를 통해 JPA 가 관리하는 객체임을 알리고, @Table 을 통해 상세 조건을 기술한다.
