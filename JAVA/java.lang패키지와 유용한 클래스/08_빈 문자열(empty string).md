# 08_빈 문자열(empty string)
>
> 길이가 0인 배열이 존재할 수 있을까???
> 답은 YES! 이다.  
> char형 배열도 길이가 0인 배열을 생성할 수 있고, 이 배열을 내부적으로 가지고 있는 문자열이 바로 빈 문자열이다.
> 

> ’`String s = “”;`’과 같은 문장이 있을 때, 참조변수 s가 참조하고 있는 String 인스턴스는 
내부에 ‘`new char[0]`’와 같이 길이가 0인 char형 배열을 저장하고 있는것!
> 

> ‘String s = “”;’와 같은 표형이 가능하다고 해서 ‘`char c = “;`’와 같은 표현이 가능한 것은 아니다.
char형 변수에는 반드시 하나의 문자를 지정해야 한다.
> 

```java
String s = null;     ->     String s = "";   // 빈 문자열로 초기화
char c = '\u000';    ->     char c = '';     // 공백으로 초기화
```

- 일반적으로 변수를 선언할 때,  각 타입의 기본값으로 초기화 하지만
- **String은** 참조형 타입의 기본값인 `null 보다는 빈 문자열`로,
- **char형은** 기본값인 `“\u0000” 대신 공백으로 초기화` 하는 것이 보통이다.

### ex)

```java
/*
빈 문자열 (empty string)
 */
public class Ex9_8 {
    public static void main(String[] args) {

        // 길이가 0인 char배열을 선언한다.
        char[] cArr = new char[0];         // char[] cArr = {}; 와 같다.
        String s = new String(cArr);       // String s = new String(""); 와 같다.

        System.out.println("cArr.length=" + cArr.length);
        System.out.println("@@@" + s + "@@@");
    }
}
```
