# 04_Garbage Collection(가비지 컬렉션)
# 가비지 컬렉션(Garbage Collection)

## - 자바  말고 다른 언어의 메모리 관리는❓

- **C언어나 C++**같은 언어에서 ***메모리 관리는 프로그래머의 책임*** 이다.
- 필요한 **메모리 공간을** 라이브러리를 통해 **운영체제로부터 할당 받아 사용** 하다가 다 쓰면 다시 해제해서 운영체제로 **반환** 해야한다.
- 개발자가 꼼꼼히 메모리 관리를 하지 않는다면 메모리 공간을 할당 받기만 하고 반환하지 않아 프로세스가 점점 커지다가 죽게된다.
- 메모리를 해제하지 않아서 생기는 이런 버그를 **`“메모리 릭(Memory Leak)”`** 이라고 한다.

## - 자바는❓

- 자바는 메모리 관리라는 막중한 책임에서 프로그래머를 자유롭게 해줬다.
- 자바를 사용하는 프로그래머는 직접 메모리 공간의 할당과 반환을 수행하는 대신 **JVM을 통해 메모리를 할당** 받는다.
- ***더이상 사용되지 않는 메모리 공간은 JVM이 알아서 회수한 다음 해제*** 해준다.
- JVM의 이런 메모리 해제 동작을 **`“가비지 컬렉션(Garbage Collection)”`**  이라고 한다.

## 가비지(Garbage)는 뭐지?

> 가비지 컬렉션은 더이상 사용되지 않는 메모리 공간을 JVM알아서 회수해주는 동작을 의미한다.
이 때 **더이상 사용되지 않는 메모리 공간**이 바로 **`“가비지(Garbage)”`** 라고 할 수 있다.
> 

### 사용되지 않는 메모리 공간❓🧐

```java
Person person = new Person("Dave");
person.sayHello();

person = new Person("Eric");
person.sayHello();
```

- 위의 코드를 수행하면서 두 개의 객체가 생성된다.
- “Dave”라는 이름의 Person 객체와 “Eric”이라는 이름의 Person 객체가 실행되는 도중에 생성된다.
- ***생성된 객체*** 는 ***person 변수의 의해 참조*** 된다.
![image](https://user-images.githubusercontent.com/106788504/198931582-1aea422e-cc81-4fa4-ae18-41abf4a4e811.png)

- 그림을 그려보면,
    1. “Dave” 객체가 생성된 이후 person 변수에 의해 참조 된다. 이 때는 가비지가 없다.
    2. 이 후 “Eric” 객체가 생성되고 person 변수가 새로 생성된 “Eric” 객체를 참조한다.
    3. “Dave” 객체를 참조하던 person 변수가 “Eric” 객체를 참조하면서 “Dave” 객체를 참조하는 변수가 살라졌다.
    4. “Dave” 객체는 어떠한 경로로도 참조되지 않기 때문에 **“Unreachable” 상태**라고 하며,
    **이 객체는 가비지로 판단되어 회수** 당한다.

⭐️ ➡️ ***가비지 컬렉션을 수행하는 “가비지 컬렉터(Garbage Collector)”는 스택 변수로부터 참조 체인을 도달할 수 없는(Unreachable) 객체들을 가비지로 판단하고, 이 객체들의 메모리 공간을 회수한다.***

# Garbage Collection Process

### Step 1 : Marking 마킹

- 이 단계에서는 가비지 컬렉터가 사용중인 메모리와 사용하지 않는 메모리 조각을 식별한다.

![image](https://user-images.githubusercontent.com/106788504/198931623-532bc665-7bfe-4563-b835-7209503a8703.png)


- 참조된 객체는 파란색으로 표시되고, 참조되지 않은 객체는 금색으로 표시된다.
- 참조 여부를 판단하기 위해서는 마킹 단계에서 모든 객체를 스캔해야 하는데,
- 이경우 프로세스 시간이 많이 소요될 수 있다.

### Step 2 : Normal Deletion 일반 삭제

- 일반 삭제는 참조되지 않은 객체를 제거하여 참조된 객체와 포인터를 여유 공간으로 남긴다.
![image](https://user-images.githubusercontent.com/106788504/198931647-b4933fbe-b64f-445b-ac02-880e3f073ee8.png)


- 메모리 할당자는 새 객체를 할당할 수 있도록 참조 여유 공간을 잡는다.
- 성능을 향상시키기 위해 참조되지 않은 객체를 삭제하는 것 외에도 참조된 나머지 객체를 압축할 수도 있다.
- 참조된 객체를 함께 이동하면 새 메모리 할당이 훨씬 쉽고 빨라진다.

![image](https://user-images.githubusercontent.com/106788504/198931688-9613e970-54fa-4328-8f63-bdb87d9da48e.png)



**참고 자료**

> [https://www.oracle.com/technetwork/tutorials/tutorials-1876574.html](https://www.oracle.com/technetwork/tutorials/tutorials-1876574.html)
> 
> 
> [https://www.oracle.com/webfolder/technetwork/tutorials/obe/java/gc01/index.html](https://www.oracle.com/webfolder/technetwork/tutorials/obe/java/gc01/index.html)
>
