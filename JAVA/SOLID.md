# 객체지향의 SOLID원칙

### SRP : 단일 책임 원칙
 - 모든 클래스는 각각 하나의 책임만 가져야 한다. 클래스는 그 책임을 완전히 캡슐화해야 함을 말한다.

설계를 잘한 프로그램은 기본적으로 새로운 요구사항과 프로그램 변경에 영향을 받는 부분이 적다. 다시말해, 응집도는 높고 결합도는 낮은 프로그램을 뜻한다. 만약 한 클래스가 수행할 수 있는 기능, 즉 책임이 많아진다. 책임이 많아지면 클래스 내부의 함수끼리 강한 결합을 발생할 가능성이 높아진다. 이는 유지보수에 비용이 증가하게 되므로 따라서 책임을 분리시킬 필요가 있다.

### OCP : 개방 폐쇄 원칙 
 - 자신의 확장에는 열려 있고, 주변의 변화에 대해서는 닫혀 있어야 한다.

### LSP : 리스코프 치환 원칙
 - 자식 클래스는 언제나 자신의 부모 클래스를 대체할 수 있다는 원칙이다.

### ISP : 인터페이스 분리 원칙 
 - 한 클래스는 자신이 사용하지 않는 인터페이스는 구현하지 말아야 한다. 하나의 일반적인 인터페이스보다 여러개의 구체적인 인터페이스가 낫다.

### DIP : 의존 역전 원칙
- 의존 관계를 맺을 때 변화하기 쉬운 것 또는 자주 변화하는 것보다는 변화하기 어려운 것, 거의 변화가 없는 것에 의존하라는 것이다.