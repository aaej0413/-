# 비교 대상의 문자열이 지정된 접두사로 시작하는지 확인
> **비교대상 문자열.startsWith(접두사)**
> 
- **지정된 접두사로 시작하면, false 반환**

```java
public static void main(String[] args) {
        String[] members = {"안은주", "김주희", "테이", "응두", "응가"};
        boolean answer = true;

        for(int i = 0; i < members.length; i++) {
            if (members[i].startsWith("응")) {
                answer = false;
            }
        }
        System.out.println(answer);  // false 반환
    }
```

- **지정된 접두사로 시작하지 않으면, true 반환**

```java
public static void main(String[] args) {
        String[] members = {"안은주", "김주희", "테이", "응두", "응가"};
        boolean answer = true;

        for(int i = 0; i < members.length; i++) {
            if (members[i].startsWith("주")) {
                answer = false;
            }
        }
        System.out.println(answer);  // true 반환 
    }
```
