# JVM

- JVM **Java Virtual Machine (자바 가상 머신)의 줄임말.**
- 직역하면 **'자바를 실행하기 위한 가상 기계'** 라고 할 수 있다.
- 자바 코드를 컴파일하여 .class 바이트 코드로 만들면 이 코드가 자바 가상 머신 환경에서 실행. J
- VM은 자바 실행 환경 JRE(Java Runtime Environment)에 포함되어 있음.
- 현재 사용하는 컴퓨터의 운영체제에 맞는 자바 실행환경 (JRE)가 설치되어 있다면 자바 가상 머신이 설치되어 있다는 뜻입니다.

> Java는 어떠한 플랫폼에 영향을 받지 않는다.
> 
- **JVM을 사용하면 하나의 바이트 코드(.class)로 모든 플랫폼에서 동작하도록 할 수 있습니다.**

> .class 파일은 바이트 코드라고 하는데 사람이 쓰는 자바 코드에서 컴퓨터가 읽는 기계어로의 중간 단계라고 생각하시면 됩니다.
> 

## - C언어와 Java 비교

**C언어의 경우**

![https://blog.kakaocdn.net/dn/bSyyF2/btruTDnDSKz/73EXAY7aiTWRzHKlM2OFpK/img.png](https://blog.kakaocdn.net/dn/bSyyF2/btruTDnDSKz/73EXAY7aiTWRzHKlM2OFpK/img.png)

- C언어로 작성된 Test.c가 있음
- 이 Test.c를 윈도우 컴파일러를 사용해서 컴파일하면 Test.exe가 만들어짐.
- 윈도우 컴파일러로 컴파일되었기에 Test.exe는 윈도우에서만 실행되는 실행 파일.
- 리눅스 운영체제에서는 실행 못함. **즉 C / C++에서는 컴파일 플랫폼과 타겟 플랫폼이 다를 경우에는 프로그램이 동작하지 않음.**
- 만약 이 Test.exe 파일을 리눅스 운영체제에서 실행하려면 리눅스 환경을 타겟으로 크로스 컴파일을 해서 리눅스 운영체제에 맞는 실행 파일을 새로 만들어야 함.

**Java의 경우**

![https://blog.kakaocdn.net/dn/56cSc/btruTEtjRXJ/r1JNTkEuEeY8cSKtqcXCRK/img.png](https://blog.kakaocdn.net/dn/56cSc/btruTEtjRXJ/r1JNTkEuEeY8cSKtqcXCRK/img.png)

- Java의 경우에는 Java언어로 작성된 Test.java는 컴파일하면 Test.class 파일이 생성.
- **생성된 바이트 코드는 각자의 플랫폼에 설치되어 있는 자바 가상 머신(JVM)이 운영체제에 맞는 실행 파일로 바꿔줌.**
- 즉, Java에서는 C언어와는 달리 JVM을 사용하기 때문에 각자의 플랫폼에 맞게끔 컴파일을 따로따로 해줘야 할 필요가 없음.
- 하나의 바이트 코드로 JVM이 설치되어 있는 모든 플랫폼에서 동작이 가능.

## ***※ Java는 플랫폼에 종속적이지 않지만 JVM은 플랫폼에 종속적이다.***

- Java는 컴파일된 바이트코드로 어떤 JVM에서도 동작시킬 수 있기 때문에 플랫폼에 의존적이지 않음.
- 하지만 반대로 자바 가상 머신(JVM)은 플랫폼에 의존적.
- 즉 리눅스의 JVM과 윈도우의 JVM은 서로 다름.
- 자바로 작성된 모든 프로그램은 자바 가상 머신에서만 실행될 수 있으므로, 자바 프로그램을 실행하기 위해서는 반드시 자바 가상 머신이 설치되어 있어야 함.
- 따라서 오라클은 대부분의 주요 운영체제뿐만 아니라 웹 브라우저, 스마트 폰, 가전기기 등에서도 자바 가상 머신을 손쉽게 설치할 수 있도록 지원.

## **자바 프로그램의 실행 과정과 JVM**

![https://blog.kakaocdn.net/dn/bXdEIg/btru3sF159q/aS1KNKZS4xGeQTnRnZuoy1/img.png](https://blog.kakaocdn.net/dn/bXdEIg/btru3sF159q/aS1KNKZS4xGeQTnRnZuoy1/img.png)

- 우리가 자바로 .java 코드를 작성하고 파워쉘이나 터미널에 있는 자바 컴파일러인 javac에 컴파일 명령을 내리면 .class 파일이 만들어짐.
- 이후 이 바이트 코드는 클래스 로더를 통해 JVM Runtime Data Area로 로딩되고,
- 로딩된 .class 바이트 코드를 실행할 컴퓨터에 깔린 JVM에 가져다주면 그 컴퓨터가 이 프로그램을 실행할 때 이 JVM이 그때그때 기계어로 해석.
