# Mokito

## 용어

* Mock : 진짜 객체와 비슷하게 동작하지만, 프로그래머가 직접 행동을 관리하는 객체

## 동기

* dao 또는 repository가 어떻게 작동하는지 구현 전에 테스트를 작성하기 위해 제작됨.

## 특징

* Mock 객체를 쉽게 만들고, 관리하고, 검증할 수 있는 방법을 제공하는 프레임워크
* dao 또는 repository가 어떻게 작동하는지에 대해서 대리 한다.
* Mockito는 기본으로 sprring-boot-starter-test 의존성에 같이 포함

## 역사

...(나중에 Mockito 발전 방향을 기록 하면 좋을 듯)

## 실제 사용 사례

```java
@ExtendWith(MockitoExtension.class)
class StudyServiceTest {

  // @Mock 을 사용하면, Mock 객체를 생성해준다.
  @Mock MemberService memberService;

  @Test
    void createStudyService(
        memberService,
        // 매개변수로 받는 곳에 @Mock 애노테이션을 붙히면 Mock 객체가 생성되어 주입
        @Mock StudyRepository studyRepository) {
        StudyService studyService = new StudyService(memberService, studyRepository);
        assertNotNull(studyService);
    }
}
```

## 참고 자료

* [Reference](https://javadoc.io/doc/org.mockito/mockito-core/latest/org/mockito/Mockito.html)
* [Blog](https://catsbi.oopy.io/a29ed4d0-49d3-44d3-bd24-154d6a7dc71f)
