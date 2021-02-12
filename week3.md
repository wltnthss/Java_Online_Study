## 3주차 과제

### 목표
프리미티브타입, 변수 그리고 배열을 사용하는 방법을 익힙니다.
## 학습할 내용
- 산술 연산자
- 비트 연산자
- 관계 연산자
- 논리 연산자
- instanceof
- assignment(=) operator
- 화살표(->) 연산자
- 3항 연산자
- 연산자 우선 순위
- (optional) Java 13. switch 연산자

### 1-1 산술 연산자
<img src="https://t1.daumcdn.net/cfile/tistory/9994BF335A156E6B22" width="700" height="250"> <br>
출처 : <https://keep-cool.tistory.com/18>   

산술 연산자는 기본적인 사칙연산과 나머지 연산을 포함한 다섯 가지 연산을 뜻한다. 덧셈과 뺄셈, 곱셈은 기본적으로 수학 계산과 비슷하나 자바에서 나눗셈과 나머지 연산은 2주차 과제에서 알아보았던 캐스팅, 프로모션 형변환이 빈번하게 일어나므로 이를 유의해야합니다.


```java
public class TestCal {
	public static void main(String[] args) {
		int n1 = 10;
		int n2 = 3;

		System.out.println("n1 + n2 = " + (n1 + n2));
		System.out.println("n1 - n2 = " + (n1 - n2));
		System.out.println("n1 * n2 = " + (n1 * n2));

		System.out.println("n1 / n2 = " + (n1 / n2));						// (1)
		System.out.println("n1 / n2 = " + (n1 / (double)n2));

		System.out.println("n1 % n2 = " + (n1 % n2));
		System.out.println("n1 % n2 = " + (double)(n1 % n2));

	    //실행결과
	    n1 + n2 = 13
	    n1 - n2 = 7
	    n1 * n2 = 30

	    n1 / n2 = 3
	    n1 / n2 = 3.333333333...

	    n1 % n2 = 1
	    n1 % n2 = 1.0
	}
}
```
(1)의 결과를 보았을 때 10/3의 값이 3이 나오는 것을 볼 수 있습니다. 그 이유는 n1, n2가 int형으로 선언되었기 때문입니다. 때문에 정확한 결과값을 위해서는  10/3의 값은 실수로 피연산자를 실수형으로 Casting(형변환) 해야합니다. 이 때의 형변환은 큰 값에서 작은 값으로 이루어지므로 값손실이 일어납니다.

### 1-2 비트 연산자
비트 연산자는 카카오 코딩테스트에도 출시된 경험도 있을 정도로 간단하지만 중요한 개념입니다. 비트 연산자는 이진수인 0과 1로 이루어져있어 각 자리를 규칙에 따라 연산을 수행합니다.

#### & (AND)
피연산자 모두 1일때만 1의 결과를 얻고, 그 외에 값은 0을 얻습니다.
#### | (OR)
피연산자 중 한 쪽의 값이 1이면 1의 결과를 얻고, 그 외에 값은 0을 얻습니다.
#### ^ (XOR)
피연산자 값이 서로 다를때만 1의 결과를 얻고, 그 외에 값은 0을 얻습니다.
#### ~ (NOT)
1의 값은 0으로 0의 값은 1로 반환합니다.
#### >> (right SHIFT)
비트를 오른쪽으로 밀어낸 뒤, 밀어내기 전 가장 왼쪽 비트와 동일한 숫자로 공백을 채웁니다.
#### << (left SHIFT)
비트를 왼쪽으로 밀어낸 뒤 공백을 0으로 채웁니다.
#### >>> (unsigned right SHIFT)
오른쪽으로 밀어낼 때 공백을 0으로 채웁니다.

```java
public class TestBitCal {
	public static void main(String[] args) {
		int a = 5 & 1;				// 0101 & 0001 = 0001
		int b = 3 | 1;				// 0011 | 0001 = 0100
		int c = 3 ^ 1;				// 0011 ^ 0001 = 0010
		int d = c >> 1;		  	// 0010 >> 1 = 0001
		int e = c << 1;		 	  // 0010 << 1 = 0100

		System.out.println(a);		
		System.out.println(b);		
		System.out.println(c);		
		System.out.println(d);		
		System.out.println(e);				
	}
}

```
### 1-3 관계 연산자
- `==` : Equal to
- `!=` : Not equal to
- `>` : greater than
- `<` : less than
- `>=` : greater than or equal to
- `<=` : less than or equal to

