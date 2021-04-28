<!-- Heading -->
# 제네릭이란?
JDK 1.5에 처음 도입
데이터타입(data type)을 일반화한다(generalize)는 것을 의미합니다.  
<br/>

제네릭은 아래표의 타입들이 많이 사용됩니다.
|타입|설명|
|---|---|
|\<T>|Type|
|\<E>|Element|
|\<K>|Key|
|\<V>|Value|
|\<N>|Number| 

<br/>

### 제네릭클래스 및 인터페이스
```java
public class ClassName <T> {...}
public Interface InterfaceName <T> {...}
```
기본적으로 제네릭 타입의 클래스나 인터페이스는 위와 같이 선언 합니다.  
선언한 제네릭 클래스를 사용할 때, 객체 생성시에는 구체적인 타입을 명시해야합니다.  
<br />




```java
public class ClassName <T, K> { ... }
 
public class Main {
	public static void main(String[] args) {
		ClassName<String, Integer> a = new ClassName<String, Integer>();
	}
}
```
위와 같이 객체생성 시 제네릭클래스의 타입 T는 String, K는 Integer가 됩니다.
* 타입 파라미터로 명시할 수 있는 것은 참조 타입(Reference Type)밖에 올 수 없음. (int, double 등 원시 타입(primitive type) 불가)  
<br/>

### 제네릭 메소드
```java
class ClassName<T> {
	private T type;
	
	void set(T type) {	// 제네릭 메소드
		this.type = type;
	}
	
	T get() {	// 제네릭 메소드
		return type;
	}
}

class Main {
	public static void main(String[] args) {
		
		ClassName<String> a = new ClassName<String>();
		ClassName<Integer> b = new ClassName<Integer>();
		
		a.set("10");
		b.set(10);
	
		System.out.println("a data : " + a.get());
		System.out.println("a E Type : " + a.get().getClass().getName());
		
		System.out.println("b data : " + b.get());
		System.out.println("b E Type : " + b.get().getClass().getName());
		
	}
}
```
위와 같이 ClassName란 객체를 생성할 때 타입 파라미터를 다르게 지정,
a 객체는 String 타입, b 객체는 Integer 타입의 결과가 나옵니다.  

<br/>

### 제한된 타입 제네릭
제네릭의 타입을 제한하고 싶은 경우 extends 또는 super를 사용하여 참조된 클래스의 타입으로 제한 할 수 있습니다.  '?'는 와일드카드라고 해서 '알 수 없는 타입'을 의미 합니다.
```java
<? extends T>	// T와 T의 자손 타입만 가능
<? super T>	// T와 T의 부모(조상) 타입만 가능
<?>		// 모든 타입 가능. <? extends Object>랑 같은 의미
```

Integer, Long, Byte, Double, Float, Short 같은 래퍼 클래스들은 Number 클래스를 상속을 받습니다. 이때 제네릭을 제한 한다면 아래와 같이 사용할 수 있다.
```java
public class ClassName <? extends Number> { ... }
```
<br/>

### 제네릭의 장점
1. 잘못된 타입이 들어올 수 있는 것을 컴파일 단계에서 방지 해줌
2. 클래스 외부에서 타입을 지정해주기 때문에 타입을 따로 체크하고 변환 해줄 필요가 없음.
3. 코드의 재사용성이 높아짐.
