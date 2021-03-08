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



### 1-3 LinkedList 구현
#### 목표
- LinkedList 공부하기
- 정수를 저장하는 ListNode 클래스 구현
- ListNode add(ListNode head, ListNode nodeToAdd, int position)
- ListNode remove(ListNode head, int postionToRemove)
- boolean contains(ListNode head, ListNode nodeToCheck)

**LinkedList**란 각 노드가 데이터와 포인터를 가지고 한 줄로 연결되어 있는 방식으로 데이터를 저장하는 자료구조이다. 일반적으로 LinkedList는 노드(Node)와 링크(Link)로 구성되어있다. 

`노드` : 실제 정보를 담고 있는 하나의 단위이다.   
`링크` : 노드간의 위치정보를 저장하고 있어 연결리스트 순서를 유지할 수 있도록 하는 연결고리이다.

노드의 시작점은 head, 끝점은 tail이라 부르며 노드의 추가, 삭제, 탐색이 가능하다.

<img src="https://postfiles.pstatic.net/MjAyMDEyMDFfMjU2/MDAxNjA2Nzk3NDA4OTUy.2vXZPVs0TxU4EY3SVip7YHQTL2Vs1fZl9pYvXetXnHgg.rhiZXuoyBBs81HDVW7AkSJleEvevaV_Jji_GQbu7BIEg.PNG.swoh1227/1.PNG?type=w773" width="600" height="200">
출처 : <https://blog.naver.com/swoh1227/222161294264>

연결리스트(LinkedList)는 위의 그림과 같이 노드와 링크로 구성되어있다는 것을 알아두자.

#### 연결 리스트 특징
- 배열에 비해서 삽입/삭제가 용이합니다.
배열은 데이터의 길이를 정해두고 사용하고 중간 데이터를 삭제하거나 삽입하려면 빈 공간을 남기거나 기존 데이터를 밀어내야합니다. 하지만 연결 리스트는 링크를 통해 주솟값을 가지고 있어서 주소값만 변경해주면 됩니다.
- 탐색을 위해서는 첫번째 노드부터 비교해야하므로 검색속도가 느리다는 단점을 가지고 있습니다.

#### 연결 리스트 종류
연결 리스트는 단일 연결 리스트, 원형 연결 리스트, 이중 연결 리스트 세 가지의 종류가 있습니다.
위의 사진과 같은 경우가 단일 연결 리스트입니다.
- 원형 연결 리스트 : 마지막 노드 위치를 null이 아닌 맨 처음 노드를 가르키는 형태입니다.
- 이중 연결 리스트 :  하나의 노드에 이전 노드와 다음 노드의 위치를 둘 다 저장하는 형태입니다.

#### ListNode 클래스 구현
```java
package list_LinkedList;

public class LinkedList {
	// 첫번째 노드 변수
	private Node head;
	private Node tail;
	private int size = 0;
	private class Node{
		// 데이터 저장영역 변수
		private Object data;
		// 다음 노드를 가르키는 변수 
		private Node next;
		public Node(Object input) {
			this.data = input;
			this.next = null;
		}
		
		// 노드 내용 출력 확인 함수
		public String toString() {
			return String.valueOf(this.data);
		}	
	}
	public void addFirst(Object input) {
		// 노드 생성
		Node newNode = new Node(input);
		// 새로운 노드의 다음 노드 헤드 지정.
		newNode.next = head;
		// 헤드로 새로운 노드 지정
		head = newNode;
		size++;
		if(head.next == null) {
			tail = head;
		}
	}
	public void addLast(Object input) {
		// 노드 생성
		Node newNode = new Node(input);
		// 리스트의 노드가 없다면 첫번째 노드를 추가하는 메소드를 사용합니다.
		if(size == 0) {
			addFirst(input);
		} else {
			// 마지막 노드의 다음 노드로 생성한 노드를 지정합니다.
			tail.next = newNode;
			// 마지막 노드를 갱신합니다.
			tail = newNode;
			// 엘리먼트 개수 1증가
			size++;
		}
	}
	Node node(int index) {
		Node x = head;
		for(int i=0; i<index; i++)
			x = x.next;
		return x;
	}
}
```



### 1-4 Stack 구현


### 1-5 ListNode 활용 Stack 구현


### 1-6 Queue 구현


### 후기 및 느낀점
