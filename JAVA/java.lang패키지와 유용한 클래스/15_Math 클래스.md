# 15_Math 클래스
> **`Math클래스의 생성자`** 는 접근제어자가 **`private`** 이기 때문에 다른 클래스에서 Math인스턴스를 생성할 수 없도록 되어있다.
그 이유는 클래스 내에 **`인스턴스 변수가 하나도 없어`** 서 인스턴스를 생성할 필요가 없기 때문이다.
Math클래스의 **`메서드는 모두 static`** 이며, 아래와 같이 **`2개의 상수만 정의`** 해 놓았다.
> 

```java
public static final double E = 2.7182818284590452354;   // 자연로그의 밑
public static final double PI = 3.14159265358979323846; // 원주율
```

## 올림, 버림, 반올림 - Math.round()

Q. 90.7552라는 값을 소수점 ***셋째자리에서 반올림*** 후 ***소수점 두번째 자리까지의 값*** 을 얻고 싶으면?? 


1. 원래 값에 **`100을 곱`** 한다.
    1. 90.7552 * 100  →  **9075.52**
2. 위의 결과에 **`Math.round()를 사용`** 한다.
    1. Math.round(9075.52)  →  **9076** 
3. 위의 결과를 **`다시 100.0으로 나눈다.`**
    1. 9076 / 100.0  →  90.76
    2. 만약 정수형을 얻고 싶으면?? 9076 / 100 하면 됨!

- 소수점 넷째자리에서 반올림하고 소수점 세 자리 값까지 얻으려먼 1000으로 곱하고 1000.0으로 나누면 된다!!!

# Math의 메서드

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/42840a2b-2531-4710-8b93-0942984b2042/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220709T104021Z&X-Amz-Expires=86400&X-Amz-Signature=66b52067b7ab02627719c46276104287c53a73a516993a0b86973f7e74af7f8f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

### ex)

```java
import static java.lang.Math.*;
/*
Math의 메서드 예제
 */
public class Ex9_13 {
  public static void main(String[] args) {
      double val = 90.7552;
      System.out.println("round("+ val + ") = " + round(val)); // 반올림

      val *= 100;
      System.out.println("round("+ val + ") = " + round(val));  // 반올림

      System.out.println("round("+ val + ") / 100 = " + round(val)/100);// 반올림
      System.out.println("round("+ val + ") / 100.0 = " + round(val)/100.0);// 반올림
      System.out.println("----------------------------------------------");

      System.out.printf("ceil(%.1f) = %.1f%n", 1.1, ceil(1.1)); // 올림
      System.out.printf("floor(%.1f) = %.1f%n", 1.5, floor(1.5));// 버림
      System.out.printf("ceil(%.1f) = %.1f%n", -1.5, ceil(-1.5));// 올림
      System.out.printf("floor(%.1f) = %.1f%n", -1.5, floor(-1.5));// 버림
      System.out.printf("round(%.1f) = %d%n", 1.1, round(1.1));//반올림
      System.out.printf("round(%.1f) = %d%n", 1.5, round(1.5));// 반올림 
      System.out.printf("rint(%.1f) = %f%n", 1.5, rint(1.5));// 반올림
      System.out.printf("round(%.1f) = %d%n", -1.5, round(-1.5));// 반올림
      System.out.printf("rint(%.1f) = %f%n", -1.5, rint(-1.5));// 반올림
    }
}
```

**실행 결과**

```java
round(90.7552) = 91
round(9075.52) = 9076
round(9075.52) / 100 = 90
round(9075.52) / 100.0 = 90.76
-----------------------------------------------------
ceil(1.1) = 2.0
floor(1.5) = 1.0
ceil(-1.5) = -1.0
floor(-1.5) = -2.0
round(1.1) = 1
round(1.5) = 2     // 반환 값이 int
rint(1.5) = 2.000000   // 반환 값이 double
round(-1.5) = -1
rint(-1.5) = -2.000000
```

- **rint()** 도 round()처럼 소수점 첫 째 자리에서 반올림 하지만, **반환값이 double**이다.
- **음수를 반올림할 때,** round(-1.5)의 결과는 -2가 아니라 -1이다.
- ***round()*** 는 항상 ***가까운 “큰” 정수***로 ***반올림***하기 때문이다. (-2보다 -1이 더 큼)
- ***rint()*** 도 가장 ***가까운 정수***로 ***반올림*** 하지만 ***두 정수의 정가운데*** 있는 값은 ***짝수 정수***로 결과를 ***반환***한다.
