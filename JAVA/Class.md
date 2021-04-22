### Class 란 무엇인가?
---
클래스(class)는 객체 지향 프로그래밍(OOP)에서 특정 객체를 생성하기 위해 변수와 메서드를 정의하는 일종의 틀을 의미 합니다.

#### 클래스의 구성요소
* 변수 
  * 인스턴스변수 : 접근제어자와 변수 타입, 변수 명을 가지는 일반적인 변수
  * 클래스변수 : 위의 요소를 가지며 static이 붙은 변수
  * 지역변수 : 메서드 내에서 선언되며 매서드 내에서만 사용할 수 있음
* 메서드
   * 메서드는 클래스의 행위를 표현하는 것으로 클래스 내의 함수
  
* 생성자
  * 객체를 생성할 때 항상 실행되는 것으로, 객체를 초기화해주기 위해 맨 처음 실행되는 메소드
  * 생성자는 클래스 이름과 동일해야 함
  * 모든 클래스는 생성자가 반드시 존재

#### 클래스의 수식
* 접근제어자 
   * public : 모든 클래스에서 해당클래스로 참조가 가능함
   * protect : 패키지 내부의 존재하는 클래스와 하위클래스는 참조가 가능함
   * private : 자기 자신인 내부에서만 참조가 가능함
* abstract : 추상클래스 선언시 사용, 해당 클래스는 메서드 구현부를 가지지 않고 상속 시 구현을 강제 함
* static : 클래스가 메모리에 올라갈 때 자동적으로 생성되기 때문에 인스턴스화 하지 않아도 사용 가능
* final : 해당 클래스는 상속이나 변경을 금지함
* sysnchronized : 동기화. 멀티 쓰레드 환경에서 데이터의 안정성을 보장
* strictfp : Double, Float에 대해 부동소수점 오차를 없앨 수 있음