# 05_String 클래스
> 기존의 **다른 언어**에서는 **문자열을 char형의 배열로 다루었으나**,
**자바에서는 문자열을 위한 클래스를 제공**한다. 그것이 바로 **String클래스**이다.
**String클래스는 문자열을 저장하고, 이를 다루는데 필요한 메서드를 함께 제공**한다.
> 

## “변경 불가능”한(immutable) 클래스

- String클래스에는 문자열을 저장하기 위해 문자형 배열 참조변수(char[]) value를 인스턴스 변수로 정의해놓고 있다.
- 인스턴스 생성 시 생성자의 매개변수로 입력받는 문자열은 이 인스턴스 변수(value)에 문자형 배열(char[])로 저장되는 것이다.

<aside>
💢 String클래스는 앞에 final이 붙어 있으므로 다른 클래스의 조상이 될 수 없다.

</aside>

```java
public final class String implements java.io.Serializable, Comparable {
		private char[] value;
				...
```

- 한 번 생성된 String은 읽어올 수만 있고 변경할 수는 없다.
- 예를들어, ‘+’연산자를 이용해 **문자열을 결합하는 경우** 인스턴스 내의 **문자열이 바뀌는 것이 아니라 새로운 문자열이 담긴 String인스턴스가 생성**되는 것이다.

![스크린샷 2022-07-08 오후 12.48.28.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/76c009f7-77f8-4d40-abce-3aadf143c165/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-07-08_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.48.28.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220709T095732Z&X-Amz-Expires=86400&X-Amz-Signature=2a63506ed962af40f5050dccb3198cdbf33c4fb854ea5eb85a553247a0d20de4&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-07-08%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252012.48.28.png%22&x-id=GetObject)

- 이처럼 덧셈연산자'+’를 사용해서 문자열을 결합하는 것은 매 연산 마다 새로운 문자열을 가진 String인스턴스가 생성되어 메모리 공간을 차지하게 되므로 가능한 한 결합횟수를 줄이는 것이 좋다.
- **문자열 간의 결합이나 추출 등 문자열을 다루는 작업이 많이 필요한 경우**에는 **“StringBuffer클래스”를 사용**하는 것이 좋다.
- StringBuffer인스턴스에 저장된 문자열은 변경이 가능하므로 하나의 StringBuffer인스턴스만으로도 문자열을 다룰 수 있다.
