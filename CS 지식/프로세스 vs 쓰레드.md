# *프로세스 vs Thread(쓰레드)*

## 1. 프로세스

- 운영체제로부터 CPU자원을 할당 받는 **작업의 단위**.
- 메모리에 올라와 실행중인 프로그램을 말한다.
- 기본적으로 프로세스당 최소 1개의 스레드(메인 스레드)를 가지고 있다.
- 프로세스는 각각 **독립된 메모리 영역** (Code, Data, Stack, Heap)을 할당 받는다.
(운영체제로부터 프로세서, 필요한 주소공간, 메모리 등의 자원을 할당 받음.)
- 각 프로세스는 별도의 주소 공간에서 실행되며, 한 프로세스는 다른 프로세스의 변수나 자료구조에 접근❌

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/18da5ccb-f86e-4407-bd4c-4e06425d3d28/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220702%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220702T064707Z&X-Amz-Expires=86400&X-Amz-Signature=357d84791aa55e085672b6765e1a000f1ad54bef51f0f32ce940af2f7852553c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

1. **코드(Code) 영역 :** 
    
    실행할 프로그램의 코드 및 매크로 상수가 기계어로 저장되는 영역이다.
    
2. **데이터(Data) 영역 :** 
    
    코드에서 선언한 전역 변수와 정적(static)변수가 저장되는 영역이다. 데이터 영역은 프로그램의 시작과 함께 할당되어 종료될 때 소멸된다.
    
3. **스택(Stack) 영역 :**
    
    함수 안에 선언된 지역변수, 매개변수, 리턴 값 등이 저장되고 함수 호출시 기록하고 종료되면 제거한다.
    
    스택이라는 자료구조 명칭에서도 알 수 있듯이 **LIFO(Last In First Out)** 를 따른다.
    
    재귀함수를 통해 너무 많은 함수를 호출하게 되는 경우 스택 영역이 초과하면서 **StackOverflow**(스택오버플로우) 에러가 발생한다.
    
4. **힙(Heap) 영역 :**
    
    동적으로 할당받은 영역이다. 동적으로 생성된 데이터들의 영역 (생성자를 통한 객체 생성)
    

