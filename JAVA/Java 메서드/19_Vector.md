# Vector

- Vector는 ArrayList와 동일한 내부구조를 가지고 있다.
- ArrayList와 마찬가지로 Vector내부에 값이 추가되면 자동으로 **크기가 조절**되며 그다음 객체들은 한 자리씩 뒤로 이동된다.
- 하지만 Vector와 Arraylist의 한가지 다른 점이 있는데 **Vector는 동기화된 메소드로 구성**되어 있기 때문에 멀티 **스레드가 동시에 이 메소드들을 실행할 수 없고**, 하나의 스레드가 실행을 완료해야만 다른 스레드들이 실행할 수 있다.
- 그래서 **멀티 스레드 환경에서 안전하게 객체를 추가하고 삭제**할 수 있다.
- Vector는 **항상 동기화**되는 장점이자 단점을 가지고 있다.
- 스레드가 1개일때도 동기화를 하기 때문에 ArrayList보다 성능이 떨어진다.
- Arraylist는 기본적인 기능은 Vector와 동일하나 자동 동기화 기능이 빠져있고, 동기화 옵션이 존재한다. 그리고 Vector에 비해 속도가 더 빠르기 때문에 Vector에 비해 많이 쓰이고 있다.

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8482aac8-6989-426d-bcd1-4dae3b21feda/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220702%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220702T075627Z&X-Amz-Expires=86400&X-Amz-Signature=ddc42d14ccf23f36a594c30432581d1dc25ad681592e00f3e3bce635210a4797&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

# Vector 생성

```java
Vector<E> v = new Vector<E>();
```

- Vector<E>의 E에 요소로 사용할 객체형 타입을 지정해야 한다. (기본형 타입 사용 불가)
- Vector 선언시 타입을 지정하지 않고 임의의 타입의 값을 넣고 사용할 수도 있지만 이렇게 사용할 경우 벡터 내부의 값을 사용하려면 캐스팅(Casting) 연산이 필요하며 잘못된 타입으로 캐스팅을 한 경우에는 에러가 발생하기에 처음부터 타입을 명시해주는 것이 좋다.
- Vector<Integer> v = new Vector<Integer>();이라고 되어있다면 int객체들만 add되어질 수 있고 다른 타입의 객체는 사용이 불가능하다.

```java
Vector v = new Vector();//타입 미설정 Object로 선언된다.
Vector<Student> student = new Vector<Student>(); //타입설정 Student객체만 사용가능
Vector<Integer> num2 = new Vector<Integer>(); //타입설정 int타입만 사용가능
Vector<Integer> num3 = new Vector<>(); //new에서 타입 파라미터 생략가능
Vector<String> v2 = new Vector<String>(10);//초기 용량(capacity)지정
Vector<Integer> v3 = new Vector<Integer>(Arrays.asList(1,2,3)); //초기값 지정
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f918e9d2-163d-4d29-b583-0abb7bb5c4ab/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220702%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220702T075645Z&X-Amz-Expires=86400&X-Amz-Signature=e708c2bd6d864ba7e48663242eb8b33b0749a7e18efee31dff083d73a6bd1c99&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

# Vector 값 추가

```java
Vector<Integer> v = new Vector<Integer>();
v.add(3); //값 추가
v.add(null); //null값도 add가능
v.add(1,10); //index 1뒤에 10 삽입
```

```java
Vector v = new Vector();
Student student = new Student(name,age);
v.add(student);
v.add(new Member("홍길동",15));
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a591e664-043d-41b1-8335-dbfd79446412/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220702%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220702T075701Z&X-Amz-Expires=86400&X-Amz-Signature=8c991f9755f8f29db68a60051e73b2a1cb7384c8c8b9404bde25a85223d637d3&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

- Vector에 값을 추가하려면 Vector의 **add(index, value) 메소드**를 사용하면 된다. 구조는 ArrayList나 LinkedList와 같다.
- index를 생략하면 Vector의 맨 뒤에 값이 추가되며 index 중간에 값을 추가하면 해당 인덱스부터 마지막 인덱스까지 모두 한 칸씩 뒤로 밀려난다.

# Vector 값 삭제

```java
Vector<Integer> v = new Vector<Integer>(Arrays.asList(1,2,3));
v.remove(1);  //index 1 제거
v.removeAllElements(); //모든 값 제거
v.clear();  //모든 값 제거
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e2b607c0-093b-45e7-befb-70d54cb06dcc/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220702%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220702T075727Z&X-Amz-Expires=86400&X-Amz-Signature=ad503f7b3b8defdf2f0e6fee7223203298f15fd0ba2876d003a2335088ed2fbc&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

- Vector에서 값을 삭제 하려면 Vector의 **remove(index) 메소드**를 사용하면 된다.
- remove() 함수를 사용하여 특정 인덱스의 값을 제거하면 바로 뒤에 있는 인덱스부터 마지막 인덱스까지 모두 앞으로 한 칸씩 앞으로 당겨진다.
- **모든 값을 제거**하려면 **clear() 메소드**나 **removeAllElements() 메소드**를 사용하면 된다.

# Vector 크기 구하기

```java
Vector<Integer> v = new Vector<Integer>(10);//초기용량 10
v.add(1); //값 추가
System.out.println(v.size()); //Vector 자료 개수 : 1
System.out.println(v.capacity()); //Vector 물리적크기 : 10
```

- Vector의 **값이 들어있는 개수를 구하려면 size() 메소드**를 사용하면 되고, **물리적 크기를 알고 싶다면 capacity() 메소드**를 사용하면 된다.

# Vector 값 출력

```java
Vector<Integer> list = new Vector<Integer>(Arrays.asList(1,2,3));

System.out.println(list.get(0));//0번째 index 출력
				
for(Integer i : list) { //for문을 통한 전체출력
    System.out.println(i);
}

Iterator iter = list.iterator(); //Iterator 선언 
while(iter.hasNext()){//다음값이 있는지 체크
    System.out.println(iter.next()); //값 출력
}
```

- Vector에서 값을 출력하는 방법은 ArrayList와 동일하다. **get(index) 메소드**를 사용하면 Vector의 원하는 index의 값이 리턴 된다.
- **전체 출력**은 대부분 **for문**을 통해서 출력을 하고 **Iterator**를 사용해서 출력을 할 수도 있다.

> [출처1](https://coding-factory.tistory.com/553), [출처2](https://blog.naver.com/PostView.nhn?blogId=ihp0001&logNo=221471470332&categoryNo=11&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=search)
>
