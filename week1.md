
## 1주차 과제

### 목표
자바 소스 파일(.java)을 JVM으로 실행하는 과정 이해하기.
### 학습할 내용
- JVM이란 무엇인가
- 컴파일 하는 방법
- 실행하는 방법
- 바이트코드란 무엇인가
- JIT 컴파일러란 무엇이며 어떻게 동작하는가
- JVM 구성 요소
- JDK와 JRE의 차이

### 1-1 JVM이란 무엇인가?
JVM이란 Jave Virtual Machine의 약어로 자바 바이트코드를 실행시키기 위한 가상의 기계로 정의합니다. 자바로 작성된 모든 프로그램은 자바 가상 머신에서만 실행될 수 있으므로, 자바 프로그램을 실행시키기 위해서는 자바 가상 머신이 설치되어 있어야만 합니다. 일반 프로그램은 OS만 거치고 HW로 전달되지만 자바는 JVM을 한번 더 거친다는 특징으로 실행 시에 해석되기 때문에 속도가 느리다는 단점이 있습니다.   

<img src="http://www.tcpschool.com/lectures/img_java_jvm.png" width="500" height="300"> <br>   
출처 : <http://www.tcpschool.com/java/java_intro_programming> <br> 

위의 그림 처럼 다른 운영체제에서도 JVM만 설치되어 있다면, 추가적인 환경 설정 없이 동작이 가능합니다. 하지만 JVM을 설치할 때에는 운영체제에 종속적이므로, Mac, Window 각 운영체제에 맞는 JVM을 설치해야합니다.

### 1-2 컴파일 하는 방법?
자바 파일(.java)를 자바 컴파일러(javac.exe)를 이용하여 JVM이 이해할 수 있는 중간단계의 언어 바이트 코드(.class)로 바꿔줍니다. 실행 시, 바이트코드를 기계어로 바꿔주는데 이 역할을 JVM에서 해줍니다. 

<img src ="https://user-images.githubusercontent.com/60785586/106427158-3b79fb80-64aa-11eb-96f0-99d636433d0e.png" width="500" height="300"> <br>

위의 화면처럼 cmd에서 저장한 자바소스코드가 있는 위치까지 이동하고 해당 위치에 Main.java라고 되어있는 소스코드를 확인할 수 있습니다. 존재를 확인한 후에 컴파일을 하기 위한 명령어 **javac Main.java**를 입력하면 **Main.class**가 생성된 것을 확인할 수 있습니다. 생성된 class 파일은 **java Main**을 통해서 실행할 수 있습니다.

<img src ="https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/516/1847.gif" width="500" height="300"> <br>
출처 : <https://opentutorials.org/module/2495/13968> <br>

이렇게 생성된 자바 바이트 코드(.class)는 클래스 로더에 의해 JVM 내로 로드 되고, 실행 엔진에 의해 기계어로 해석되어 메모리 상에 배치되어진다. 실행엔진에는 Interpreter와 JIT(Just-in-Time)가 있는데 Interprter는 바이트 코드를 한줄씩 읽기 때문에 실행이 느린 단점이 있습니다. 이러한 단점을 보완하기위해 JIT Compiler가 바이트 코드를 직접 컴파일하고 인터프리팅 하지 않게되어 속도를 향상시켜줍니다.

### 1-3 실행하는 방법?