> **CPU(프로세서)는 한 번에 하나의 프로세스만 처리할 수 있다. 그럼 컴퓨터의 멀티태스킹은 어떻게 가능하지???**
> 
- CPU가 프로세스들을 여러 번 왔다갔다 하면서 자원을 바꾸며 일하고 있음! **(Context Switching)** 우리는 그저 동시에 일어났다고 느끼고 있을 뿐~
- CPU는 프로세스의 상태를 파악하면서 왔다갔다 하는데,
- 상태는 **[PCB(Process Control Block)](https://www.notion.so/Spring-58cf917851864e31bff153a4d5c8b825)** 라는 공간에 저장된 데이터를 기반으로 파악하면서 처리한다.

### 1_1. PCB(Process Control Block)

- PCB는 운영체제에서 프로세스에 대한 정보를 저장하기 위한 자료구조이다.
- OS는 프로세스를 관리하기 위해 프로세스를 생성함과 동시에 고유한 PCB를 생성한다.
- 프로세스는 CPU를 할당받아 작업하다가도 context-switching 이 일어나면, 진행중 작업을 저장하고 CPU를 반납해야 하는데, 이 때 작업 진행상황이 PCB에 저장된다. 그 후 다시 CPU를 할당받게 되면 PCB안에 있던 정보들을 불러와서 작업이 멈춘 시점부터 다시 시작한다.
- PCB에는 다음과 같은 프로세스의 정보가 저장된다.
    1. 프로세스 식별자(Process ID)
    2. 프로세스 상태(Process State): 생성(create), 준비(ready), 실행(running), 대기(waiting), 완료(terminated)
    3. 프로그램 계수기(Program Counter): 프로세스가 다음에 실행할 명령어의 주소를 가리킨다.
    4. CPU 레지스터 및 일반 레지스터
    5. CPU 스케쥴링 정보: 우선 순위, 최종 실행시각, CPU점유 시간
    6. 메모리 관리 정보: 프로세스의 주소 공간
    7. 프로세스 계정 정보: 페이지 테이블, 스케쥴링 큐 포인터, 소유자, 부모
    8. 입출력 상태 정보
    9. 포인터: 부모프로세스, 자식 프로세스, 프로세스가 위치한 메모리 주소에 대한 포인터, 할당된 자원에 대한 포인터

### 1_2. 결론

- 프로세스는 여러개 자식 프로세스 중 하나에 문제가 발생해도 다른 자식 프로세스에 영향이 확산되지 않아 안정성이 좋다.
- 하지만, 멀티 프로로세스는 **CPU는 하나의 프로세스만 실행**할 수 있어서 **다른 프로세스를 왔다갔다** 해야한다.
- 이렇게 왔다갔다 하는 행위. 즉, 자원을 교체하는 행위를 Context Switching이라고 한다.
- A 프로세스를 실행하다가 잠시 쉬고 PCB에 데이터 적재 후, B 프로세스를 실행하기 위해 B 프로세스 데이터를 다시 모두 가져와야한다.
- 그러므로 **CPU가 전체적인 프로세스 자원을 바꿔주는 Context Switching에서의 비효율이 상당**하다.
- 이러한 문제를 **쓰레드라는 개념을 통해 해결!!**

## 2. Thread(쓰레드)

- 프로세스가 할당받은 자원을 이용하는 **실행의 단위**.
- 스레드는 프로세스 내에서 각각 **Stack만 할당** 받고 **Code, Data, Heap 영역은 공유**한다.
- 프로그램 코드를 한 줄 씩 실행하는 것이 쓰레드의 역할이다.
- 한 프로세스는 하나 이상의 스레드를 가지고 스레드를 동시에 실행할 수 있다.
- 이러한 샐행 방식을 멀티스레드(multithread)라고 하며,
- 자바는 이러한 멀티 스레드를 지원한다.

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6f078dec-e814-4f5e-af4f-f73e6442545f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220702%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220702T064720Z&X-Amz-Expires=86400&X-Amz-Signature=574343bab9b177004c2051ed0fadaa345a49f05c60a0b804f37cf8618a816f86&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

### 2_1. 멀티 스레드

- 단일 프로세스 내에서 여러 스레드가 동시에 실행되는 것을 말한다.
- **Context Switching이 빠르다**(프로세스 자원의 전체 영역이 아닌 **Stack영역만 변경하면 된다.**)
- 멀티 스레드의 경우 자원을 공유하면서 동기화 문제가 발생한다.

## ✚ 멀티 프로세싱 vs 멀티 스레드

**멀티 프로세싱**

- 두 개 이상의 다수의 프로세스가 협력적으로 하나의 작업을 동시에 병렬적으로 처리하는 것
- 프로세스간 메모리 공유는안되기 때문에, IPC를 이용해 소통
- 하나의 프로세스에서 문제가 생겨도 다른 프로세스는 계속 진행할 수 있음.
- 컨텍스트 스위칭 비용이 높음

**멀티 스레딩**

- 단일 프로세스 내에서 여러 쓰레드로 나누어 동시에 실행
- 컨텍스트 스위칭 비용이 거의 없음
- 스택을 제외한 데이터,코드,힙 영역을 공유하기 때문에 공유하는데 편리함
- 임계영역의 문제가 있음

# 자바에서 Thread 생성 방법

1. 스레드 클래스를 직접 상속(extends)받는 방법
2. Runnable 인터페이스 이용 즉, Implement를 하는 방법이다.
    
    Runnable 인터페이스를 implement 했을 때 우리는 **run()** 메서드를 **오버라이딩** 해주어야 한다. 
    
    이 **run()** 메서드는 스레드가 실행할 부분을 기술하는 메서드이다.
    

### 1. **Thread 클래스를 상속받아 사용하는 방법**

- Thread 클래스를 이용하는 방식은 java.lang.Thread 클래스를 상속받아서 run 메서드를 재정의 (Overrideing) 하면 된다. run 메서드는 스레드가 실행동작하는 메서드로서,
개발자는 이 메서드에 실행 동작할 코드를 기술하면 된다.

**ex_01) Thread 1개 실행**

```java
package com.devkuma.tutorial.thread;
 
public class MyThread extends Thread {
 
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println("This is thread. i=" + i);
        }
    }
 
    public static void main(String[] args) {
        MyThread thread = new MyThread();
        thread.start();
    }
}
```

**결과)**

```
This is thread. i=0
This is thread. i=1
This is thread. i=2
This is thread. i=3
This is thread. i=4
This is thread. i=5
This is thread. i=6
This is thread. i=7
This is thread. i=8
This is thread. i=9
```

**ex_02) Thread 2개 실행**

```java
public class MyThread2 extends Thread {
 
    public MyThread2(String name) {
        super(name);
    }
 
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println(super.getName() + " thread. i=" + i);
        }
    }
 
    public static void main(String[] args) {
        MyThread2 thread1 = new MyThread2("first");
        MyThread2 thread2 = new MyThread2("second");
        thread1.start();
        thread2.start();
    }
}
```

**결과)**

