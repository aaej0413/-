# 문자열 길이
> 1. length
> 
- arryays (int[], double[], String[])
- length는 **배열의 길이**를 알고자 할 때 사용된다.

```java
int[] array01 = new int[12];
System.out.println(array01.length);   //12
```

> 2. length()
> 
- String related Object(String, StringBuilder etc)
- length()는 **문자열의 길이**를 알고자 할때 사용된다.

```java
String test = "test";
System.out.println(test.lenth());    //4
```

> 3. size()
> 
- Collection Object(ArrayList, Set etc)
- size()는 **컬렉션 프레임워크 타입의 길이**를 알고자 할때 사용된다.

```java
ArrayList<Object> test = new ArrayList<Object>();
System.out.println(test.size());   //0
```

**응용 예**

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public int[] solution(int[] arr, int divisor) {
        List<Integer> list = new ArrayList<>();

        for(int n : arr) {
            if(n % divisor == 0) {
                list.add(n);
            }
        }
        if (list.size()==0){
            list.add(-1);
        }
        int[] result = new int[list.size()];
        for(int i = 0; i < list.size(); i++){
            result[i] += list.get(i);
        }
        Arrays.sort(result);
        return result;
    }
```

