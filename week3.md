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

		System.out.println("n1 / n2 = " + (n1 / n2));
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
(1)의 결과를 보았을 때 10/3의 값이 3이 나오는 것을 볼 수 있다. 그 이유는 n1, n2가 int형으로 선언되었기 때문입니다. 때문에 정확한 결과값을 위해서는 연산자나 피연산자중 한 쪽을 실수형으로 Casting 해야합니다.

### 1-2 비트 연산자
비트 연산자는 카카오 코딩테스트에도 출시된 경험도 있을 정도로 간단하지만 중요한 개념이다. 비트 연산자는 이진수인 0과 1로 이루어져있어 각 자리를 규칙에 따라 연산을 수행합니다.

#### & (AND)
피연산자 모두 1일때만 1의 결과를 얻고, 그 외에 값은 0을 얻습니다.
#### | (OR)
피연산자 중 한 쪽의 값이 1이면 1의 결과를 얻고, 그 외에 값은 0을 얻습니다.
#### ^ (XOR)
피연산자 값이 서로 다를때만 1의 결과를 얻고, 그 외에 값은 0을 얻습니다.
#### ~ (NOT)
1의 값은 0으로 0의 값은 1로 반환합니다.
#### >> (right SHIFT)

#### << (left SHIFT)

#### <<< (unsigned right SHIFT)


### 1-3 관계 연산자

### 1-4 논리 연산자

### 1-5 instanceof

### 1-6 assignment(=) operator

### 1-7 화살표(->) 연산자

### 1-8 3항 연산자

### 1-9 연산자 우선 순위

### 1-10 (optional) Java 13. switch 연산자
