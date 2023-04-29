# @Embeddable

## 동기

* Aggregate 사용 대신 Value Object 를 사용하는것을 권장하기 때문에 나온 개념

## 특징

* Aggregate을 대신하는 객체
* 컬럼의 역할을 대신하여 처리해 주는 객체이다.

## 실제 사용 사례

```java
@Embeddable
@Data
@NoArgsConstructor
    public class MultilineText {
        @Column(name = "content")
        private String[] lines;

        public MultilineText(String text) {
            appendText(text);
        }

        @Override
    public String toString() {
        var stringBuilder = new StringBuilder();

        if (lines.length == 1) {
            stringBuilder.append(lines[0]);
        } else {
            Arrays.stream(lines).forEach(line -> stringBuilder.append(line + "\n"));
        }

        return stringBuilder.toString();
    }

    public void appendText(String text) {
        lines = text.split("\n");
    }
}
```

## 사용사례로 본 역할

* .NET 에서는 관계 매핑을 위해 사용되는데, 이는 JPA 에서는 객체지향을 위해 필드의 제약을 두는 역할이 주인것 같다.
