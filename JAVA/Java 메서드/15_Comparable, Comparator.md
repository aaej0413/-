# 객체 정렬 시, 사용하는 인터페이스 (Comparable, Comparator)
## 정렬

- 두 대상을 비교하면서 자리 바꿈을 반복하는 것

## 정렬을 하려면?

- (1) 대상, (2) 기준 필요

**두 대상을 비교할 때의 리턴값**

| 양수 (+1) | 0 | 음수 (-1) |
| --- | --- | --- |
| 왼쪽이 큼 | 같음 | 오른쪽이 큼 |

**객체 정렬에 필요한 메서드(정렬 기준)를 정의한 인터페이스**

| 구분 | Comparable | Comparator |
| --- | --- | --- |
| 정렬 기준 | 기본 | 기본 외 다른 기준 |
| 사용 메서드 | compareTo() | compare() |
| 비교 대상 | 자신과 비교 | 두 대상을 비교 |
- Comparable을 구현하여 compareTo() 메소드를 사용하는 것은 단 한번만 가능하다. 그래서 기본으로 설정된 정렬 기준 외 추가로 다른 기준으로 정렬할 때, Comparator를 사용한다.
- 실제 정렬은 Collection.sort(정렬 대상, 정렬 기준) 메소드가 알아서 해준다.
- Comparable 인터페이스를 사용한 경우에는 Collection.sort 메소드 사용 시 정렬 대상만 넣어주면 된다. 이유는 기본 정렬 기준이 디폴트 값으로 설정되어 있기 때문이다.

> **코드 예제** 
[https://www.geeksforgeeks.org/comparable-vs-comparator-in-java/?ref=gcse](https://www.geeksforgeeks.org/comparable-vs-comparator-in-java/?ref=gcse)

**남궁성 선생님 유튜브**
[https://www.youtube.com/watch?v=EW3Mub24wYg](https://www.youtube.com/watch?v=EW3Mub24wYg)
>
