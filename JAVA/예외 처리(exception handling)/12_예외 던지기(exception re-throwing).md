# 12_예외 던지기(exception re-throwing)
> **한 메서드에서 발생할 수 있는 예외가 여러개인 경우**, **몇 개는 try-catch문을 통해** **메서드 내에서 자체적으로 처리** 하고,  
**나머지는 선언부에 지정** 하여 **호출한 메서드에서 처리** 하도록 함으로써, 양쪽에 나눠서 처리되도록 할 수 있다.  
심지어 단 하나의 예외에 대해서도 예외가 발생한 메서드와 호출한 메서드, 양쪽에서 처리하도록 할 수 있다.  
이것을 **“예외 던지기(exexception re-throwing)”** 라고 한다.
> 

## 예외 던지기(exception re-throwing)

1. 먼저 `예외`가 `발생`할 `가능성이 있는` `메서드`에서 `try-catch문`을 사용해 `예외를 처리`한다.
2. catch문에서 필요한 작업을 수행한 후 `throw문을 사용하여 예외를 다시 발생`시킨다.
3. `다시 발생한 예외는` 이 메서드를 `호출한 메서드에게 전달` 되고, 호출한 메서드의 try-catch문에서 예외를 또`다시 처리`한다.

👉🏻 이 방법은 하나의 예외에 대해서  
예외가 발생한 메서드와 , 이를 호출한 메서드 양쪽 모두에서 처리해줘야 하는 작업이 있을 때 사용!!



⚠️ 이 때 주의할 점은!! 
예외가 발생할 메서드에서는 try-catch문을 사용해서 예외처리를 해줌과 동시에 **메서드 선언부에 발생할 예외를 throws에 지정** 해줘야 함!!

</aside>

```java
public class Ex8_12 {
    public static void main(String[] args) {
        try {
            method1();
        } catch (Exception e) {
            System.out.println("main에서 예외가 처리되었습니다.");
        }
    }   // main메서드의 끝

    static void method1() throws Exception {
        try {
            throw new Exception();
        } catch (Exception e) {
            System.out.println("method1메서드에서 예외가 처리되었습니다.");
            throw e;    // 다시 예외를 발생시킴.
        }
    }   // method1메서드의끝
}
```

**컴파일 결과**

```java
method1메서드에서 예외가 처리되었습니다.
main에서 예외가 처리되었습니다.
```

- 결과를 보면 method1()과 main메서드 양쪽의 catch블럭이 모두 수행 되었다.
- method1()의 catch블럭에서 예외를 처리하고도 throw문을 통해 다시 예외를 발생 시켜, main메서드에서 한 번 더 처리한 것이다.

## 반환값이 있는 return문의 경우는??

```java
static int method1() {
		try {
					System.out.println("method1()이 호출되었습니다.");
					return 0;  // 현재 실행중인 메서드를 종료한다.
		} catch (Exception e) {
					e.prinStackTrace();
					return 1;  // catch블럭 내에도 return문이 필요하다.
		} finally {
					System.out.println("method1()의 finally블럭이 실행되었습니다.");
		}
}  // method1메서드의 끝
```

- catch블럭에도 return문이 있어야 한다.
- 예외가 발생했을 경우에도 값을 반환해야하기 때문이다.
