# 16_래퍼(wrapper)클래스
> 객체지향 개념에서 모든 것은 객체로 다루어져야 한다.
그러나 자바에서는 8개의 기본형을 객체로 다루지 않는데,
이것이 바로 자바가 객체지향 언어가 아니라는 얘기를 듣는 이유다. 대신! 보다 높은 성능을 얻을 순 있다.
> 

> **기본형(primitive type)** 변수도 어쩔 수 없이 **객체도 다뤄야 하는 경우**가 있다.
> 

***예를 들면,***

1. 매개변수로 객체를 요구할 때,
2. 기본형 값이 아닌 객체로 저장해야 할 때,
3. 객체간의 비교가 필요할 때

> 이 때 사용되는 것이 **`래퍼(wrapper)클래스`** 이다.
8개의 기본형을 대표하는 8개의 래퍼클래스가 있는데, 이 클래스들을 이용하면 **기본형 값을 객체도 다룰 수 있다.**
> 

> 래퍼 클래스들은 객체 생성시에 생성자의 인자로 주어진 각 자료형에 맞는 값을 내부적으로 저정하고 있으며, 관련된 여러 메서드가 정의되어 있다.
> 

![스크린샷 2022-07-09 오후 7.44.17.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/91160e21-154b-4c39-8edc-10239c62d47a/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-07-09_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_7.44.17.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220709T104623Z&X-Amz-Expires=86400&X-Amz-Signature=7a09d3cea5432307ea9304f67b42fca26587bff17d5a0187a86a53114d0b48cc&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-07-09%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25207.44.17.png%22&x-id=GetObject)

- 래퍼 클래스의 생성자는 ***매개변수***로 **`문자열`** 이나 **`각 자료형의 값`** 들을 인자로 받는다.
- 이 때 주의해야할 것은 생성자의 ***매개변수로 문자열을 제공할 때***, `**각 자료형에 알맞은 문자열을 사용**`‼️
- 예를 들어 **“new Integer(”1.0”);** 이렇게 사용 ❌ 왜냐면 **NumberFormatException이 발생**한다.
- 래퍼클래스들은 MAX_VALUE, MIN_VALUE, SIZE, BYTES, TYPE등의 static 상수를 공통적으로 가지고 있다.

### ex)

```java
/*
래퍼(wrapper)클래스 예제
 */
public class Ex9_14 {
    public static void main(String[] args) {

        Integer i = new Integer(100);
        Integer i2 = new Integer("100");

        System.out.println("i==i2 ? " + (i==i2));
        System.out.println("i.equals(i2) ? " + i.equals(i2));
        System.out.println("i.compareTo(i2) = " + i.compareTo(i2));     // 값이 같으면 0을 리턴.
        System.out.println("i.toString() = " + i.toString());

        System.out.println("--------------------------------------------");

        System.out.println("MAX_VALUE = " + Integer.MAX_VALUE);
        System.out.println("MIN_VALUE = " + Integer.MIN_VALUE);
        System.out.println("SIZE = " + Integer.SIZE + " bits");
        System.out.println("'BYTES = " + Integer.BYTES + "bytes");
        System.out.println("TYPE = " + Integer.TYPE);
    }
}
```

**실행 결과**

```java
i==i2 ? false
i.equals(i2) ? true
i.compareTo(i2) = 0
i.toString() = 100
--------------------------------------------
MAX_VALUE = 2147483647
MIN_VALUE = -2147483648
SIZE = 32 bits
BYTES = 4bytes
TYPE = int
```

### 실행결과 equals가 왜 true야❓

- 래퍼 클래스들은 모두 equals()가 오버라이딩 되어 있어서 주소값이 아닌 객체가 가지고 있는 값을 비교한다.
- **오토박싱**이 된다고 해도 ***Integer객체에 비교연산자를 사용할 수 없다.***
- 대신 **compareTo()** 를 제공한다.

```java
/*
Integer 클래스의 equals()
*/
public boolean equals(Objectobj) {
    if (objinstanceofInteger) {
        return value == ((Integer)obj).intValue();
    }
    return false;
```

## compareTo()

- ***숫자의 비교 같은 경우***는  ***크다(1)***, ***같다(0)***, ***작다(-1)*** 의 관한 결과값을 리턴.
    - 기준 값과 비교대상이 동일한 값일 경우 0
    - 기준 값이 비교대상 보다 작은 경우 -1
    - 기준 값이 비교대상 보다 큰 경우 1
- ***문자열의 비교 같은 경우*** 는 ***같다(0)***, ***그 외 양수/음수값***  같은 결과를 리턴.
