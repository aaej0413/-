# **Thread**

- 스레드(Thread)란 프로세스 내에서 실행되는 흐름의 단위를 말한다.
- 한 프로세스는 하나 이상의 스레드를 가지고 스레드를 동시에 실행할 수 있다.
- 이러한 샐행 방식을 멀티스레드(multithread)라고 하며,
- 자바는 이러한 멀티 스레드를 지원한다.

# Thread 생성 방법

1. 스레드 클래스를 직접 상속(extends)받는 방법
2. Runnable 인터페이스 이용 즉, Implement를 하는 방법이다.
    
    Runnable 인터페이스를 implement 했을 때 우리는 **run()** 메서드를 **오버라이딩** 해주어야 한다. 
    
    이 **run()** 메서드는 스레드가 실행할 부분을 기술하는 메서드이다.
    

### - **Thread 클래스를 상속받아 사용하는 방법**

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
 
 
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println(super.getName() + " thread. i=" + i);
        }
    }
 
    public static void main(String[] args) {
        MyThread2 thread1 = new MyThread2();
        MyThread2 thread2 = new MyThread2();
        thread1.start();
        thread2.start();
    }
}
```

**결과)**

```java
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

### - **Runnable 인터페이스를 implement 해서 사용하는 방법**

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
