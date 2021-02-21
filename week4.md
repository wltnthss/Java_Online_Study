## 4주차 과제

## 목표
제어문 학습
## 학습할 내용
- JUnit5 학습
- live-study 대시 보드 만드는 코드 작성
- LinkedLikst 구현
- Stack 구현
- 앞서 만든 ListNode 활용 Stack 구현
- Queue 구현

### 1-1 JUnit5 학습
JUnit은 Java를 위한 단위 테스트 프레임워크로 개발하는 프로그램에 대한 테스트 케이스를 쉽게 작성할 수 있도록 도와줍니다.

#### JUit 특징
- 단위 테스트 Frameworkd 중 하나
- 단정문으로 테스트 케이스의 수행 결과를 판별함
- 어노테이션으로 간결하게 지원함
- 결과는 성공(녹색), 실패(붉은색)중 하나로 표시

```java
public class Calculator {

    public int add(int num1, int num2) {
        return num1 + num2;
    }   
    public int sub(int num1, int num2) {
        return num1 - num2;
    }
}
```

```java
class JUnit5Test {
    @Test
    public void test() {

        Calculator calculator = new Calculator();
        int resultAdd = calculator.add(5, 5);       
        int resultSub = calculator.sub(5, 5);

        System.out.println("resultAdd : " + resultAdd);       
        System.out.println("resultSub : " + resultSub);

        //실행결과
        resultAdd : 10
        resultSub : 0
    }
}
```
간단한 예로 위와 같은 class.java 생성 후 라이브러리에 JUnit5를 추가하고 상황에 맞는 테스트 메소드를 작성해서 실행시켜주면 됩니다.

JUnit5에는 `@Test`와 같이 메소드 위에 선언되면 테스트 대상 메소드임을 의미하는 어노테이션과 어노테이션과 관련된 메소드들을 상황에 맞게 사용해서 테스트 코드를 작성합니다.

`@BeforeAll` - 해당 annotation 이 달린 메서드가 현재 클래스의 모든 테스트 메서드보다 먼저 실행됩니다. 메서드는 static 이어야합니다.

`@BeforeEach` - 해당 annotation 이 달린 메서드가 각 테스트 메서드 전에 실행됩니다.

`@DisplayName` - 테스트 클래스 또는 테스트 메서드의 이름을 정의할 수 있습니다.

`@Disable` - 테스트 클래스 또는 메서드를 비활성화할 수 있습니다.

`@AfterAll` - 해당 annotation 이 달린 메서드가 현재 클래스의 모든 테스트 메소드보다 이후에 실행됩니다. 메서드는 static 이어야합니다.

`@AfterEach` - 해당 annotation 이 달린 메서드가 각 테스트 메서드 이후에 실행됩니다.

`assertArrayEquals(a,b)` : 배열 a와b가 일치함을 확인합니다.

`assertEquals(a,b)` : 객체 a와b의 값이 같은지 확인합니다.

`assertSame(a,b)` : 객체 a와b가 같은 객체임을 확인합니다.

`assertTrue(a)` : a가 참인지 확인합니다.

`assertNotNull(a)` : a객체가 null이 아님을 확인합니다.

### 1-2 live-study 대시 보드 만드는 코드 작성
개인적으로 git 라이브러리는 처음 접하므로 API를 사용하는 방법에 대해서 알아보자.



### 1-3 LinkedLikst 구현


### 1-4 Stack 구현


### 1-5 ListNode 활용 Stack 구현


### 1-6 Queue 구현


### 후기 및 느낀점
