# Stack

- 뒤에서 부터 꺼내기
- **LIFO = Last In First Out**
- “가장 나중에 들어간 값이 가장 먼저 나온다”
- 스택은 저금통처럼 양 옆과 바닥이 막혀 있어서 위로만 뺄수 있는 구조!!

![스크린샷 2022-06-14 오후 4.52.57.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f81ddcc1-c6c4-414f-aff9-ae919615c79f/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-06-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_4.52.57.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220830%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220830T095010Z&X-Amz-Expires=86400&X-Amz-Signature=a8d1bbe6bea5fbaa4f38f34622baae4fc3787edbb8967f76f4ddd18805fbfa4d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-06-14%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25204.52.57.png%22&x-id=GetObject)

- `boolean empty()` - Stack이 비어있는지 알려준다.
- `Object push(Object item)` - Stack에 객체(item)을 저장한다.
- `Object pop()` - Stack의 맨 위에 저장된 객체를 꺼낸다. (비었을 때는 EmptyStackException발생)
- `Object peek()` - Stack의 맨 위에 저장된 객체를 반환. pop()과 달리 Stack에서 객체를 꺼내지는 않음. (비었을 때는 EmptyStackException 발생)
- `int search(Object o)` - Stack에서 주어진 객체(o)를 찾아서 그 위치를 반환. *못찾으면 -1을 반환.*
(배열과 달리 위치는 0이 아닌 1부터 시작. 맨 위의 요소가 1)

**List로 스택 구현하기**

```java
public class Solution {
    public static void main(String[] args) {
        List<Integer> list = new LinkedList<>();

        list.add(1); // 제일 먼저 넣은 값임.
        list.add(2);
        list.add(3);
        list.add(4);
        list.add(5);

        System.out.println(list);

        System.out.println(list.remove(list.size()-1));
        System.out.println(list);

        System.out.println(list.remove(list.size()-1));
        System.out.println(list);

    }
}
				//출력 값
				[1, 2, 3, 4, 5]
				 5                 //제일 마지막에 넣은 값이 제일 처음으로 나옴.
				[1, 2, 3, 4]
				 4
				[1, 2, 3]
```

**자바가 제공해주는 Stack 사용**

```java
public class Solution {
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();

        stack.push(1);
        stack.push(2);
        stack.push(3);
        stack.push(4);
        stack.push(5);  // 가장 나중에 넣은 값

        System.out.println(stack);

        stack.pop();
        System.out.println(stack);
        stack.pop();
        System.out.println(stack);
        stack.pop();
        System.out.println(stack);

    }
}
				// 출력 값
				[1, 2, 3, 4, 5]
				[1, 2, 3, 4]
				[1, 2, 3]
				[1, 2]
```

# Queue

- 앞에서 부터 꺼내기
- **FIFO = First In First Out**
- “제일 먼저 들어간 데이터가 제일 먼저 나온다”
- 큐는 양 옆만 막혀있고 위아래로 뚫려 있어서 위로는 넣고 밑으로는 뺄 수 있는 파이프와 같은 구조!!

![스크린샷 2022-06-14 오후 3.22.17.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4dbb90b2-964f-4705-a9a1-8c82d289c7e6/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-06-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_3.22.17.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220830%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220830T095056Z&X-Amz-Expires=86400&X-Amz-Signature=8ae7388361b75529f3c3ebf1b4af5dae50b0fc5627c4e83818ffbd1fefcf8bd5&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-06-14%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25203.22.17.png%22&x-id=GetObject)

- `boolean add(Object o)` - 지정된 객체를 Queue에 추가한다. 성공하면 true를 반환. 저장공간이 부족하면 illegalStateException발생.
- `Object remove()`  - Queue에서 객체를 꺼내 반환. 비어있으면 NoSuchElementExceiption발생.
- `Object element()` - 삭제없이 요소를 읽어옴. peek와 달리 Queue가 비어있을  때 NoSuchElementExceiption발생.
- `boolean offer(Object o)` - Queue에 객체를 저장. 성공하면 true, 실패하면 false를 반환.
- `Object poll()` - Queue에서 객체를 꺼내서 반환. 비어있으면 null을 반환.
- `Object peek()` - 삭제없이 요소를 읽어옴. Queue가 비어있으면 null을 반환.

**List로 큐 구현하기**

