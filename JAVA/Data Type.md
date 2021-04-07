# Primitive Type과 Reference Type

Primitive type : 변수에 실제 값을 저장  
Reference type - 값이 저장되어있는 주소를 할당

|Primitive type|Reference type|
|---|---|
|byte, short, int, long, <br/> float, double, char, boolean |기본형 8가지를 제외한 나머지 타입|

<br/>

## Wapper Class   
Integer, Float, Boolean 등이 Wrapper class에 해당.  
기본 자료형(Primitive data type)에 대한 클래스 표현을 Wrapper class 라고 합니다.  
Primitive type으로 표현할 수 있는 간단한 데이터를 객체로 만들어야 할 경우 사용합니다.

### 특징
1. 모두 첫글자가 대문자
2. 산술연산이 불가
3. null로 초기화 할 수 있음.


### Boxing과 Unboxing
 - Boxing
   - primitive type을 Wrapper class로 변환
  ```java
  int primitive_number = 1;
  Integer wrapper_number = new Integer(primitive_number);
  ```

 - Unboxing
   - Wrapper class를 primitive type으로 변환
  ```java
  Integer wrapper_number = new Integer(1);
  int primitive_number = wrapper_number.intValue();
  ```

<br/>

JDK 1.5 부터는 AutoBoxing과 AutoUnBoxing을 제공합니다. 각 Wrapper class 에 상응하는 Primitive data type 일 경우에만 사용 가능합니다.
```java
int number = 1;
Integer obj = number;
```

