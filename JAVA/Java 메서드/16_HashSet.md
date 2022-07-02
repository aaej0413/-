# HashSet 은 Set 인터페이스의 구현 클래스

> **Set 특징**
> 
- Set은 **객체를 중복해서 저장할 수 없고** 하나의 null 값만 저장할 수 있음.
- 저장 순서가 유지되지 않음. (저장 순서를 유지해야 한다면 LinkedHashSet 클래스를 사용)
- Set 인터페이스를 구현한 클래스 중 아래 두가지를 제일 많이 사용함.
    - HashSet → 정렬 X
    - TreeSet → 자동 정렬
- Set의 가장 큰 장점은 중복을 자동으로 제거해준다는 점

> ****HashSet 생성****
> 
- HashSet을 기본 생성했을 때는 initial capacity(16), load factor(0.75)의 값을 가진 HashSet 객체가 생성됨.
- Set은 한 칸씩 저장공간을 늘리지 않고 저장용량을 약 두 배로 늘리기 때문에 과부하가 발생할 수 있음. 그렇기에 초기에 저장할 데이터 개수를 알고 있다면 Set의 초기용량을 지정해주는 것이 좋음.

```java
HashSet<Integer> set1 = new HashSet<Integer>();//HashSet생성
HashSet<Integer> set2 = new HashSet<>();//new에서 타입 파라미터 생략가능
HashSet<Integer> set3 = new HashSet<Integer>(set1);//set1의 모든 값을 가진 HashSet생성
HashSet<Integer> set4 = new HashSet<Integer>(10);//초기 용량(capacity)지정
HashSet<Integer> set5 = new HashSet<Integer>(10, 0.7f);//초기 capacity,load factor지정
HashSet<Integer> set6 = new HashSet<Integer>(Arrays.asList(1,2,3));//초기값 지정
```

> ****HashSet 값 추가****
> 
- **add(value) 메소드 사용**
- 입력되는 값이 HashSet 내부에 존재하지 않는다면 그 값을 HashSet에 추가하고 true를 반환하고 내부에 값이 존재한다면 false를 반환함.

```java
HashSet<Integer> set = new HashSet<Integer>();//HashSet생성
set.add(1); //값 추가
set.add(2);
set.add(3);
```

> **HashSet 값 삭제**
> 
- **remove(value) 메소드 사용**
- 매개변수 value의 값이 HashSet 내부에 존재한다면 그 값을 삭제한 후 true를 반환하고 없다면 false를 반환함.
- 모든 값을 제거하려면 clear() 메소드를 사용

```java
HashSet<Integer> set = new HashSet<Integer>(Arrays.asList(1,2,3));//HashSet생성
set.remove(1);//값 1 제거
set.clear();//모든 값 제거
```

> **HashSet 크기 구하기**
> 
- **size() 메소드를 사용**

```java
HashSet<Integer> set = new HashSet<Integer>(Arrays.asList(1,2,3));//HashSet생성
System.out.println(set.size());//set 크기 : 3
```

> **HashSet 값 출력**
> 
- Set컬렉션을 그냥 print하게 되면 대괄호 [ ]로 묶여서 set의 전체 값이 출력됨.
- Set에는 인덱스로 객체를 가져오는 get(index) 메소드가 없음.
- 대신 전체 객체를 대상으로 한 번씩 반복해서 가져오는 Iterator 인터페이스의 iterator() 메소드를 사용하면 됨.
- Iterator에서 하나의 객체를 가져올 때는 next() 메소드를 사용함.
- next() 메소드를 사용하기 전에 hasNext() 메소드를 사용하는 것이 좋음.
- hasNext() 메소드는 가져올 객체가 있으면 true를 리턴하고 없으면 false를 리턴함.

```java
HashSet<Integer> set = new HashSet<Integer>(Arrays.asList(1,2,3));//HashSet생성

System.out.println(set); //전체출력 [1,2,3]
		
Iterator iter = set.iterator();	// Iterator 사용
while(iter.hasNext()) {//값이 있으면 true 없으면 false
    System.out.println(iter.next());
}
```

> **HashSet 값 검색**
> 
- **contains(value) 메소드를 사용**
- 파라미터로 주어진 객체가 HashSet이 가지고 있다면 true, 아니면 false를 반환함.

```java
HashSet<Integer> set = new HashSet<Integer>(Arrays.asList(1,2,3));//HashSet생성
System.out.println(set.contains(1)); //set내부에 값 1이 있는지 check : true
```

<aside>
💡 참고 사이트
[https://coding-factory.tistory.com/554#recentComments](https://coding-factory.tistory.com/554#recentComments)

</aside>
