# int를 String으로, String을 int로 (문자열 숫자 변환)
> **1. toString / String.valueOf()**
> 
1. **toString으로 int type을 String type으로 변환하기**

```java
public class IntToString {
	public static void main(String[] args) {
		int intValue1 = 123;
		int intValue2 = -123;

		String str1 = Integer.toString(intValue1);  //"123"
		String str2 = Integer.toString(intValue2);  //"-123"

		System.out.println(str1);
		System.out.println(str2);
	}
}
```

> **2. String.valueOf()**
> 
1. **String.valueOf()으로 int type을 String type으로 변환하기**

```java
public class IntToString {
	public static void main(String[] args) {
		int intValue1 = 123;
		int intValue2 = -123;

		String str1 = String.valueOf(intValue1);  //"123"
		String str2 = String.valueOf(intValue2);  //"-123"

		System.out.println(str1);
		System.out.println(str2);
		}
}
```

> **3. Integer.parseInt()**
> 
- **입력 받은 문자열을 primitive type int형을 반환.**

```java
public class StringToInt {
	public static void main(String[] args) {
		String str1 = "456";
		String str2 = "-456";

		int intValue1 = Integer.parseInt(str1);
		int intValue2 = Integer.parseInt(str2);

		System.out.println(intValue1); // 456
		System.out.println(intValue2); // -456
		}
}
```

> **4. Integer.valueOf()**
> 
- **입력 받은 문자열을 wrapper Object인 integer를 반환.**

```java
public class StringToInt {
	public static void main(String[] args) {
		String str1 = "456";
		String str2 = "-456";

		int intValue1 = Integer.valueOf(str1).intValue();
		int intValue2 = Integer.valueOf(str2).intValue();

		System.out.println(intValue1); // 456
		System.out.println(intValue2); // -456
		}
}
```

> **5. int + “”**
> 
- **문자열에 int를 이어붙이면, 문자열이 반환되는 속성을 이용**

```java
public static void main(String[] args) {

        int i = 12345;
        int j = -98765;

        String s1 = i + "";
        String s2 = j + "";

        System.out.println(s1);  // 12345
        System.out.println(s2);  // -98765
    }
```
