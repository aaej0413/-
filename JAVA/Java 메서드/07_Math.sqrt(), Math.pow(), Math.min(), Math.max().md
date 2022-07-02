# 제곱근 구하기, 최대값,최소값 구하기!
> **1. Math.sqrt()**
> 
- Math 클래스가 제공하는 메소드는 모두 정적이므로 따로 import 할 필요 없음.
- 주어진 숫자의 제곱근을 반환.
- 숫자가 음수이면 NaN을 반환.

```java
public class MathSqrt {
	public static void main(String[] args) {

		System.out.println(Math.sqrt(9));   //3.000000
		System.out.println(Math.sqrt(25));  //5.000000
		System.out.println(Math.sqrt(100));  //10.000000
	}
}
```



> **2. Math.pow()**
> 
- 제곱을 계산하는 함수이다.

```java
public class MathPow {
	public static void main(String[] args) {

		System.out.println(Math.pow(2,3));  //12.000000
		System.out.println(Math.pow(3,3));  //27.000000
		System.out.println(Math.pow(3,4));  //81.000000
	}
}
```


> **3. Math.min(파라미터1, 파라미터2)**
> 
- 둘 중에 작은 값을 리턴

```java
public class MathMin {
	public static void main(String[] args) {

		System.out.println(Math.min(3.14,5.18));  //3.14
		System.out.println(Math.min(9,13));  //9
		System.out.println(Math.min(3,4));  //3
	}
}
```



> **4. Math.max(파라미터1, 파라미터2)**
> 
- 둘 중에 작은 값을 리턴

```java
public class MathMin {
	public static void main(String[] args) {

		System.out.println(Math.max(3.14,5.18));  //5.18
		System.out.println(Math.max(9,13));  //13
		System.out.println(Math.max(3,4));  //4
	}
}
```
