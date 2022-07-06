# 03_예외 처리하기 - try -catch문
- 프로그램의 실행도중에 발생하는 에러는 어쩔 수 없지만,
- 예외는 프로그래머가 이에 대한 처리를 미리 해줘야 한다.

### 예외처리(exception handling)의

**정의** → **프로그램 실행시 발생할 수 있는 예기치 못한 예외의 발생에 대비한 코드를 작성하는 것.**

**목적** → **실행중**인 **프로그램의 갑작스런 비정상 종료를 막고**, **정상적인 실행상태를 유지**할 수 있도록 하는 것.

💢 **참고** : 에러와 예외는 모두 실행 시 (runtime) 발생하는 오류이다.

### 발생한 예외 처리 못하면??

- 프로그램은 비정상적으로 종료되며,
- 처리되지 못한 예외(uncaught exception)는 JVM의 ‘예외처리기(UncaugthExceptionHandler)’가 받아서 예외의 원인을 화면에 출력한다.

## try-catch의 구조

```java
try {
	// 예외가 발생할 가능성이 있는 문장들을 넣는다.
} catch (Exception1 e1) {
	// Exception1이 발생했을 경우, 이를 처리하기 위한 문장을 적는다.
} catch (Exception2 e2) {
	// Exception2가 발생했을 경우, 이를 처리하기 위한 문장을 적는다.
} catch (ExceptionN eN) {
	// ExceptionN이 발생했을 경우, 이를 처리하기 위한 문장을 적는다.
}
```

- 하나의 try블럭 다음에는 여러 종류의 예외를 처리할 수 있도록 하나 이상의 catch블럭이 올 수 있으며,
- 이 중 발생한 예외의 종류와 일치하는 단 한개의 catch블럭만 수행된다.
- 발생한 예외의 종류와 일치하는 catch블럭이 없으면 예외는 처리되지 않는다.
    
    💢 **참고** : if문과 달리, try블럭이나 catch블럭 내에 포함된 문장이 하나뿐이어도 괄호{ }를 생략할 수 ❌.
    

## try-catch문에서, 예외가 발생한 경우와 발생하지 않았을 때 흐름이 달라진다.

### 👉🏻  try블럭 내에서 예외가 발생한 경우

1. 발생한 예외와 일치하는 catch블럭이 있는지 확인한다.
2. **일치하는 catch블럭을 찾게 되면**, 그 catch블럭 내의 문장들을 수행하고 전체 try-catch문을 빠져나가서 그 다음 문장을 계속해서 수행한다.
**일치하는 catch블럭을 찾지 못하면, 예외는 처리되지 못한다.**

```java
/*
예외가 발생한 경우
 */
public class Ex8_2 {
    public static void main(String[] args) {
        System.out.println(1);
        try {
            System.out.println(0/0); // 0으로 나눠서 고의로 ArithmeticException을 발생 시킴.
            System.out.println(2);
        } catch (ArithmeticException ae) {
            System.out.println(3);
        }   // try-catch의 끝
        System.out.println(4);
    }   // main메서드의 끝
}
```

- try블럭에서 예외가 발생했기 때문에 try블럭을 바로 벗어나서 2는 출력되지 않는다.
- 그후 발생한 예외에 해당하는 catch블럭을 실행후, 전체 try-catch문을 벗어나서 다음 문장 4를 출력한다.

### 👉🏻  try블럭 내에서 예외가 발생하지 않은 경우

1. catch블럭을 거치지 않고 전체 try-catch문을 빠져나가서 수행을 계속한다.

```java
/*
예외가 발생하지 않은 경우
 */
public class Ex8_1 {
    public static void main(String[] args) {
        System.out.println(1);
        try {
            System.out.println(2);
            System.out.println(3);
        } catch (Exception e) {
            System.out.println(4);  // 실행되지 않는다.
        }   // try-catch의 끝
        System.out.println(5);
    }
}
```

- 예외가 발생하지 않았으므로 catch블럭의 문장이 실행되지 않는다.
