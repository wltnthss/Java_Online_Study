
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

### 1-1 JVM이란 무엇인가
JVM이란 Jave Virtual Machine의 약어로 자바 바이트코드를 실행시키기 위한 가상의 기계로 정의합니다. 자바로 작성된 모든 프로그램은 자바 가상 머신에서만 실행될 수 있으므로, 자바 프로그램을 실행시키기 위해서는 자바 가상 머신이 설치되어 있어야만 합니다. 일반 프로그램은 OS만 거치고 HW로 전달되지만 자바는 JVM을 한번 더 거친다는 특징으로 실행 시에 해석되기 때문에 속도가 느리다는 단점이 있습니다.   

<img src="http://www.tcpschool.com/lectures/img_java_jvm.png" width="500" height="300"> <br>   
출처 : <http://www.tcpschool.com/java/java_intro_programming> 

위의 그림 처럼 다른 운영체제에서도 JVM만 설치되어 있다면, 추가적인 환경 설정 없이 동작이 가능합니다. 하지만 JVM을 설치할 때에는 운영체제에 종속적이므로, Mac, Window 각 운영체제에 맞는 JVM을 설치해야합니다.

### 1-2 컴파일 하는 방법
자바 파일(.java)를 자바 컴파일러(javac.exe)를 이용하여 JVM이 이해할 수 있는 중간단계의 언어 바이트 코드(.class)로 바꿔줍니다. 실행 시, 바이트코드를 기계어로 바꿔주는데 이 역할을 JVM에서 해줍니다. 

<img src ="https://user-images.githubusercontent.com/60785586/106427158-3b79fb80-64aa-11eb-96f0-99d636433d0e.png" width="500" height="300"> <br>

위의 화면처럼 cmd에서 저장한 자바소스코드가 있는 위치까지 이동하고 해당 위치에 Main.java라고 되어있는 소스코드를 확인할 수 있습니다. 존재를 확인한 후에 컴파일을 하기 위한 명령어 **javac Main.java**를 입력하면 **Main.class**가 생성된 것을 확인할 수 있습니다. 생성된 class 파일은 **java Main**을 통해서 실행할 수 있습니다.

<img src ="https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/516/1847.gif" width="500" height="300"> <br>
출처 : <https://opentutorials.org/module/2495/13968> 

이렇게 생성된 자바 바이트 코드(.class)는 클래스 로더에 의해 JVM 내로 로드 되고, 실행 엔진에 의해 기계어로 해석되어 메모리 상에 배치되어집니다. 실행엔진에는 Interpreter와 JIT(Just-in-Time)가 있는데 Interprter는 바이트 코드를 한줄씩 읽기 때문에 실행이 느린 단점이 있습니다. 이러한 단점을 보완하기위해 JIT Compiler가 바이트 코드를 직접 컴파일하고 인터프리팅 하지 않게되어 속도를 향상시켜줍니다.

### 1-3 실행하는 방법
자바를 실행하는 방법은 크게 두 가지로 나뉘는데 설치와 환경변수를 적용해서 실행할 수 있기때문에 잘정리된 사이트를 참고합니다.
[이클립스](https://racoonlotty.tistory.com/entry/Eclipse-%EC%84%A4%EC%B9%98-%EB%B0%8F-%EC%8B%A4%ED%96%89)   [IntelliJ](https://whitepaek.tistory.com/10)

### 1-4 바이트코드란 무엇인가?
자바 바이트코드는 자바 가상 머신(JVM)이 실행하는 명령어의 형태입니다. 컴파일러에 의해 변환되는 코드가 1바이트이기 때문에 자바 바이트 코드라 불리고 있습니다. 이러한 자바 바이트 코드의 확장자는 .class이며, JVM만 설치되어 있으면, 어떠한 운영체제에서도 실행 가능합니다.

### 1-5 JIT 컴파일러란 무엇이며 어떻게 동작하는가

<img src = "https://miro.medium.com/max/4000/1*VFo0CC-chzvqJk6sls6ukQ.png" width="900" height="300"> <br>
출처 : <https://medium.com/@ahn428/java-jit-%EC%BB%B4%ED%8C%8C%EC%9D%BC%EB%9F%AC-c7d068e29f45>  

JIT(Just In Time)은 프로그램을 실행하는 시점(실시간)에 기계어로 번역하는 컴파일 기법입니다. 위의 그림에서 보면 알 수 있듯이 JIT컴파일러는 JRE안에 존재합니다.(JRE는 JVM를 담고있으므로 JVM에 존재한다고도 말합니다.) 프로그램을 만드는 방법은 크게 인터프리트 방식과 정적 컴파일 방식으로 나눌 수 있습니다. JIT 컴파일러는 두 가지의 방식을 혼합한 방식으로 실행 시점에 인터프리트 방식으로 기계어 코드를 생성하고, 그 코드를 캐싱하여, 같은 함수가 여러 번 불릴 때 매번 기계어 코드를 생성하는 것을 방지합니다.

### 1-6 JVM 구성 요소
<img src ="https://t1.daumcdn.net/cfile/tistory/25616D45576B854C3F" width="500" height="300"> <br>
출처 : <https://asfirstalways.tistory.com/158> 

Class Loader를 통해 가져온 class파일들을 JVM으로 로딩합니다. 로딩된 class파일들은 Execution engine을 통해 해석됩니다. 해석된 바이트코드들은 Runtime Data Areas 에 배치되고 실질적인 수행이 이루어지게 됩니다. JVM 구성 요소들을 5가지로 정의해볼 수 있습니다.
1. Class Loader   
JVM내로 클래스를 로드하고, 링크를 통해 배치하는 작업을 수행하는 모듈입니다. Runtime 시에 동적으로 클래스를 로드하며, jar파일 내 저장된 클래스들을 JVM위에 탑재하고 사용하지 않는 클래스들은 메모리에서 삭제합니다.

2. Excution Engine   
클래스를 실행시키는 역할이며, JVM내에 런타임 데이터 영역에 바이트 코드를 배치시키고, 실행엔진에 의해 실행됩니다. 이 실행엔진은 바이트코드를 실제로 JVM 내부에서 기계가 실행할 수 있는 형태로 변경하게 되는데 이 떄의 두 가지 방식으로 인터프리터와 JIT 방식을 사용합니다.

3. Interprter, 4. JIT   
Interpreper는 바이트코드를 명령어 단위로 한 줄씩 읽어서 수행하므로 느리다는 단점을 보완한 것이 JIT컴파일러입니다. 다시 한 번 정리하자면 인터프리터 방식으로 실행하다가 적절한 시점에 바이트코드 전체를 컴파일하여 네이티브 코드로 변경하고, 이후에는 더 이상 인터프리팅 하지 않고 네이티브 코드로 직접 실행하는 방식입니다. 네이티브 코드는 캐시에 보관하기 때문에 한 번 컴파일된 코드는 빠르게 수행할 수 있다는 장점이 있습니다.  

물론 JIT컴파일러가 컴파일하는 과정은 바이트코드를 인터프리팅하는 것보다 오래걸리므로 **한 번만 실행되는 코드**라면 컴파일하지 않고 인터프리팅 하는 것이 유리합니다. 따라서 JIT 컴파일러를 사용하는 JVM들은 내부적으로 해당 메서드가 얼마나 자주 수행되는지 체크하고, 일정 정도를 넘을 때에만 컴파일을 수행합니다.

5. Garbage collector   
GC를 수행하는 모듈(쓰레드)이 있습니다.
  


                                                                                          


