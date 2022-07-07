# 08_checked예외, unchecked예외
# 자바의 예외는 크게 3가지로 나눌 수 있다.

- `체크 예외(Checked Exception)`
- `에러(Error)`
- `언체크 예외(Unchecked Exception)`

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5bf4b8aa-a17e-4218-9541-3f88727d1279/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220707%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220707T010910Z&X-Amz-Expires=86400&X-Amz-Signature=82154a6c2c51735c7c52e8f4456a903818f97e325696cafb4357fa3b755f09ac&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

# checkedd예외

```java
public class Ex8_7 {
    public static void main(String[] args) {
        throw new Exception();  // Exception을 고의로 발생시킨다.
    }
}
```

**컴파일 결과**

```java
java: unreported exception java.lang.Exception; 
must be caught or declared to be thrown
```

- 위와 같은 에러가 발생하면 컴파일이 완료되지 않을 것이다.
- 예외처리가 되어있지 않다는 에러.
- “**Exception클래스**와 그 자손들(**checked예외**)” 이 발생할 가능성이 있는 문장들에 대해 **예외 처리를 해주지 않으면 컴파일 조차 되지 않는다**.
- 즉, 체크 예외는 Exception 클래스의 하위 클래스들이다. `체크 예외의 특징은 반드시 에러 처리를 해야하는 특징(try/catch or throw)`을 가지고 있다.
    - 존재하지 않는 파일의 이름을 입력`(FileNotFoundException)`
    - 실수로 클래스의 이름을 잘못 적음`(ClassNotFoundException)`
    
    체크 예외의 예시는 이러한 것들이 있다.
    

# unchecked예외

```java
public class Ex8_8 {
    public static void main(String[] args) {
        throw new RuntimeException(); // RuntimeException을 고의로 발생시킨다.
    }
}
```

**컴파일 결과**

```java
Exception in thread "main" java.lang.RuntimeException
	at exception_handling.Ex8_8.main(Ex8_8.java:5)
```

- 이 예제는 예외처리를 하지 않았음에도 컴파일이 성공적으로 될 것이다.
- 그러나 실행을 하면, 위 실행결과처럼 RuntimeException이 발생하여 비정상적으로 종료.
- 이 예제가 명백해 RuntimException을 발생시키는 코드를 가지고 있고, 예외처리를 안했음에도 불구하고 성공적으로 컴파일 되었다.
- “**RuntimException**클래스와 그 자손(**unchecked예외**)”에 해당하는 예외는 **프로그래머의 실수로 발생하는 것들이기 때문에 예외처리를 강제하지 않는다.**
- 즉, 언체크 예외는 RuntimeException의 하위 클래스들을 의미한다. 이것은 체크 예외와는 달리 에러 처리를 강제하지 않습니다. 말 그대로실행 중에(runtime) 발생할 수 있는 예외를 의미한다.
    - 배열의 범위를 벗어난`(ArrayIndexOutOfBoundsException)`
    - 값이 null이 참조변수를 참조`(NullPointerException)`
    
    언체크 예외는 이러한 것들이 있다.
    

## 언체크 예외는 예외처리를 강제하지 않는 이유는 무엇일까?

```java
public class ArrayTest {
    public static void main(String[] args) {
        try {
            int[] list = {1, 2, 3, 4, 5};
            System.out.println(list[0]);
        } catch (ArrayIndexOutOfBoundsException e) {
            e.printStackTrace();
        }
    }
}
```

- 만약 언체크 예외가 에러 처리를 강제해야 했다면 단순히 배열을 만들어 배열의 원소를 출력하고자 하는데 `try/catch`문을 꼭 사용해야 한다.
- 이러한 RuntimeException은 개발자들에 의해 실수로 발생하는 것들이기 때문에 에러를 강제하지 않는 것이다.

> 컴파일러가 예외처리를 확인하지 않는 RuntimeException 클래스들은 **unchecked 예외**라고 부르고,
예외처리를 확인하는 Exception 클래스들은 **checked 예외**라고 부른다.
> 

# 체크 예외와 언체크 예외의 Rollback 여부

