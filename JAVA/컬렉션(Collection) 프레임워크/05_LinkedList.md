# 05_LinkedList
### 배열의 장점

1. 배열은 가장 기본적인 형태의 자료구조로 구조가 간단하며 사용하기 쉽다.
2. 데이터를 읽어오는데 걸리는 시간(접근시간, access time)이 가장 빠르다.

### 배열의 단점

1. **크기를 변경할 수 없다.**
    - 크기를 변경할 수 없으므로 새로운 배열을 생성해서 테이터를 복사해야한다.
    - 실행속도를 향상시키기 위해서는 충분히 큰 크기의 배열을 생성해야 하므로 메모리가 낭비된다.
2. **비순차적인 데이터의 추가 또는 삭제에 시간이 많이 걸린다.**
    - 차례대로 데이터를 추가하고 마지막에서부터 데이터를 삭제하는 것은 빠르지만,
    - 배열의 중간에 데이터를 추가하려면, 빈자리를 만들기 위해 다른 데이터들을 복사해서 이동해야 한다.

> 💥 이러한 **`배열의 단점을 보완`** 하기 위해 **`링크드 리스트(linked list)`** 라는 자료구조가 고안되었다.
배열은 모든 데이터가 연속적으로 존재하지만 링크드 리스트는 **`불연속적으로 존재하는 데이터를 서로 연결`**(link)한 형태로 구성되어 있다.
> 

                                                                                                                                                                            

![스크린샷 2022-08-03 오후 2.57.50.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b4d02a2f-e88d-4a77-b841-682b4523e92e/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-08-03_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2.57.50.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220803%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220803T065838Z&X-Amz-Expires=86400&X-Amz-Signature=ec65a3e55be07df49ff1e11e9419734b0baf63170e7e4598faa84e0bb53537f3&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-08-03%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25202.57.50.png%22&x-id=GetObject)

👉🏻 링크드 리스트의 각 요소(node)들은 자신과 연결된 ***다음 요소에 대한 참조(주소값)***와 ***데이터로 구성***되어 있다.

```java
Class Node {
		Node next;  // 다음 요소의 주소를 저장.
		Object obj; // 데이터를 저장.
```

## LinkedList의 추가와 삭제

- 링크드 리스트에서의 데이터 삭제는 간단하다.
- 삭제하고자 하는 요소의 이전요소가, 삭제하고자 하는 다음 요소를 참조하도록 변경하면 된다.
- 단 하나의 참조만 변경하면 삭제가 이루어진다.
- 배열처럼 데이터를 이동하기 위해 복사하는 과정이 없기 떄문에 처리속도가 매우 빠르다.

![스크린샷 2022-08-03 오후 3.24.51.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/02ab8ba6-6586-4619-8e50-9a9b2ea2ad09/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-08-03_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_3.24.51.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220803%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220803T065859Z&X-Amz-Expires=86400&X-Amz-Signature=eb8d88de90e6ac5a2c3e003fd40c2eb68a4942112aaace7624311b175b16b0c2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-08-03%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25203.24.51.png%22&x-id=GetObject)

- 새로운 데이터를 추가할 때는 새로운 요소를 생성한 다음
- 추가하고자 하는 위치의 이전 요소의 참조를 새로운 요소에 대한 참조로 변경해주고,
- 새로운 요소가 그 다음 요소를 참조하도록 변경하기만 하면 되므로 처리속도가 매우 빠르다.

![스크린샷 2022-08-03 오후 3.29.58.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/127cf47f-eb4a-4d7e-b142-1022f579bb62/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-08-03_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_3.29.58.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220803%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220803T065910Z&X-Amz-Expires=86400&X-Amz-Signature=c62524c3239eb364ef081f40880182af6645839a7d9cd004e0e68d405654973a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-08-03%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25203.29.58.png%22&x-id=GetObject)

## ArrayList와 LinkedList의 비교

- 배열은 각 요소들이 연속적으로 메모리상에 존재하기 때문에 간단한 계산만으로 원하는 요소의 주소를 얻어서 저장된 데이터를 곧바로 읽어올 수 있다.
- LinkedList는 불연속적으로 위치한 각 요소들이 서로 연결된 것이라 처음부터 n번째 데이터까지 차례대로 따라가야만 원하는 값을 얻을 수 있다.
- 그래서 LinkedList는 저장해야하는 데이터 개수가 많아질수록 데이터를 읽어 오는 시간, 
즉 접근시간(acces time)이 길어진다.

![스크린샷 2022-08-03 오후 3.57.07.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ea95df94-9b76-42db-b79c-277c64c4127b/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-08-03_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_3.57.07.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220803%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220803T065927Z&X-Amz-Expires=86400&X-Amz-Signature=45c34268da67bf4e291adf9ab90d431bb8d91ef83e80cf4276c20f8135afbbe5&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-08-03%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25203.57.07.png%22&x-id=GetObject)