### 1-4 논리 연산자
- Binary Operator(이항)
    - `&&` (LOGICAL AND)
    - `||` (LOGICAL OR)
- 피연산자의 타입은 `boolean`
- 연산 결과 타입은 `boolean`

### 1-5 instanceof
참조변수가 참조하고 있는 인스턴스의 실제 타입을 알아볼 때 instanceof 연산자를 사용합니다. 형변환 가능여부를 가능하면 true, 불가하면 false로 리턴해줍니다. 주로 상속 관계에서 부모객체인지 자식객체인지 확인하는데 사용됩니다.

```java
class A{ 						// A = 부모
}
class B extends A{				// B = 자식  		
}
public class InstanceofTest {			
	public static void main(String[] args) {		
		A a = new A();
		B b = new B();

		System.out.println(a instanceof A);	// a는 자기 자신 객체 true
		System.out.println(b instanceof B);	// b는 자기 자신 객체 true

		System.out.println(b instanceof A);	// b는 A의 자식 객체 true
		System.out.println(a instanceof B);	// a는 B의 부모 객체 false
	}
}
```

### 1-6 assignment(=) operator
대입 또는 할당 연산자라고 부릅니다. 오른쪽의 피연산자를 왼쪽의 피연산자의 값으로 할당합니다. 그렇기 때문에 왼쪽에는 변수, 오른쪽에는 리터럴이 담긴 변수가 옵니다.

- `=` (ASSIGN)
- `+=` (ADD and ASSIGN)
- `-=` (SUBTRACT and ASSIGN)
- `*=` (MULTIPLY and ASSIGN)
- `/=` (DIVIDE and ASSIGN)
- `%=` (MODULO and ASSIGN)
- `&=` (AND and ASSIGN)
- `^=` (XOR and ASSIGN)
- `|=` (OR and ASSIGN)
- `<<=` (LEFT SHIFT and ASSIGN)
- `>>=` (RIGHT SHIFT and ASSIGN)
- `>>>=` (UNSIGNED RIGHT SHIFT and ASSIGN)

```java
public class assignmentTest {		

	public static void main(String[] args) {
		int num1 = 7, num2 = 7, num3 = 7;

		num1 = num1 - 3;
		num2 -= 3;
		num3 =- 3;

		System.out.println("- 연산자에 의한 결과 : "+ num1);
		System.out.println("-= 연산자에 의한 결과 : "+ num2);
		System.out.println("=- 연산자에 의한 결과 : "+ num3);

		- 연산자에 의한 결과 : 4
		-= 연산자에 의한 결과 : 4
		=- 연산자에 의한 결과 : -3
	}
}
```
복합 대입 연산자에서 연산자의 순서는 중요하므로 알아두어야한다.

### 1-7 화살표(->) 연산자
학원에서 아직 람다에 대해 학습을 하지 않았기 때문에 화살표 연산자를 알아보며 람다에 대해 좀 더 자세하게 개념을 숙지해두자.  

#### 람다 표현식이란?
람다는 익명 클래스로써 메소드를 간단하게 하나의 식으로 표현한 것입니다. 람다는 ``java 8`` 이후 나온 기술이며 메소드를 하나의 인수로 취급할 수 있어, 유연한 프로그래밍을 가능하게 해줍니다. 람다를 이해하려면 기본적으로 클래스와 인터페이스, 약식 상속에 대해서 숙지하고 알고있어야 합니다.
```java
예제 ,,, (1)

int min(int x, int y) {
    return x < y ? x : y;
}
/// 람다 표현식 표현
(x, y) -> x < y ? x : y;

예제 ,,, (2)

new Thread(new Runnable() {
    public void run() {
        System.out.println("전통적인 방식의 일회용 스레드 생성");
    }
}).start();

 /// 람다 표현식 표현
new Thread(()->{
    System.out.println("람다 표현식을 사용한 일회용 스레드 생성");
}).start();
```
위의 예제들처럼 람다는 객체를 생성하지 않아도 메소드가 사용가능하고, 불필요한 코드를 줄이고 코드의 가독성이 좋아집니다. 하지만 호출이 까다롭고, stream 사용 시 단순 for문 while문 사용 시 성능이 떨어진다는 단점이 있습니다.

