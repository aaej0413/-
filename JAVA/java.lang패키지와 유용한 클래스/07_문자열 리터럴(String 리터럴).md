# 07_문자열 리터럴(String 리터럴)
- ""(쌍따옴표) **리터럴**을 이용하면, 기존에 존재하던 것을 재사용 한다.
- 객체에 생성되는 것이 아닌, **Constant String Pool**(상수풀)을 참조한다.


💢 **리터럴** = 데이터(값) 그 자체


### ex)

```java
String s1 = "Cat";
String s2 = "Cat";
```

## String Pool이란?

![https://user-images.githubusercontent.com/45073750/101246499-22c5c180-3757-11eb-938a-61ccca6e0c38.png](https://user-images.githubusercontent.com/45073750/101246499-22c5c180-3757-11eb-938a-61ccca6e0c38.png)

> Java Heap Memory 내에 문자열 리터럴을 저장한 공간.(HashMap으로 구현)
> 
- 한번 생성된 문자열 리터럴은 변경될 수 없다.
- 문자열 리터럴은 클래스가 메모리에 로드될 때 자동적으로 미리 생성된다.
- 리터럴로 문자열을 생성하면(내부적으로 **String.intern()** 호출)
1. String Pool에 같은 값이 있는지 찾는다.
2. 같은 값이 있으면 그 참조값이 반환된다.
3. 같은 값이 없으면 String Pool에 문자열이 등록된 후 해당 참조값이 반환된다.

### 💢 참고

> 원래 이 pool은 heap 영역이 아니라 Perm 영역에 존재했는데,  
> Perm영역은 실행시간(Runtime)에 가변적으로 변경할 수 없는 고정된 사이즈기 때문에 intern메서드 호출 시  
> 저장 공간이 부족하여 OOM(Out Of Memory Exception)이 발생 할 수 있어 변경되었다.
> 

- **Java 6** 이하 : Perm영역(Permanent Generation) - 고정된 사이즈로 **런타임**에 사이즈가 확장되지 않는다.때문에 intern()메소드 호출 시 OOM이 발생할 수 있다.
- **Java 7** 이상 : Heap영역 - String pool의 모든 문자열도 GC의 대상이 된다.hashcode성능이슈 때문에 사이즈(-xx:StringTableSize)는 소수를 사용한다.

참고자료

 - [https://velog.io/@ditt/Java-String-literal-vs-new-String](https://velog.io/@ditt/Java-String-literal-vs-new-String)

 - [https://bepoz-study-diary.tistory.com/272](https://bepoz-study-diary.tistory.com/272)

