# 1. EJB 란?

- EJB는 *엔터프라이즈급 애플리케이션 개발을 단순화하기 위해 발표한 스펙이다.
    
    **엔터프라이즈급 개발이란?* 
    
    *엔터프라이즈급 개발이란 기업을 대상으로 하는 개발이라는 뜻이다. 
    즉, 대규모 데이터 처리와 트랜잭션이 여러 사용자로 부터 동시에 행해지는 매우 큰 규모의 환경을 엔터프라이즈 환경이라고 한다.* 
    
- Java Bean이라는 자바 객체를 재사용 가능하도록 즉, 컴포넌트화시킬 수 있는 코딩 방침을 정의한 것을 의미한다.
- **Bean**은 쉽게 **component** 또는 **객체**라고 이해할 수 도 있음!

## * JavaBeans(자바 빈즈)

- Java로 작성된 소프트웨어 컴포넌트라고 정의된다.
- JavaBeans는 단순히 Java언어로 작성된 클래스를 의미하는 것이 아니라 어떤 관례에 따라 만들어진 클래스를 의미한다. 관례는 다음과 같다.
    1. 클래스는 직렬화 되어야 한다.
    2. 클래스는 기본 생성자를 가지고 있어야 한다.
    3. 클래스의 속성들은 get, set 혹은 표준 명명법을 따르는 메서드를 사용해 접근할 수 있어야 한다.
    4. 클래스는 필요한 이벤트 처리 메서드를 포함하고 있어야 한다.
    

# 2. EJB 등장 배경

- 기업의 IT 시스템 규모가 점점 커지고 복잡성이 증가하면서 많은 사용자의 요구를 빠르고 안정적으로 처리할 수 있는 다양한 기술(**트랜잭션, 멀티 쓰레딩, 리소스 풀링, 보안 등**)이 필요했다.
- But, 개발자가 비즈니스 로직 뿐만 아니라 다양한 기술🔝을 모두 고려하여 개발하기는 쉽지 않다.
- 그래서 등장한 기술이 바로 EJB!
- EJB는 **구조가 복잡한 대규모 시스템에서 분산 객체 환경을 쉽게 구현하기 위해** 등장했다.
- 즉, 개발을 하다 보면 많은 객체들을 만들게 되는데 이런 비즈니스 객체를 관리하는 컨테이너를 만들어서 필요할 때 마다 객체를 가져다 쓰는 식으로 관리하기 위해 EJB가 탄생했다!

# 3. **EJB의 종류**

## 1. Session Bean

### 1_1. Stateful Session Bean(상태유지 세션 빈)

- 비즈니스 로직을 수행하기 위한 빈으로써 특정 클라이언트의 상태 정보를 빈의 인스턴스가 삭제되기 전까지 유지한다.
- 보통 유지 세션빈은 세션 정보를 유지하거나 장바구니와 같은 기능을 구현할 때 사용한다.

### 1_2. Stateless Session Bean(무상태 세션 빈)

- 비즈니스 로직을 수행하기 위한 빈으로써 특정 클라이언트의 상태를 유지하지 않는 빈이다.
- 일반적으로 무상태 세션 빈은 **JDBC를 이용하여 데이터 베이스를 직접 핸들링** 하는 경우 많이 사용되며,
그 외 공통적인 비즈니스 로직을 처리할 때 사용한다.
- **EJB 애플리케이션에서 전체의 90%이상을 차지**하는 빈이다.

## 2. Entity Bean

- 데이터베이스 테이블과 매핑되어 있는 빈으로써 **엔티티빈은 테이블의 데이터를 개체로 표현한다**.
- 그래서 이 엔티티 빈을 영속성 객체라고 표현한다.
- **이 영속성 객체의 값을 변경하면 이것과 매핑되어 있는 테이블의 값도 변경되기 때문에, 세션빈을 이용하여 JDBC를 처리하는 것 보다 훨씬 쉽게 데이터베이스를 처리할 수 있다.**

## 3. Message-driven Bean

- 비동기 메세지 서비스인 JMS(Java Messagin Service)의 클라이언트로서 비동기 메세지를 수신하여 처리하는 역할을 수행한다.
- 필요에 따라 엔티티 빈이나 다른 세션 빈 또는 JMS 송신지로서의 역할을 수행하기도 한다.
- Message-driven Bean이 없다면 비동기로 메세지를 수신하는 수신자를 EJB컨테이너 상에 위치시켜 처리할 수 없게 된다.
- 트랜잭션으로 비동기 메세지를 수신하여 다른 빈을 호출 할 수 있는 능력을 가지고 있다.

# 4. EJB의 구조

- EJB는 거대 규모의 시스템 구축을 위한 컴포넌트 모델이라고 할 수 있다.
- 컴포넌트 모델이라는 의미는 각각의 S/W를 독립적인 모듈로 제작하여 **재사용성과 호환성을 높이는 것**이다.
- 일반적으로 사용되는 *Java EE의 API로 클라이언트가 볼 수 있는 **화면단은 JSP**가, **비즈니스 로직은 EJB**가 구현하는 구조이다.
    
    ****Java EE** : 엔터프라이즈(기업) 에디션의 자바 플랫폼*
    
