# 06_문자열(String)의 비교  

> 문자열을 만들 때는 두가지 방법이 있다.  
> 
**1.** **문자열 리터럴을 지정하는 방법**  

**2.** **String클래스의 생성자를 사용해서 만드는 방법  

**→** new 연산자는 메모리의 `heap`영역에 할당되고, 리터럴 방식은 `String Constant Pool`영역에 할당된다.  

> 

### 1. 문자열 리터럴을 지정하는 방법

```java
String str1 = "abc";     // 문자열 리터럴 "abc"의 주소가 str1에 저장됨.
String str2 = "abc";     // 문자열 리터럴 "abc"의 주소가 str2에 저장됨.
```

### 2. String 클래스의 생성자를 사용해서 만드는 방법

```java
String str3 = new String("abc");    // 새로운 String인스턴스를 생성
String str4 = new String("abc");    // 새로운 String인스턴스를 생성
```

- **`String클래스의 생성자를 이용`** 한 경우에는 **`new연산자에 의해 메모리할당`** 이 이루어지기 때문에
**`항상 새로운 String인스턴스가 생성`** 된다.
- 그러나 **`문자열 리터럴은 이미 존재하는 것을 재사용`** 하는 것이다.

![스크린샷 2022-07-08 오후 1.59.27.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/35062697-7151-4207-8891-70054238bce8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-07-08_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1.59.27.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220709T095831Z&X-Amz-Expires=86400&X-Amz-Signature=463f8c546d51a81d3bb5790bebc9153936f324a5244a11342f4306500ff4f7b7&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-07-08%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25201.59.27.png%22&x-id=GetObject)

---

### ex)

```java
/*
문자열 String 비교
 */
public class Ex9_6 {
    public static void main(String[] args) {
        String str1 = "abc";
        String str2 = "abc";
        System.out.println("String str1 = \"abc\";");
        System.out.println("String str2 = \"abc\";");

        System.out.println("str1 == str2 ? " + (str1 == str2 ));
        System.out.println("str.equals(str2) ? " + str1.equals(str2));
        System.out.println();

        String str3 = new String("abc");
        String str4 = new String("abc");

        System.out.println("String str3 = \"abc\";");
        System.out.println("String str4 = \"abc\";");

        System.out.println("str3 == str4 ? " + (str3 == str4 ));
        System.out.println("str.equals(str2) ? " + str3.equals(str4));
    }
}
```

**실행 결과**

```java
String str1 = "abc";
String str2 = "abc";
str1 == str2 ? true
str.equals(str2) ? true

String str3 = "abc";
String str4 = "abc";
str3 == str4 ? false
str.equals(str2) ? true
```

- **equals()를 사용했을 때는** ***두 문자열의 내용(”abc”)을 비교***하기 때문에 두 경우 모두 true지만,
- String인스턴스의 주소를 “==”로 비교했을 때는 결과가 다르다.
