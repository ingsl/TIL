### 자바 가상머신(JAVA Virtual Machine)
Java와 OS사이의 중재자로 JAVA바이트코드를 OS에 특화된 코드로 변환(인터프리터 & JIT 컴파일러)하여 실행  
스택기반의 가상머신

<br />

### JRE란?  
Java어플리케이션을 실행하기 위한 최소 배포 단위로서 JVM과 필요 Library가 포함.  
Java11부터는 JDK만 제공하며 따로 JRE를 제공하지 않음.
 
<br />

### JDK란?  
JRE + 개발에 필요한 툴

<br />


### 자바프로그램 실행과정
1. 프로그램이 실행되면 JVM은 OS로부터 필요로하는 메모리를 할당받음. (JVM은 메모리를 용도에 따라 영역별로 관리)
2. 자바 컴파일러(javac)가 소스코드(java)를 읽어 바이트코드(class)로 변환 (컴파일된 결과물)
3. Class Loader를 통해 class파일을 JVM에 로딩. 로딩된 파일들은 Excution engine을 통해 기계어로 번역, 명령을 실행
4. OS에서 메모리를 할당 받은 Runtime Data Areas에 배치되어 실행
<br />

![](https://github.com/ingsl/TIL/blob/1fcb1fe5da5ce09b004db3978ed6a96b31e5cb7c/JAVA/image/JVM_image1.png)
<br />
 
### JVM의 구성  

#### Class Loader  
JVM내로 .class파일을 로드하고  Runtime Data Areas에 배치.
<br />

#### Excution engine
로드된 클래스의 Bytecode를 기계가 이해할 수 있는 형태로 변환(Interpreter와  JIT(Just-In-Time)으로 실행)  
<br />

#### Runtime Data Area
프로그램을 실행하기 위해 OS로부터 할당받은 메모리 공간

<br />

![](https://github.com/ingsl/TIL/blob/1fcb1fe5da5ce09b004db3978ed6a96b31e5cb7c/JAVA/image/JVM_image2.png)

<br />

1) PC Register  
 CPU의 Register와 역할이 비슷한 역할 수행. JVM명령의 주소값을 저장(각 Thread별로 하나씩 생성)
<br />

2) JVM stack  
 Java Method 내에서 사용되는 값들(매개변수, 지역변수, 리턴값 등)이 저장되는 영역.
 메소드 호출시마다 스택프레임이 생성됨.
<br />

3) Native Method Stack  
 실제 기계어로 작성된 프로그램을 실행하는 영역으로 Java가 아닌 다른 언어로 작성된 메소드 호출을 위해 할당된 stack영역
 <br />

4) Method Areas  
 클래스 정보를 처음 메모리공간에 올릴 때 초기화되는 대상(클래스, 변수, Method, static 변수, 상수 정보 등)을 저장하기 위한 메모리 공간이 저장되는 영역 (모든 Thread가 공유)
 <br />

5) Heap Area  
 객체를 저장하는 가상 메모리리공간  
 new 명령어로 생성된 인스턴스와 객체가 저장되는 영역(Garbage Collection 이슈는 이 영역에서 일어나며, 모든 Thread가 공유)
 <br />

![](https://github.com/ingsl/TIL/blob/c88d3776a371fa0d613fcc7c4efe9e5b7b01af1f/JAVA/image/JVM_image3.png)
<br />

### NEW / YOUNG
 - Eden : 객체들이 최초로 생성되는 공간.
 - Survivor 0 / 1 : Eden에서 참조되는 객체들이 저장되는 공간.

### Old
New Area에서 일정 시간 참조되고 있는, 살아남은 객체들이 저장되는 공간. Eden 영역에 객체가 가득 차게되면 첫 번째 GC(Minor GC)가 발생한다. Eden 영역에 있는 값들을 Survivor 1 영역에 복사하고 이 영역을 제외한 나머지 영역의 객체를 삭제한다.  
인스턴스는 소멸 방법과 소멸 시점이 지역변수와는 다르기에 힙이라는 별도의 영역에 할당

### Java7 Perm
Heap메모리 영역  
Perm은 JVM에 의해 크기가 강제되던 영역  
 <br />
### Java8 Metaspace 
Native memory 영역  
OS가 자동으로 크기를 조절하며 옵션으로 Metaspace의 크기를 줄일 수 있음.

Perm 영역은 보통 Class의 Meta 정보나 Method의 Meta 정보, Static 변수와 상수 정보들이 저장되는 공간.
이 영역은 Java 8부터는 Native 영역으로 이동하여 Metaspace 영역으로 변경
(다만, 기존 Perm 영역에 존재하던 Static Object는 Heap 영역으로 옮겨져 최대한 GC 대상이 될 수 있도록 함.)

출처
- https://johngrib.github.io/wiki/java8-why-permgen-removed/ 
- https://coding-start.tistory.com/205
- https://asfirstalways.tistory.com/158

