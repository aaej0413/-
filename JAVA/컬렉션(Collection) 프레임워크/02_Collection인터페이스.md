# 02_Collection인터페이스
> List와 Set의 조상인 Collection인터페이스에는 다음과 같은 메서드들이 정의되어 있다.
> 
| 메서드 | 설명 |
| --- | --- |
| boolean add(Object o) | 지정된 객체(o) 또는 Collection(c)의 객체들을 Collection에 추가한다. |
boolean addAll(Collection c) 
| void clear() | Collection의 모든 객체를 삭제한다. |
| boolean contains(Object o)
boolean containsAll(Collection c) | 지정된 객체(o) 또는 Collection의 객체들이 Collection에 포함되어 있는지 확인한다. |
| boolean equals(Object o) | 동일한 Collection인지 비교한다. |
| int hashCode() | Collection의 hash code를 반환한다. |
| boolean isEmpty() | Collection이 비어있는지 확인한다. |
| Iterator iterator() | Collection의 iterator을 얻어서 반환한다. |
| boolean remove(Object o) | 지정된 객체를 삭제한다. |
| boolean removeAll(Collection c) | 지정된 Collection에 포함된 객체들을 삭제한다. |
| boolean retainAll(Collection c) | 지정된 Collection에 포함된 객체만을 남기고 다른 객체들은 Collection 에서 삭제한다. 이 작업으로 인해 Collection에 변화가 있으면 true를, 그렇지 않으면 false를 반환한다. 
| int size() | Collection에 저장된 객체의 개수를 반환한다. |
| Object[ ] toArray() | Collection에 저장된 객체를 객체배열(Object[ ])로 반환한다. |
| Object[ ] toArray(Object[ ] a) | 지정된 배열에 Collection의 객체를 저장해서 반환한다. |

***💢 Iterator인터페이스는 컬렉션에 포함된 객체들에 접근할 수 있는 방법을 제공한다.***

- Collection인터페이스는 컬렉션 클래스에 저장된 데이터를 읽고, 추가하고 삭제하는 등 컬레션을 다루는데 가장 기본적인 메서드를 정의하고 있다.
- 반환타입이 boolean인 메서드들은 작업을 성공하거나 사실이면 true를, 그렇지 않으면 false를 반환한다.  
    - 예를들어, “boolean add(Object o)”를 사용해 객체를 컬렉션에 추가할 때, 성공하면 true 실패하면 false를 반환한다.  
    ”boolean is Empty()”를 사용해 컬렉션에 포함된 객체가 없으면 true, 그렇지 않으면 false를 반환한다.  
