# 05_printStackTrace() 와 getMessage()
> 예외가 발생했을 떄 생성되는 **예외 클래스의 인스턴스에는 발생한 예외에 대한 정보**가 담겨있다.
이 정보는 **getMessage()** 와 **pringSatckTrace()** 를 통해서 얻을 수 있다.
catch블럭의 괄호()에 선언된 참조변수를 통해 이 인스턴스에 접근할 수 있다.
이 참조변수는 선언되 catch블럭 내에서만 사용 가능하.
> 

## printStackTrace( )

👉🏻 예외발생 당시의 호출스택(Call Stack)에 있었던 메서드의 정보와 예외 메세지를 화면에 출력한다.

## getMessage( )

👉🏻 발생한 예외 클래스의 인스턴스에 저장된 메세지를 얻을 수 있다.

```java
public class Ex8_5 {
    public static void main(String[] args) {
        System.out.println(1);
        System.out.println(2);

        try {
            System.out.println(3);
            System.out.println(0 / 0);  // 예외 발생!!
            System.out.println(4);      // 실행 ❌

        } catch (ArithmeticException ae) {
            ae.printStackTrace();       // 참조변수 ae를 통해, 생성된 ArithmeticException 인스턴스에 접근 가능.
            System.out.println("예외메세지 : " + ae.getMessage());
        }   // try-catch의 끝

        System.out.println(6);
    }   // main메서드의 끝
}
```

```java
결과

1
2
3
java.lang.ArithmeticException: / by zero
	at exception_handling.Ex8_5.main(Ex8_5.java:10)
예외메세지 : / by zero
6
```

- try-catch문으로 예외처리를 하여, 예외가 발생해도 비정상적으로 종료하지 않도록 해주는 동시에,
printStackTrace() 또는 getMessage()와 같은 메서드를 통해 예외의 발생 원인을 알 수 있다.
