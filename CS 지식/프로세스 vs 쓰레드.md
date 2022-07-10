# *프로세스 vs Thread(쓰레드)*

## 1. 프로세스

- 운영체제로부터 CPU자원을 할당 받는 **작업의 단위**.
- **메모리에 올라와 실행중인 프로그램**을 말한다.
    
    *ex) 웹 브라우저를 2개 실행 → 두개의 웹 프로세스가 생성.*
    
- 기본적으로 프로세스당 최소 1개의 스레드(메인 스레드)를 가지고 있다.
- 프로세스는 각각 **독립된 메모리 영역** (Code, Data, Stack, Heap)을 할당 받는다.
(운영체제로부터 프로세서, 필요한 주소공간, 메모리 등의 자원을 할당 받음.)
- 각 프로세스는 별도의 주소 공간에서 실행되며, 한 프로세스는 다른 프로세스의 변수나 자료구조에 접근❌

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/18da5ccb-f86e-4407-bd4c-4e06425d3d28/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220710%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220710T023515Z&X-Amz-Expires=86400&X-Amz-Signature=255d69ecc6b31eeb3993b2e42b058340f0ee7f9ae536add11410f8adfa76d1af&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

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
    

### 1_2. 멀티 태스킹(Multi Tasking)

- 2가지 이상의 작업을 동시에 처리하는 것.

> **CPU(프로세서)는 한 번에 하나의 프로세스만 처리할 수 있다. 그럼 컴퓨터의 멀티태스킹은 어떻게 가능하지???**
> 
- CPU가 프로세스들을 여러 번 왔다갔다 하면서 자원을 바꾸며 일하고 있음! **(Context Switching)** 우리는 그저 동시에 일어났다고 느끼고 있을 뿐~
- CPU는 프로세스의 상태를 파악하면서 왔다갔다 하는데,
- 상태는 **[PCB(Process Control Block)](https://www.notion.so/Spring-58cf917851864e31bff153a4d5c8b825)** 라는 공간에 저장된 데이터를 기반으로 파악하면서 처리한다.

### 주의!! → 멀티 태스킹이 꼭 멀티 프로세스를 뜻하는 건 아님!

- 한 프로세스 내에서도 멀티 태스킹을 할 수 있도록 만들어진 애플리케이션도 있음 (음악, 메신저 등)
    
    *ex) 메신저 : 채팅 기능을 제공하면서 동시에 파일 전송도 가능.*
    

> 어떻게?? → **멀티 쓰레드를 이용!**
> 
- 멀티 프로세스는 애플리케이션 단위의 멀티 태스킹.
- 멀티 스레드는 애플리케이션 내부에서의 멀티 태스킹.

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a8259fd3-e48d-402c-bfd6-64df27015fc8/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220710%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220710T023558Z&X-Amz-Expires=86400&X-Amz-Signature=257953be80cf202dd4323768f80135f4d589c88cbdadcf09f6d839ec2437a104&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

### 1_2. PCB(Process Control Block)

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

### 1_3. 결론

- 프로세스는 여러개 자식 프로세스 중 하나에 문제가 발생해도 다른 자식 프로세스에 영향이 확산되지 않아 안정성이 좋다.
- 하지만, 멀티 프로세스는 **CPU는 하나의 프로세스만 실행**할 수 있어서 **다른 프로세스를 왔다갔다** 해야한다.
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

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6f078dec-e814-4f5e-af4f-f73e6442545f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220710%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220710T023618Z&X-Amz-Expires=86400&X-Amz-Signature=2b1f0351ea61e441e61c62b6ef6d48d28a4e843846f6aa460bfb484d5eb09886&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

### 2_1. 멀티 스레드

- 단일 프로세스 내에서 여러 스레드가 동시에 실행되는 것을 말한다.
- **Context Switching이 빠르다**(프로세스 자원의 전체 영역이 아닌 **Stack영역만 변경하면 된다.**)
- 멀티 스레드의 경우 자원을 공유하면서 동기화 문제가 발생한다.

## ✚ 멀티 프로세스 vs 멀티 스레드

**멀티 프로세스**

- 두 개 이상의 다수의 프로세스가 협력적으로 하나의 작업을 동시에 병렬적으로 처리하는 것
- 프로세스간 메모리 공유는안되기 때문에, IPC를 이용해 소통
- 각자 할당받은 자신의 메모리를 가지고 실행하기 때문에 서로 독립적이다.
- 그래서, 하나의 프로세스에서 문제가 생겨도 다른 프로세스에게는 영향을 미치지 않는다.
- 컨텍스트 스위칭 비용이 높음

**멀티 스레드**

- 단일 프로세스 내에서 여러 쓰레드로 나누어 동시에 실행
- 컨텍스트 스위칭 비용이 거의 없음
- 스택을 제외한 데이터,코드,힙 영역을 공유하기 때문에 공유하는데 편리함
- 임계영역의 문제가 있음
즉, 하나의 프로세스 내부에 생성되기 때문에 하나의 스레드가 예외를 발생시키면 프로세스 자체가 종료될 수 있어 다른 쓰레드에게 영향을 미친다.

- ex) 멀티 프로세스인 워드와 액셀을 동시에 사용하던 중, 워드에 오류가 생겨서 먹통이 되더라도 엑셀은 여전히 사용 가능하다.
- ex2) 멀티 스레드로 동작하는 메신저의 경우, 파일을 전송하는 스레드에서 예외가 발생하면 메신저 프로세스 자체가 종료되므로 채팅 스레드도 같이 종료된다( **예외처리 중요 !!** )