- 비즈니스 로직을 구현한 것을 **Enterprise Bean**이라고 하고, 
Database처리, 트랜잭션 처리 같은 시스템 서비스를 구현해 놓은 부분을 **Container**라고 한다.
    
    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/af89c5f8-3ba1-4f74-95dd-dadbe1dee571/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220702%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220702T102413Z&X-Amz-Expires=86400&X-Amz-Signature=611b8a1ca6d5f8787d327bd55609d3deef6c987cadc3c2e15cf4ed72b0a787e4&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
    

# 5. EJB의 장점

EJB의 비전은 “EJB는 애플리케이션 개발을 쉽게 만들어준다. 애플리케이션 개발자는 로우 레벨 기술들에 관심을 가질 필요도 없다” 였다.
즉, 도메인과 비즈니스 로직에만 집중하면 된다는 것이었다.

 EJB컨테이너(WebLogic)로 부터 아래의 항목을 자동으로 지원 받을 수 있으므로 어플리케이션을 신속하게 구축할 수 있다.

1. **인스턴스 폴링**
- 객체를 미리 생성하고 메모리에 저장하여 사용준비 상태에 들어가도록 한다.
- 많은 동시접속자에 대한 안정성 지원 및 확보
1. **트랜잭션**
- 자동으로 컨테이너가 모든 처리메소드에 대하여 트랜잭션을 처리해준다.
- 안정적인 데이터 조작 가능
1.  **퍼시스턴트 관리**
- Beans의 상태를 메모리에서 사용여부에 따라 자동으로 활성화/비활성화를 실행하여 관리해준다.
1.  **FAT Client를 Thin Client로, n-tier시스템을 구축할 수 있다.**  
2. **WebLogic, WebSpace 주로 사용, 국산은 제우스를 사용한다.**  
3. **EJB컴포넌트들이 로딩되어 활동하는 서버쪽 프로그램, 컴포넌트의 생성, 소멸, 라이프 사이클, 보안, 쓰레딩.. 서비스 제공.**

# 6. **EJB의 한계**

- EJB의 다양한 기술들을 사용하기 위해서는 EJB 스펙을 사용해야 했고,
- 로직 보다 EJB 컨테이너 설정을 위해 더 많은 시간을 투자
- 모든 기능이 다 필요하지도 않은 고가의 WAS 구입
- 반복되는 수정-빌드-배포-테스트의 과정
- 컨테이너 안에서만 동작할 수 있는 객체구조
- 형편 없는 개발 생산성
- 불필요한 기술적 복잡도
    - IDE 도움 없이 손대기 어려운 복잡한 설정 파일
- 객체지향적이지 않음!
- 특정 환경에 종속족인 코드로 오히려 개발의 복잡함이 증가.

### 그래서!

마틴 파울러를 비롯한 많은 오피니언 리더들은 EJB와 같은 잘못 설계된 과도한 기술을 피하고,

**객체지향 원리에 따라 만들어진 자바 언어의 기본 기술에 충실하게 비즈니스 로직을 구현**하는

일명 **POJO(Plain Old Java Object) 방식**으로 돌아서야 한다고 지적하고 나섰다.

이렇게 등장한 POJO라는 개념은 **Spring 프레임워크의 기원**이 된다.

## ➕ 막간 상식‼️

### Hibernate

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d39cba60-5e6b-4e6f-b3bc-132883e0c603/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220702%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220702T102429Z&X-Amz-Expires=86400&X-Amz-Signature=12ffcd43c6d3e3de815cd3acc7d51de67d798a18dcac8bb6b9b6cccc59684c8d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

- EJB에는 ORM기술인 엔티티빈 기술을 가지고 있다.
- Spring 컨테이너와 마찬가지로 EJB의 엔티티빈 기술을 후에 Hibernate가 등장하였고, 현재 JPA 표준 인터페이스의 구현체 중 가장 많이 사용되고 있다.
- 하이버네이트 ORM(Hibernate ORM)은 **자바 언어를 위한 객체 관계 매핑 프레임워크**이다.
    - **객체 지향 도메인 모델을 → 관계형 데이터베이스로 매핑하기 위한 프레임워크를 제공**한다.

> 참고 자료
>-[https://yenny-zzang.tistory.com/67](https://yenny-zzang.tistory.com/67)
>- [https://velog.io/@corone_hi/엔터프라이즈-자바빈즈-EJB-Enterprise-Java-Beans](https://velog.io/@corone_hi/%EC%97%94%ED%84%B0%ED%94%84%EB%9D%BC%EC%9D%B4%EC%A6%88-%EC%9E%90%EB%B0%94%EB%B9%88%EC%A6%88-EJB-Enterprise-Java-Beans)
>- [https://velog.io/@mingggkeee/EJBEnterprise-Java-Bean](https://velog.io/@mingggkeee/EJBEnterprise-Java-Bean)
>- [https://www.mindprod.com/jgloss/ejb.html](https://www.mindprod.com/jgloss/ejb.html)
>
