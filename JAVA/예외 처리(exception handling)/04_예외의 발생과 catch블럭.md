# 04_예외의 발생과 catch블럭
> catch블럭은 **괄호( )** 와 **블럭{ }** **두 부분으로 나눠**져 있는데,  
괄호( )내에는 **처리하고자 하는. 예외와 같은 타입의 참조변수 하나를 선언**해야 한다.
> 

## 예외가 발생하면??

- **발생한 예외에 해당하는 클래스의 인스턴스가 만들어진다.**

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

- 여기서는 ArithmeticException이 발생했으므로 **ArithmeticException인스턴스**가 생성된다.
- 예외가 발생한 문장이 try블럭에 포함되어 있다면, 이 예외를 처리할 수 있는 catch블럭이 있는지 찾게 된다.
    1. 첫번째 catch블럭부터 차례로 내려가면서 catchy블럭의 괄호( )내에 선언된 참조변수의 종류와
    생성된 예외클래스의 인스턴스에 instanceof연산자를 이용해서 검사하게 되는데,
    검사결과가 true인 catch블럭을 만날 때 까지 검사는 계속된다.
    2. 검사 결과가 true인 catch블럭을 찾게 되면 블럭에 있는 문장들을 모두 수행한 후,
    try-catch문을 빠져나가고 예외는 처리되지만
    3. 검사 결과가 true인 catch블럭이 하나도 없으면 예외는 처리되지 않는다.
    

### 💢 모든 예외 클래스는 Exception클래스의 자손이므로,
catch블럭 괄호( )에 Exception클래스 타입의 참조변수를 선언해 놓으면
어떤 종류의 예외가 발생하더라도 이 catch블럭에 의해 처리된다.

**ex)**

```java
public class Ex8_3 {
    public static void main(String[] args) {
        System.out.println(1);
        System.out.println(2);

        try {
            System.out.println(3);
            System.out.println(0/0);    // 0으로 나눠서 고의로 ArithmeticException 을 발생시킴.
						System.out.println(4);      // 실행되지 ❌
        } catch (Exception e) {         // **ArithhmeticException 대신 Exception 을 사용.**
            System.out.println(5);
        }   // try-catch의 끝

        System.out.println(6);
    }   // main메서드의 끝
}
```

- ArithmeticException클래스는 Exception클래스의 자손이므로 ArithmeticException인스턴스와   
Exception클래스와의 instanceof연산 결과가 true가 되어 Exception클래스 타입의 참조변수를 선언한  
catch블럭의 문장들이 수행된 것.

**ex2)**

```java
public class Ex8_4 {
    public static void main(String[] args) {
        System.out.println(1);
        System.out.println(2);
        try {
            System.out.println(3);
            System.out.println(0/0);    // 0으로 나눠서 고의로 ArithmeticException 을 발생시킴.
            System.out.println(4);      // 실행되지 ❌

        } catch (ArithmeticException ae) {
            if (ae instanceof ArithmeticException)
                System.out.println("true");
            System.out.println("ArithmeticException");

        } catch (Exception e) {         // ArithmeticException을 제외한 모든 예외가 처리된다.
            System.out.println("Exception");
        }   // try-catch의 끝
        System.out.println(6);
    }   // main메서드의 끝
}
```

- 여기서는 두개의 catch블럭,
    - ArithmeticException 타입의 참조변수를 선언한 것과,
    - Exception타입의 참조변수를 선언한 것을 사용했다.
- try블럭에서 ArithmeticException이 발생했으므로 instanceof연산자로 catch블럭을 하나씩 차례대로 검사하게 되는데,
- **첫 번째 검사에서 일치하는 catch블럭을 찾았기 때문에 두번째 catch블럭은 검사하지 않게 된다.**
- 만약!! try블럭 내에서 ArithmeticException이 아닌 다른 종류의 예외가 발생한 경우에는 두번째 catch블럭이 실행!
- 이처럼 try-catch문의 마지막에 Exception타입의 참조변수를 선언한 catch블럭을 사용하면 어떤 종류의 예외가 발생하더라도 다 걸림!
