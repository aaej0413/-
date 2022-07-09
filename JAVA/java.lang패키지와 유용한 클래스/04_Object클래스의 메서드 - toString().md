# 04_Object클래스의 메서드 - toString()
> 이 메서드는 **인스턴스에 대한 정보를 문자열(String)로 제공**할 목적으로 정의한 것이다.
인스턴스의 정보를 제공한다는 것은 대부분의 경우 **인스턴스 변수에 저장된 값들을 문자열로 표현**한다는 뜻이다.
> 

### Object클래스에 정의된 toString()

```java
public String toString() {
		retrun get.Class().getName()+"@"+Integer.toHexString(hasCode());
}
```

- 클래스를 작성할 때 toString()을 오버라이딩 하지 않는다면, 위와 같은 내용이 그대로 사용될 것이다.
- 즉, toString()을 호출하면 **`클래스이름`**과 **`16진수의 해시코`드**를 얻게 된다.

### ex)

```java
/*
toString() 간단히 써보기
 */
class Card {
    String kind;
    int number;

    Card() {
        this("SPADE", 1);
    }
    Card(String kind, int number) {
        this.kind = kind;
        this.number = number;
    }
}
public class Ex9_4 {
    public static void main(String[] args) {
        Card c1 = new Card();
        Card c2 = new Card();

        System.out.println(c1.toString());
        System.out.println(c2.toString());
    }
}
```

**실행 결과**

```java
objclassprac.Card@35bbe5e8
objclassprac.Card@2c8d66b2
```

- Card인스턴스 두 개를 생성한 다음, 각 인스턴스에 toString()을 호출한 결과를 출력했다.
- Card클래스에서 toString()을 오버라이딩하지 않았기 때문에 Card 인스턴스에 toString을 호출하면,
Object클래스의 toString()이 호출된다.
- 그래서 위의 결과와 같은 클래스이름 + 해시코드가 출력되었다.
- 서로 다른 인스턴스에서 toString()을 호출하였기 때문에 해시코드 값은 다르다.

# toString()의 오버라이딩

> String클래스의 toString()은 String인스턴스가 갖고 있는 문자열을 반환하도록 오버라이딩 되어있고,
Date클래스의 경우, Date인스턴스가 갖고 있는 날짜와 시간을 문자열로 변환하여 반환하도록 오버라이딩 되어 있다.
> 

> toString()은 일반적으로 **인스턴스나 클래스에 대한 정보** 또는 **인스턴스 변수들의 값을 문자열로 변환하여 반환**하도록 오버라이딩하는 것이 보통이다.
> 

### ex)

```java
/*
toSting() 오버라이딩
 */
class Card2 {
    String kind;
    int number;

    Card2() {
        this("SPADE", 1);  // Card(String kind, int number)를 호출
    }
    Card2(String kind, int number) {
        this.kind = kind;
        this.number = number;
    }

    public String toString() {
        return "kind : " + kind + ", number : " + number;
    }   // Card2인스턴스의 kind와 number를 문자열로 반환한다.
}
public class Ex9_5 {
    public static void main(String[] args) {
        Card2 c1 = new Card2();
        Card2 c2 = new Card2("HEART",10);

        System.out.println(c1.toString());
        System.out.println(c2.toString());
    }
}
```

**실행 결과**

```java
kind : SPADE, number : 1
kind : HEART, number : 10
```

- Card2인스턴스의 toString()을 호출하면 인스턴스가 갖고 변수 kind와 number의 값을 문자열로 바꿔 반환하도록 오버라이딩 했다.
- Object클래스에 정의된 toString()의 접근 제어자가 public이므로 Card2에서 정의된 toString()도 접근 제어자가 public이다.
- 왜냐하면, 조상의 정의된 메서드를 자손에서 오버라이딩 할 때, 조상의 접근 제어자아 같거나 더 넓어야하기 때문이다.

