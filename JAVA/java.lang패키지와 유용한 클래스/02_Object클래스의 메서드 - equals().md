# 02_Object클래스의 메서드 - equals()
> **매개변수**로 **객체의 참조변수를 받아서 비교**하여 그 결과를 booelan값으로 알려주는 역할을 한다.
> 

<aside>
💢 참고 
  
  객체를 생성할 때, 메모리의 비어있는 공간을 찾아 생성하므로 서로 다른 두 개의 객체가 같은 주소를 갖는 일은 있을 수 없다. 
  
  그러나 두 개 이상의 참조변수가 같은 주소값을 갖는 것(한 객체를 참조하는 것)은 가능하다.

</aside>

### **ex)**

```java
/*
equals() 간단하게 써보기
 */
public class Ex9_1 {
    public static void main(String[] args) {
        Value v1 = new Value(10);
        Value v2 = new Value(10);

        if(v1.equals(v2)) {
            System.out.println("v1과 v2는 같습니다.");
        } else {
            System.out.println("v1과 v2는 다릅니다.");
        }

    }
}

class Value {
    int value;

    Value(int value) {
        this.value = value;
    }
}
```

**실행 결과**

```java
v1과 v2는 다릅니다.
```

- equals메서드는 주소값으로 비교를 하기 때문에, 두 Value인스턴스의 멤버변수 value의 값이 10으로 같아도 결과는 false이다.
    
    ![스크린샷 2022-07-08 오전 9.50.45.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/642eedcb-2cb2-4cdf-b7e1-96e7b3f9de72/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-07-08_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_9.50.45.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220709T095125Z&X-Amz-Expires=86400&X-Amz-Signature=dc1af324ae9078cbe1b63a37ab59b380f694fa946d2eb600216f681a7adb173b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-07-08%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%25209.50.45.png%22&x-id=GetObject)
    

# equals( )의 오버라이딩

> **equals메서드는** 두 개의 참조변수가 같은 객체를 참조하고 있는지.
즉 ,두 **참조변수의 주소값이 같은지를 판단**하는 기능밖에 할 수 없다.
**하지만** `equals메서드를 오버라이딩 하여` equals메서드로 `Value인스턴가 가지고 있는 value값을 비교`하도록 할 수 있다.
주소가 아닌 객체에 저장된 내용을 비교하도록 변경하면 된다.
> 

**ex)**

```java
/*
equals()메서드 오버라이딩
 */
class Person {
    long id;

    Person(long id) {
        this.id = id;
    }

    @Override
    public boolean equals(Object obj) {
        if (obj instanceof Person) {
            return id == ((Person)obj).id;  // obj가 Object 타입이므로 id값을 참조하기 위해서는 Person타입으로
        }else {                             // 형변환이 필요하다
            return false;       // 타입이 Person이 아니면 값을 비교할 필요도 없다.
        }
    }
}
public class Ex9_2 {
    public static void main(String[] args) {
        Person p1 = new Person(8011081111222222L);
        Person p2 = new Person(8011081111222222L);

        if(p1.equals(p2)) {
            System.out.println("p1과 p2는 같은 사람입니다.");
        }else {
            System.out.println("p1과 p2는 다른 사람입니다.");
        }
    }
}
```

**실행 결과**

```java
p1과 p2는 같은 사람입니다.
```

- equals메서드가 Person인스턴스의 주소값이 아닌 멤버변수 id의 값을 비교하도록 하기 위해 equals메서드를 오버라이딩 했다.
- 이렇게 함으로써 서로 다른 인스턴스일지라도 같은 id를 가지고 있다면 equals메서드로 비교했을 때 true를 얻게 할 수 있다.
    
    ![스크린샷 2022-07-08 오전 10.28.30.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f252f116-407f-4bae-83bd-4ebbd075e9f5/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-07-08_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_10.28.30.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220709T095152Z&X-Amz-Expires=86400&X-Amz-Signature=3b8f87fe6d159b23fbd1f4af046f91a54a1088064fe165e8a22f8ce07a474f8b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-07-08%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%252010.28.30.png%22&x-id=GetObject)
