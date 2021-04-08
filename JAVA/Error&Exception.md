# Error와 Exception

- Error : 컴파일 시 문법적인 오류와 런타임 시 발생하여 프로세스에 심각한 문제를 야기 시켜 프로세스를 종료 시킬 수 있습니다.  
Exception과 다르게 에러가 발생할 경우 코드를 고치지 않고서는 해결이 불가능 합니다.  
ex) StackOverflowError, OutOfMemoryError

- Exception : 컴퓨터 시스템의 동작 도중 예기치 않았던 이상 상태가 발생하여 수행 중인 프로그램이 영향을 받는 것을 의미 합니다.  
Checked Exception, Unchecked Exception 두 종류의 예외가 존재 합니다.  

### Checked Exception과 Unchecked Exception
||Checked Exception|Unchecked Exception|
|---|---|---|
|처리여부|반드시 예외처리 해야함|명시적으로 하지 않아도 됨.|
|확인시점|컴파일시점|런타임 시점|
|트랜잭션 처리|rollback하지 않음|rollback 해야함|
|대표 예외|IOException, ClassNotFoundException|NullPointerException, IndexOutOfBoundException|

<br/>
<br/>

![](https://github.com/ingsl/TIL/blob/e9c26f6d04c3426a2ef6a612680684969ae6df04/JAVA/image/exception_image.JPG)

이미지에서 보는 것처럼 RuntimeException과 이를 상속한 클래스가 Unchecked Exception입니다.  

Checked Exception과 Unchecked Exception의  명확한 구분 기준은 '처리해야 하는가' 입니다.  
Checked Exception이 발생할 수 있는 메소드라면 try/catch나 throw로 처리 해야합니다. 반면 Unchecked Exception은 명시적 처리를 하지 않아도 됩니다. 개발자의 부주의로 발생하는 경우가 많습니다.

### 예외 처리
예외를 처리하는 방법에는 예외 복구, 예외 처리 회피, 예외 전환 방법이 있습니다.

* 예외 복구
  * 예외 상황을 파악하고 문제를 해결해서 정상 상태로 돌려놓는 방법
  * 예외를 잡아서 일정 시간, 조건만큼 대기하고 다시 재시도를 반복, 반복 횟수를 초과하면 예외를 발생시킴.
```java
final int MAX_RETRY = 100;
public Object method() {
    int maxRetry = MAX_RETRY;
    while(maxRetry > 0) {
        try {
            ...
        } catch(SomeException e) {
            // 로그 출력. 정해진 시간만큼 대기
        } finally {
            // 리소스 반납 및 정리 작업
        }
    }

    // 최대 재시도 횟수를 넘기면 직접 예외를 발생시킴
    throw new RetryFailedException();
}
```

* 예외처리 회피
   * 예외 처리를 직접 담당하지 않고 호출한 쪽으로 던져 회피하는 방법
   * 역할을 분담하고 있는 관가 아니라면 예외를 그냥 던지는 것은 무책임
```java
public void add() throws SQLException {
    // ...
}
```

* 예외 전환
  * 예외 회피처럼 그냥 던지지 않고 적절한 예외로 전환해서 넘기는 방법
```java
public void method() {
    try {
        // ...
    } catch(SQLException e)) {
        ...
         throw DuplicateUserIdException();
    }
}
```







