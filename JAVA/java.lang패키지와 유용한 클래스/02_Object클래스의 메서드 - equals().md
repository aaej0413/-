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
    
![image](https://user-images.githubusercontent.com/106788504/198930753-bf2bf563-9873-42d3-a023-ef4f6556b6b6.png)
    

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
    
![image](https://user-images.githubusercontent.com/106788504/198930788-6d84797c-2bd0-4c2d-b0c7-69244e8b5163.png)
