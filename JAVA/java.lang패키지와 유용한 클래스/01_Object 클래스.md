# 01_Object 클래스
> java.lang 패키지는 **자바프로그래밍에 가장 기본이 되는 클래스들을 포함**하고 있다.
그렇기 때문에 j**ava.lang패키지의 클래스들**은 **import문 없이도 사용**할 수 있게 됐다.
> 

> 그 동안 **String클래스**나 **System클래스**를 **import문 없이 사용할 수 있었던 이유**가 바로 **java.lang 패키지에 속한 클래스들**이기 때문이었다.
> 

# Object클래스

- Object클래스는 모든 클래스의 최고 조상이기 때문에 Object클래스의 멤버들은 모든 클래스에서 바로 사용 가능하다.

![스크린샷 2022-07-08 오후 11.02.30.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f6e89f85-a452-48a6-9a42-9facdc2592fb/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-07-08_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_11.02.30.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220708%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220708T140319Z&X-Amz-Expires=86400&X-Amz-Signature=a44137aeec9a75a4ffcaf3581464478e4948654425686afd7afb29763cbca09b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-07-08%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252011.02.30.png%22&x-id=GetObject)

- Object클래스는 멤버변수는 없고 오직 11개의 메서드만 가지고 있다.
- 이 메서드들은 모든 인스턴스가 가져야 할 기본적인 것들이다.
