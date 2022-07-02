# 문자열이 포함되어 있는지 확인하는 함수

> 1. contains
> 
- **A.contains(B)**라고 했을 때, **A문자열 중에 B라는 문자열이 포함되어 있으면 true, 아니면 false 반환.**
- 대소문자를 구분하기 때문에 대소문자 구분없이 확인 하고 싶다면 **toUpperCase()**나 **toLowerCase()**를 사용.
- contains 함수는 B변수가 null이면 NullPointerException이 발생.

```java
String s1 = "Hello world, java!";

System.out.println(s1.contains("Hello"))   //true
System.out.println(s1.contains("JaVa"));   //false
System.out.println(s1.contains("h"));      //false
System.out.println(s1.toUpperCase().contains("JAVA"));   //true
System.out.println(s1.toUpperCase().contains("H"));      //true
```

> 2. equals
> 
- **A.equals(B)**라고 했을 때, **A문자열이 B문자열과 완전히 동일한지 비교하여 일치여부를 반환.**
- 대소문자를 구분하기 때문에 대소문자 구분 없이 확인하고 싶다면 **equalsIgnoreCase()**를 사용.
- equals 함수는  B변수가 null이여도 NullPointerException 발생시키지 않음.

```java
String s1 = "hi";
String s2 = "hi";
String s4 = "HI";

System.out.println(s1.equls(s2));   //true
System.out.println(s1.equls(s4));   //false
System.out.println(s1.equalsIgnoreCase(s4)); //true
```

