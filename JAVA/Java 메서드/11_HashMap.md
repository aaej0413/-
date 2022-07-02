# HashMap은 Map인터페이스에 속해있는 Collection


> **HashMap 선언**
> 
- Map은 **키와 값**으로 구성된 Entry객체를 저장하는 구조를 가지고 있는 자료구조.
- 여기서 키와 값은 모두 객체.
- 값은 중복 저장될 수 있지만 **키는 중복 저장될 수 없음.**
- 기존에 저장된 키와 동일한 키로 값을 저장하면 기존의 값은 없어지고 새로운 값으로 대치.
- HashMap은 이름 그대로 해싱(Hashing)을 사용하기 때문에 많은 양의 데이터를 검색하는데
뛰어난 성능을 보임.
- 데이터의 순서를 보장하지 않음.

```java
HashMap<String,String> map1 = new HashMap<String,String>();//HashMap생성

HashMap<String,String> map2 = new HashMap<>();//new에서 타입 파라미터 생략가능

HashMap<String,String> map3 = new HashMap<>(map1);//map1의 모든 값을 가진 HashMap생성

HashMap<String,String> map4 = new HashMap<>(10);//초기 용량(capacity)지정

HashMap<String,String> map5 = new HashMap<>(10, 0.7f);//초기 capacity,load factor지정

HashMap<String,String> map6 = new HashMap<String,String>(){{//초기값 지정
    put("a","b");
}};
```

> **HashMap 값 추가**
> 
- **put( key, value)** 메소드를 사용.
- 선언 시 HashMap에 설정해준 타입과 같은 타입의 Key 와 Value값을 넣어야 함.
- 기존 키 캆과 입력한 키 값이 값으면 기존 값은 새로 입력되는 값으로 대치

```java
HashMap<Integer,String> map = new HashMap<>();//new에서 타입 파라미터 생략가능

map.put(1,"사과"); //값 추가
map.put(2,"바나나");
map.put(3,"포도");
```

> **HashMap 값 삭제**
> 
- **remove(key) 메소드를 사용.**
- “오직 키 값”으로만 Map의 요소를 삭제할 수 있음.
- 모든 값을 제거하려먼 clear()메소드 사용.

```java
HashMap<Integer,String> map = new HashMap<Integer,String>(){{//초기값 지정

    put(1,"사과");
    put(2,"바나나");
    put(3,"포도");
}};

map.remove(1); //key값 1 제거
map.clear(); //모든 값 제거
```

> **HashMap 값 출력**
> 

1. **System.out.print 사용.**
- Map의 전체 key값, value가 출력.
- 특정 key값의 value를 가져오고 싶다면 get(key)를 사용

```java
HashMap<Integer,String> map = new HashMap<Integer,String>(){{//초기값 지정

    put(1,"사과");
    put(2,"바나나");
    put(3,"포도");
}};
		
System.out.println(map); //전체 출력 : {1=사과, 2=바나나, 3=포도}
System.out.println(map.get(1));//key값 1의 value얻기 : 사과
```

<aside>
💡 전체를 출력하려면 entrySet()이나 keySet() 메소드를 활용하여 Map의 객체를 반환받은 후 출력하면 됩니다.

</aside>

1. **entrySet() 사용.**
- **getKey()** 메소드와 **getValue()**메소드로 각각 키와 값을 가져올 수 있음.

```java
HashMap<Integer,String> map = new HashMap<Integer,String>(){{//초기값 지정

    put(1,"사과");
    put(2,"바나나");
    put(3,"포도");
}};

		for (Entry<Integer, String> entry : map.entrySet()) {
			System.out.println("[Key]:" + entry.getKey()+ "[Value]:" + entry.getValue());

// [Key]:1 [Value]:사과
// [Key]:2 [Value]:바나나
// [Key]:3 [Value]:포도
```

1. **KeySet() 사용.**
- key 값만 필요할 경우 사용.
- get(key)를 받아서 value를 출력할 수 있음. ⇒ (key)의 값을 가져와라.

```java
HashMap<Integer,String> map = new HashMap<Integer,String>(){{//초기값 지정
    put(1,"사과");
    put(2,"바나나");
    put(3,"포도");
}};
		
//KeySet() 활용
		for(Integer i : map.keySet()){ //저장된 key값 확인
	    System.out.println("[Key]:" + i + " [Value]:" + map.get(i));
}
//[Key]:1 [Value]:사과
//[Key]:2 [Value]:바나나
//[Key]:3 [Value]:포도
```

<aside>
💡 KeySet을 이용해서 순회할 때, get()메소드로 다시 해시테이블을 조회하는 것은 오버헤드이다.
만약 전체 HashMap 데이터를 순회해야한다면, 
KeySet 대신 처음부터 EntrySet을 가져와서 사용해야 get()메소드의 호출 오버헤드를 줄일 수 있다.

</aside>

- **그 외 함수들**
    - putAll()
    - isEmpty()
    - values()
    - containsKey()
    - containsValue()
    - replace()
    

 **[💥활용 문제](https://www.notion.so/22-05-14-713a3a81ff754a7ab2def08e1ba83f80)**
