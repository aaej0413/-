# 06_멀티 catch블럭
> JDK1.7부터 여러 catch블럭을 ‘|’ 기호를 이용하여 하나의 catch블럭으로 합칠 수 있게 되었으며,
이를 ‘멀티 catch블럭’ 이라 한다.
**’멀티 catch블럭’** 을 이용하면 **중복된 코드를 줄일 수 있다.**
그리고 **‘|’ 기호로 연결할 수 있는 예외 클래스의 개수에는 제한이 없다.**
> 

```java
try {
				...
} catch (ExceptionA e) {
		e.printStackTrace();
} catch (ExceptionB e2) {
		e2.printStackTrace();
}
```

→

```java
try{
			...
} catch (Exception A | ExceptionB e) {
					e.printStackTrace();
}
```

## 멀티 catch블럭의 ‘|’ 기호로 연결된 예외 클래스가 조상과 자손의 관계에 있다면 컴파일 에러가 발생‼️

```java
try {
    ...
// } catch (**ParentException** | **ChildException e**) { // 에러 ‼️
} catch (ParentException e) { // OK. 위의 라인과 의미상 동일
    e.printStackTrace();
}
```

- 두 예외 클래스가 조상과 자손 관계에 있다면 조상 클래스만 써줘도 됨.
- 멀티 catch는 하나의 catch블럭으로 여러 예외를 처리하는 것이기 때문에,
- 발생한 예외를 멀티 catch블럭으로 처리하게 되었을 때,
- 멀티 catch블럭 내에서는 실제로 어떤 예외가 발생한 것인지 알 수 없다.
- 그래서 참조변수 e로 catch블럭에 ‘|’기호로 연결된 예외 클래스들의 공통분모인 조상 예외 클래스에 선언된 멤버만 사용할 수 있다.

```java
try {
		...
} catch (ExceptionA | ExceptionB e) {
		e.methodA(); // 에러. ExceptionA에 선언된 methodA()는 호출불가

		if(e instanceof ExceptionA) {
				ExceptionA e1 = (ExceptionA)e;
				e1.methodA();  // OK. ExceptionA에 선언된 메서드 호출 가능
		} else { // if(e instanceof ExceptionB)
				...
```
