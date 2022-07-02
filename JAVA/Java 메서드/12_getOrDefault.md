# 찾는 키가 존재한다면 찾는 키의 값을 반환하고,없다면 기본 값을 반환하는 메서드.
[키:값] [키:값] [키:값] [키:값] [키:값] [키:값] [키:값] **앞에가 키 뒤에가 값** [키:값] [키:값] [키:값] [키:값] [키:값]

> **getOrDefault ( key, DefaultValue)**
> 
- **key :** 값을 가져와야 하는 요소의 **키입니다.**
- **defaultValue :** 지정된 키로 매핑된 값이 없는 경우 반환되어야 하는 **기본값입니다.**
- **반환 값:** 찾는 key가 존재한다면 찾는 key의 value를 반환하고 없거나 null이면 default를 반환.

**ex01)**

```java
import java.util.HashMap;

public class practice {
	public static void main(String arg[]) {
    
        String [] abc = { "A", "B", "C" ,"C"}; 

        HashMap<String, Integer> hm = new HashMap<>(); 
        
        for(String key : abc) {
        	hm.put(key, hm.getOrDefault(key, 0) + 1); 
        }
        System.out.println("출력 결과 : " + hm); 

        // 출력 결과 : {A=1, B=1, C=2} 
     } 
}
```

**ex02)**

```java
💥port java.util.*;
 
public class Main {
     public static void main(String[] args) {

        String[] people = {"Mike", "Anna", "Mike", "Harry"};

        Map<String, Integer> map = new HashMap<>();

        for(String a : people) map.put(a, map.getOrDefault(a, 0) + 1);

        System.out.println(map); //{Anna=1, Mike=2, Harry=1}
    }
}       //복수 값인 'MIKE'는 찾고자 하는 키가 있으므로 1을 반환 후 +1을 해서 2가 됨.
```

## [활용문제 바로가기👉🏻](https://www.notion.so/22-05-14-713a3a81ff754a7ab2def08e1ba83f80)
