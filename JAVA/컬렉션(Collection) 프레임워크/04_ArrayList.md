# 04_ArrayList
> ArrayList는 컬렉션 프레임워크에서 가장 많이 사용되는 컬렉션 클래스이다.  
ArrayList는 List인터페이스를 구현하기 때문에 **`데이터의 저장순서가 유지`** 되고 **`중복을 허용`** 한다.  
**`ArrayList는 Object 배열을 이용해 데이터를 순차적으로 저장`** 한다.  
예를 들어,  
>1. 첫 번째로 저장한 객체는 Object배열의 0번째 위치에 저장되고,   
>2. 그 다음에 저장하는 객체는 1번째 위치에 저장된다.   
>이런 식으로 계속 배열에 순서대로 저장된다.  
> 

💥 배열에 더이상 저장할 공간이 없으면 보다 큰 새로운 배열을 만들어 기존 배열에 저장된 내용을 새로운 배열로 복사한 다음에 저장한다!

```java
public class ArrayList extends AbstractList
	implements List, RandomAccess, Cloneable, java.io.Serializable {
		...
			transient Object[] elementData;// Object배열
		...
}

// transient는 직렬화(serialization)와 관련된 제어자이다. 
```

## ArrayList의 메서드

| 메서드 | 설명 |
| --- | --- |
| ArrayList( ) | 크기가 0인 ArrayList를 생성 |
| ArrayList(Collection c) | 주어진 컬렉션이 저장된 ArrayList를 생성 |
| ArrayList(int initialCapacity) | 지정된 초기용량을 갖는 ArrayList를 생성 |
| boolean add(Object o) | ArrayList의 마지막에 객체를 추가. 성공하면 true |
| void add(int index, Object element) | 지정된 위치(index)에 객체를 저장 |
| boolean addAll(Collection c) | 지정된 위치(index)에 있는 객체를 삭제하고 삭제된 객체를 반환한다. |
| boolean addAll(int index, Collection c) | 지정된 위치(index)에 객체(element)를 저장한다. |
| void clear( ) | 지정된 비교자(comparator)로 List를 정렬한다. |
| Object clone( ) | 지정된 범위(fromIndex 부터 toIndex)에 있는 객체를 반환한다. |
| boolean contains(Object o) | 지정된 객체 o가 ArrayList에 포함되어 있는지 확인 |
| void ensureCapacity(int minCapacity) | ArrayList의 용량이 최소한 minCapacity가 되도록 한다. |
| Object get(int index) | 지정된 위치(index)에 저장된 객체를 반환한다. |
| int indexOf(Object o) | 지정된 객체가 저장된 위치를 찾아 반환한다. |
| boolean isEmpty( ) | ArrayList가 비어있는지 확인한다. |
| Iterator iterator( ) | ArrayList의 Iterator객체를 반환 |
| int lastIndexOf(Object o) | 객체o가 저장돤 위치를 끝부터 역방향으로 검색해서 반환 |
| ListIterator listItrator( ) | ArrayList의 ListIterator를 반환 |
| ListIterator listIterator(int index) | ArrayList의 지정된 위치부터 시작하는 ListIterator를 반환 |
| Object remove(int index) | 지정된 위치 index에 있는 객체를 제거한다. |
| boolean remove(Object o) | 지정한 객체를 제거한다.(성공하면 true, 실패하면 false) |
| boolean removeAll(Collection c) | 지정한 컬렉션에 저장된 것과 동일한 객체들을 ArrayList에서 제거한다. |
| boolean retainAll(Collection c) | ArrayList에 저장된 객체 중에서 주어진 컬렉션과 공통된 것들만을 남기고 나머지는 삭제한다. |
| Object set(int index, Object element) | 주어진 객체 element를 지정된 위치 index에 저장한다. |
| int size( ) | ArrayList에 저장된 객체의 개수를 반환한다. |
| void sort(Comparator c) | 지정된 정렬기준 c로 ArrayList를 정렬 |
| List subList(int fromIndex, int toIndex) | fromIndex부터 toIndex사이에 저장된 객체를 반환한다. |
| Object[ ] toArray( ) | ArrayList에 저장된 모든 객체들을 객체배열로 반환한다. |
| Object[ ] toArray(Objct[ ] a)  | ArrayList에 저장된 객체들을 객체배열 a에 담아서 반환한다. |
| void trimToSize( ) | 용량을 크기에 맞게 줄인다.(빈 공간을 없앰!) |

### ArrayList예제

```java
package collectionframework;

import java.util.*;

public class Ex11_1 {
    public static void main(String[] args) {

        ArrayList list1 = new ArrayList(10);
        list1.add(new Integer(5));
        list1.add(new Integer(4));
        list1.add(new Integer(2));
        list1.add(new Integer(0));
        list1.add(new Integer(1));
        list1.add(new Integer(3));

        ArrayList list2 = new ArrayList(list1.subList(1, 4));
        print(list1,list2);

        Collections.sort(list1);    // 오름차순 정렬.
        Collections.sort(list2);
        print(list1,list2);

        System.out.println("list1.containsAll(list2): " + list1.containsAll(list2));

        list2.add("B");
        list2.add("C");
        list2.add(3, "A");  // 인덱스가 3인 곳에 "A"를 추가.
        print(list1,list2);

        list2.set(3, "AA"); // 인덱스가 3인 곳을 "AA"로 변경.
        print(list1,list2);

        System.out.println("list1.retainAll(list2) : " + list1.retainAll(list2));
        // list1에서 list2와 겹치는 부분만 남기고 나머지는 삭제한다.

        print(list1,list2);

        for (int i = list2.size() - 1; i >= 0; i--) {
            if (list1.contains(list2.get(i))) {
                list2.remove(i);
            }
            print(list1,list2);
            // main의 끝
        }
    }
    static void print(ArrayList list1, ArrayList list2){
        System.out.println("list1 : " + list1);
        System.out.println("list2 : " + list2);
        System.out.println();

    }
}
```

### 결과

```java
list1 : [5, 4, 2, 0, 1, 3]
list2 : [4, 2, 0]

list1 : [0, 1, 2, 3, 4, 5]
list2 : [0, 2, 4]

list1.containsAll(list2): true  <- list1이 list2의 모든 요소를 포함하고 있을 때만 true.
list1 : [0, 1, 2, 3, 4, 5]
list2 : [0, 2, 4, A, B, C]  <- add(Object obj)를 이용해 새로운 개겣 저장.

list1 : [0, 1, 2, 3, 4, 5]
list2 : [0, 2, 4, AA, B, C]  <- set(int index, Object obj)를 이용해 다른 객체로 변경.

list1.retainAll(list2) : true  <- retainAll에 의해 list1에 변화가 있었으므로 true.
list1 : [0, 2, 4]  <- list2와의 공통요소 이외에는 모두 삭제됨(변화 O)
list2 : [0, 2, 4, AA, B, C]  

list1 : [0, 2, 4]
list2 : [AA, B, C]
```
