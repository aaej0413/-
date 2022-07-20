# 02_Collection인터페이스
> List와 Set의 조상인 Collection인터페이스에는 다음과 같은 메서드들이 정의되어 있다.
> 

![스크린샷 2022-07-20 오후 12.25.41.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c91d8f86-a643-4bf1-aa98-6bd2613bcb7d/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-07-20_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.25.41.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220720%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220720T032655Z&X-Amz-Expires=86400&X-Amz-Signature=694161a233e39ee91a9ae729f68f1172ff5d2bf5a7e7a25ccc29850b44f9fc30&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-07-20%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252012.25.41.png%22&x-id=GetObject)

***💢 Iterator인터페이스는 컬렉션에 포함된 객체들에 접근할 수 있는 방법을 제공한다.***

- Collection인터페이스는 컬렉션 클래스에 저장된 데이터를 읽고, 추가하고 삭제하는 등 컬레션을 다루는데 가장 기본적인 메서드를 정의하고 있다.
- 반환타입이 boolean인 메서드들은 작업을 성공하거나 사실이면 true를, 그렇지 않으면 false를 반환한다.  
    - 예를들어, “boolean add(Object o)”를 사용해 객체를 컬렉션에 추가할 때, 성공하면 true 실패하면 false를 반환한다.  
    ”boolean is Empty()”를 사용해 컬렉션에 포함된 객체가 없으면 true, 그렇지 않으면 false를 반환한다.  
