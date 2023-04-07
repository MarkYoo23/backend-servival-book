# system-under-test

## 특징

* 우리가 테스트하는 모든 것"의 줄임말

## 역사

* xUnit에서 처음 사용

## 실제 사용 사례

```java
// 변수 명으로 sut를 사용하는 경우가 많다.
public class CalculatorTest {
    @Test
    public void testAdd() {
        Calculator sut = new Calculator();
        int result = calculator.add(1, 2);
        assertEquals(3, result);
    }
}
```

## 참고 자료

* [Wiki](https://en.wikipedia.org/wiki/System_under_test)
* [xUnit](http://xunitpatterns.com/SUT.html)