![https://user-images.githubusercontent.com/45676906/105691015-0d436b80-5f40-11eb-994d-58c55b8d47b8.png](https://user-images.githubusercontent.com/45676906/105691015-0d436b80-5f40-11eb-994d-58c55b8d47b8.png)

`체크 예외`와 `언체크 예외`의 차이점 중에 같이 보아야 할 점은 **Rollback의 여부**.

- **체크 예외** : **Rollback이 되지 않고 트랜잭션이 commit까지 완료**.
- **언체크 예외** : **Rollback이 된다.**

## **Checked Exception이 Rollback되지 않는 이유**

- 기본적으로 Checked Exception은 복구가 가능하다는 메커니즘을 가지고 있다.
- 예를 들어, 특정 이미지 파일을 찾아서 전송해 주는 함수에서 이미지를 찾지 못 했을 경우 기본 이미지를 전송한다는 복구 전략을 가질 수 있다.
- 정리하자면, 복구가 가능하니 Rollback은 진행하지 않는다는 의미이다.

# **예외 처리
예외를 처리하는 방법에는**

- `예외 복구`
- `예외 처리 회피`
- `예외 전환`이 있다.

## 예외 복구

- **예외 상황을 파악하고 문제를 해결하여 정상 상태로 돌려 놓는 방법**이다.

```java
publicsendFile(String fileName)() {
        File file;
try {
                file = FileFindService.find(fileName);
        }catch (FileNotFoundException e){
// 기본 파일을 찾아서 전송한다.
                file = FileFindService.find("default.png");
        }

        send(file);
        }
}
```

- 대부분의 상황에서 예외를 복구할 수 있는 경우는 거의 없기 때문에 자주 사용되지 않는다.
- 예를 들어, 유니크해야 하는 이메일 값이 중복되어 SQLException이 발생한다고 해도 복구할 수 있는 방법이 없다.
- 이런 경우에는 RuntimeException을 발생시키고 입력을 다시 유도하는 것이 현실적이다.
- 혹시나 예외 복구를 사용할 일이 생긴다면 위처럼 예외를 복구하는 방식보다는
- 아래처럼 코드의 흐름으로 제어하는 것이 좋다.

```java
public voidsendFile(String fileName){
	if(FileFindService.existed(filename)){
	// 파일이 있는 경우 해당 파일을 찾아서 전송한다.
                send(FileFindService.find(fileName));
        }else {
	// 파일이 없는 경우 기본 이미지를 전송한다.
                send(FileFindService.find("default.png"));
        }
}
```

## 예외 처리 회피

- 예외 처리를 직접 담당하지 않고 호출한 쪽으로 던져 회피하는 방법이다.
- 긴밀하게 역할을 분담하고 있는 관계가 아닐 경우 예외를 던지는 것은 무책임한 방법이다.

```java
public ObjectsomeMethod()throws IOException {
        ...
}
```

## 예외 전환

- 예외 처리 회피와 비슷하게 메소드 밖으로 예외를 던지지만,
- 그냥 던지지 않고 적절한 예외로 전환해서 넘기는 방법이다.
- 명확한 의미로 전달되기 위해 적합한 의미를 가진 예외로 변경해야 한다.

```java
publicObject method() {
try {
                ...
        }catch (IOException e) {
throw new CustomException ("IOException 발생");
        }
}

public class CustomException extends RuntimeException{
    public CustomException(String message) {
			super(message);
    }
}
```

- 보통 예외 처리를 하기 위해서 위와 같이 RuntimeException을 상속 받은 클래스로 전환하여 던진다.

# 정리

- **예외 복구 전략이 명확**하고 **복구가 가능**하면 **Checked Exception을 try-catch로 잡아서 예외 복구**를 하거나, **코드의 흐름으로 제어**하는 것이 좋다.
- 그러나 이러한 경우는 흔하지 않기 때문에 Checked Exception이 발생하면 더 구체적인 UnChecked Exception을 발생시키고 예외에 대한 메시지를 명확하게 전달하는 것이 효과적이다.
- 무책임하게 상위 메서드에 throw로 예외를 던지는 행위를 하지 않는 것이 좋다. 상위 메서드들의 책임이 그만큼 증가하기 때문이다.
- Checked Exception은 기본 트랜잭션 속성에서 Rollback을 진행하지 않는다.

# **올바른 예외 처리 방식**

- 예외 복구 전략이 명확하고 복구가 가능하다면 Checked Excetpion을 try-catch로 잡아서 예외를 복구하는 것이 좋다.
- 복구가 불가능한 Checked Exception이 발생하면 더 구체적인 Unchecked Exception을 발생시키고 예외에 대한 메시지를 명확하게 전달하는 것이 좋다.
- 무책임하게 상위 메서드에 throw로 예외를 던지는 것은 상위 메서드의 책임이 증가하기 때문에 좋지 않은 방법이다.

  
   
<aside>
👉🏻 참고 
  
- [https://devlog-wjdrbs96.tistory.com/351] 
  
- [https://steady-coding.tistory.com/583]

</aside>