```
first thread. i=0
first thread. i=1
second thread. i=0
second thread. i=1
second thread. i=2
first thread. i=2
second thread. i=3
second thread. i=4
second thread. i=5
second thread. i=6
second thread. i=7
second thread. i=8
second thread. i=9
first thread. i=3
first thread. i=4
first thread. i=5
first thread. i=6
first thread. i=7
first thread. i=8
first thread. i=9
```

- 실행 결과에서 볼 수 있듯이 스레드를 두개를 돌려서 불규칙하게 실행되면서 각자의 결과를 표시하는 것을 볼 수  있음.
- 우린 여기서 스레드의 장점을 볼 수 있다.
- 보통 스레드 없이 작업을 한다면 한 개의 작업이 다 끝나고 나서 다른 작업이 실행되는데,
- 스레드를 사용한다면 동시에 작업을 실행할 수 있기 때문에 시간도 효율적이고 비용도 적게 든다.

### 2. **Runnable 인터페이스를 implement 해서 사용하는 방법**

- 자바에서는 다중 상속이 안되게 규칙을 만들어 놨다.
- 왜 다중 상속이 불가능하게 만들었을까? 그 이유는 일단 만들 때는 편하지만 나중에 유지보수 하기가 너무 힘들기 때문이다.
- 다중 상속을 한다면 우리가 문제가 생겼을 때 상속받은 클래스들을 다 살펴봐야 하기 때문에 자바는 처음
    
    부터 이런 것을 막아 놓았다. 
    
- 하지만 우리가 다중 상속을 못하는 것은 아니다.
- 자바에서 인터페이스는 상속과 달리 여러개의 인터페이스를 implements 할 수 있기 때문에 스레드를 사용할 때도 Runnable 인터페이스를 implement해서 사용하는 방법이 널리 쓰인다.
- 우리가 앞서 상속해서 스레드를 사용하는 방법을 봤듯이 Runnable 인터페이스도 방법이 같다.
- implements 해서 run()메서드를 오버라이딩(Overriding)을 해주면 된다.

**ex_01) Thread 1개 실행**

```java
public class MyRunnable implements **Runnable** {
 
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println("This is thread. i=" + i);
        }
    }
 
    public static void main(String[] args) {
        MyThread thread = new MyThread();
        thread.start();
    }
}
```

**결과)**

```
This is thread. i=0
This is thread. i=1
This is thread. i=2
This is thread. i=3
This is thread. i=4
This is thread. i=5
This is thread. i=6
This is thread. i=7
This is thread. i=8
This is thread. i=9
```

# 스레드Thread의 우선순위

- 자바 스레드에서는 스레드에 우선순위를 부여하여 높은 우선 순위를 가진 스레드에게 실행할 우선권을 주어 실행시킬 수 있다.
- Thread 클래스 내부에서는 우선 순위를 정하기 위해 다음과 같은 상수를 제공하고 있다.

```java
/**
     * The minimum priority that a thread can have.
     */
    public final static int MIN_PRIORITY = 1;
 
   /**
     * The default priority that is assigned to a thread.
     */
    public final static int NORM_PRIORITY = 5;
 
    /**
     * The maximum priority that a thread can have.
     */
    public final static int MAX_PRIORITY = 10;
```

- 최하 1부터 최상 10까지 부여가 가능하고 디폴트로는 5가 부여된다.
- JVM에서는 스레드를 수행하고 끝나면 다음에는 실행 가능한 스레드 중에 한개를 골라 실행을 하게 되는데,
- 우선 순위가 높을 수록 실행될 확률이 높아진다.
- 우선 순위가 같을 때에는 스레드 스케줄러의 기준에 의하여 실행될 스레드가 결정된다.

**ex_01) Thread 2개에 우선 순위를 최상과 최하로 설정했다.**

```java
public class MyThreadPriority extends Thread {
 
    public MyThreadPriority(String name) {
        super(name);
    }
 
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println(super.getName() + " thread. i=" + i);
        }
    }
 
    public static void main(String[] args) {
        MyThread2 thread1 = new MyThread2("first");
        MyThread2 thread2 = new MyThread2("second");
 
        thread1.setPriority(Thread.**MAX_PRIORITY**);
        thread2.setPriority(Thread.**MIN_PRIORITY**);
 
        thread1.start();
        thread2.start();
    }
}
```

**결과)**

```java
first thread. i=0
second thread. i=0
first thread. i=1
second thread. i=1
first thread. i=2
second thread. i=2
first thread. i=3
second thread. i=3
first thread. i=4
first thread. i=5
first thread. i=6
first thread. i=7
first thread. i=8
first thread. i=9
second thread. i=4
second thread. i=5
second thread. i=6
second thread. i=7
second thread. i=8
second thread. i=9
```

- 결과에서 보이듯이 first가 second보다 우선순위가 높아서 먼저 끝나는 것을 볼 수 있다.