```java
public class Solution {
    public static void main(String[] args) {
        List<Integer> list = new LinkedList<>();

        list.add(1); // 제일 먼저 넣은 값임.
        list.add(2);
        list.add(3);
        list.add(4);
        list.add(5);

        System.out.println(list);

        System.out.println(list.remove(0));
        System.out.println(list);

        System.out.println(list.remove(0));
        System.out.println(list);

    }
}
				//출력 값
				[1, 2, 3, 4, 5]
				 1                  //제일 먼저 넣은 1이 제일 먼저 나왔음.
				[2, 3, 4, 5]
				 2
				[3, 4, 5]
```

**자바가 제공해주는 Queue 사용.**

```java
public class Solution {
    public static void main(String[] args) {
        Queue<Integer> queue = new LinkedList<>();

        queue.offer(1); // 제일 먼저 넣은 값.
        queue.offer(2);
        queue.offer(3);
        queue.offer(4);
        queue.offer(5);

        System.out.println(queue);
        queue.poll();
        System.out.println(queue);
        queue.poll();
        System.out.println(queue);
        queue.poll();
        System.out.println(queue);

    }
}
				//출력 값
				[1, 2, 3, 4, 5]
				[2, 3, 4, 5]
				[3, 4, 5]
				[4,5]
```

## 💥 Stack과 Queue예제

```java
public class Ex11_2 {
    public static void main(String[] args) {
        Stack st = new Stack<>();
        Queue q = new LinkedList(); // Queue인터페이스의 구현체인 LinkedList를 사용.

        st.push("0");
        st.push("1");
        st.push("2");

        q.offer("0");
        q.offer("1");
        q.offer("2");

        System.out.println("====Stack=====");
        while (!st.empty()) {
            System.out.println(st.pop());   // 스택에서 요소 하나를 꺼내서 출력
        }

        System.out.println("====Queue====");
        while (!q.isEmpty()) {
            System.out.println(q.poll());   // 큐에서 요소 하나를 꺼내서 출력

        }
    }
}

결과
====Stack=====
2
1
0
====Queue====
0
1
2
```

👉🏻 *자바에서는 Stack을 클래스로 구현하여 제공하지만, Queue는 인터페이스로만 정의해 놓았을 뿐 별도의 클래스를 제공하고 있지 않다. 대신 Queue인터페이스를 구현한 클래스들이 있어서 이들 중 하나를 선택해서 사용하면 된다.*

# ⚡️ Stack과 Queue의 활용

1. **스택의 활용 예 -** 수식계산, 수식 괄호검사, 워드프로세서의 undo/redo, 웹브라우저의 뒤로/앞으로.
2. **큐의 활용 예 -** 최근 사용 문서, 인쇄작업 대기목록, 버퍼(buffer)

**Stack과 Queue의 활용 예제_01**

```java

```

**Stack과 Queue의 활용 예제_02**

```java

```

# 양쪽으로 꺼내고 뺄 수 있는 건 없어? 있지!! Deque!!

![스크린샷 2022-06-14 오후 5.02.39.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d8de7657-2cc3-474e-9230-92c7b4a988d2/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-06-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_5.02.39.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220830%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220830T095130Z&X-Amz-Expires=86400&X-Amz-Signature=82c1878206bc8ac91e823c3ed4586acfd887731b971510c460aea3d1305a7310&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-06-14%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25205.02.39.png%22&x-id=GetObject)

- 앞에 데이터를 넣고 싶으면 `offerFirst()`.
- 뒤에 데이터를 넣고 싶으면 `offerLast()`.
- 앞에 값을 꺼내고 싶으면 `pollFirst()`.
- 뒤에 값을 꺼내고 싶으면 `pollLast()`.
- 앞에서 꺼낼 차례의 값을 확인하고 싶으면 `peekFirst()`.
- 뒤에서 꺼낼 차례의 값을 확인하고 싶으면 `peekLast()`.

```java
public class Solution {
    public static void main(String[] args) {
        Deque<Integer> deque = new LinkedList<>();

        deque.offerFirst(1);
        System.out.println(deque);

        deque.offerLast(2);
        System.out.println(deque);

        deque.offerFirst(3);
        System.out.println(deque);

        deque.offerLast(4);
        System.out.println(deque);

				deque.peekFirst();
        System.out.println(deque);
        deque.peekFirst();
        System.out.println(deque);

    }
}
				// 출력 값
				[1]
				[1, 2]
				[3, 1, 2]
				[3, 1, 2, 4]
				[1,2,4]
				[2,4]
```

### 중간에 있는 값을 꺼내고 확인하고 싶을 때는 Stack, Queue, Deque 는 어울리지 않음!!! ❌❌