그 밖에 함수형 인터페이스를 람다로 사용하는 방법과 자세한 사용방법 추후에 15주차에서 자세하게 다시 알아보겠습니다.

### 1-8 3항 연산자
3항 연산자는 if else와 같은 구문이나 코드의 가독성이 더 좋으므로 간단한 조건식을 사용할 때는 3항 연산자를 주로 사용하는편입니다.

사용방법 : (조건) ? (조건 참일 때 실행) : (조건 거짓일 때 실행)

```java
//IF ELSE
int a;
if(5<4) {
    a = 50;
}else {
    a = 40;
}
System.out.println(a); //결과 = 40

//삼항연산자
int b = (5 < 4) ? 50 : 40;
System.out.println(b); //결과 = 40
```
### 1-9 연산자 우선 순위
<img src ="https://oopy.lazyrockets.com/api/v2/notion/image?src=https%253A%252F%252Fs3-us-west-2.amazonaws.com%252Fsecure.notion-static.com%252F9ac16015-dc56-4f2d-8ec6-05aa4d486f9d%252F997A014D5A90B9B00D.png&blockId=85ca48bd-e574-48fe-9f8d-58115c2921b3" width="600" height="400"> <br>
출처 : <https://catsbi.oopy.io/c750e102-a202-4b70-b679-71c2fb24188a>

연산자의 우선 순위는 외우지 않아도 알고리즘을 자주 사용하다보면 익숙해집니다. 기본적으로 괄호의 우선순위가 제일 높아 괄호를 자주 사용합니다. 산술, 비교, 논리, 대입의 순서로 흐름만 기억해두자.



### 1-10 (optional) Java 13. switch 연산자
`java12` 부터 switch 연산자가 추가되었습니다.
기존의 switch문은 다수의 case와 break, return값이 존재할 수 없다는 단점으로 if else문으로 대체하는 경우가 많았는데 새로 추가 된 switch 연산자에서는 달라진 점이 있습니다.   

#### switch operator
- break를 사용하지 않아도 됨
- `yield` 예약어 추가`
- return값 존재 가능
- `case -> A` 와 같은 형식으로 표시 가능

`java13` yield 예약어 추가되었다.

```java
public class Main {
    public static void main(String[] args) {

        //Java 12 이전
        int num = 1;
        int returnNum = 0;
        switch(num){
            case 1:
                returnNum = 1;
                System.out.println("1들어옴");
                break;
            case 2:
                returnNum = 2;
                System.out.println("2들어옴");
                break;
            case 3:
                returnNum = 3;
                System.out.println("3들어옴");
                break;
        }
        System.out.println("returnNum : [ " + returnNum + " ]");

        //Java 12
        returnNum = switch(num){
            case 1 -> 1;
            case 2 -> 2;
            default -> throw new IllegalStateException("Unexpected value: " + num);
        };
        System.out.println("returnNum : [ " + returnNum + " ]");

        //Java13
        returnNum = switch(num){
            case 1 : yield 3;
            default : throw new IllegalStateException("unexpected value : " + num);
        };
        System.out.println("returnNum : [ " + returnNum + " ]");
    }
}

1들어옴
returnNum : [ 1 ]
returnNum : [ 1 ]
returnNum : [ 3 ]
```

### 후기 및 느낀점
학원에서 배우지 못한 람다라는 개념과 자바의 버전이 업데이트되면서 새로 추가된 기능까지 함께 공부할 수 있어서 만족할 수 있었던 시간이었다. 개인적으로 복습하고 온라인 스터디 시청을 통해서 한번 더 복습해야겠다.
