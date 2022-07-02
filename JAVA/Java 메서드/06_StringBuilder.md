# StringBuilder 사용법, 주요 메소드
> **StringBuilder**
> 

 - 자바에서 String 객체는 변경 불가능하다. 한 번 생성되면 내용을 바꿀 수 없단 뜻이다. 따라서 하나의 문자열을 다른 문자열과 연결하면 새 문자열이 생성되고, 이전 문자열은 가비지 컬렉터로 들어간다. 
그래서 나온것이 **“StringBuilder!”** Stirng은 변경 불가능한 문자열을 생성하지만 StringBuilder는 변경 가능한 문자열을 만들어 주기 때문에, String을 합치는 작업 시 하나의 대안이 될 수 있다.

- **ex01**

```java
StringBuilder sb = new StringBuilder();

sb.append("ABC");
sb.append("DEF");

System.out.println(sb.toString()); // ABCDEF
```

- **ex02**

```java
public class Main
{
    public static void main(String[] args)
    {
        String result2 = "프로그래밍 - ";
        String java = "자바";
        String android = "안드로이드";
        String result = java + android;
        result2 += java += android;
        System.out.println(result);
        System.out.println(result2);
    }
}
```

- **ex03**

```java
public class Main
{
    public static void main(String[] args)
    {
        StringBuilder stringBuilder = new StringBuilder();
        stringBuilder.append("문자열 ").append("연결");

				//String str = stringBuilder;   
				// String에 StringBuilder를 그대로 넣을 순 없다. toString()을 붙여야 한다
        String str = stringBuilder.toString();

        // 두 println()은 같은 값을 출력한다
        System.out.println(stringBuilder);
        System.out.println(str);
    }

}
```

- **ex04 (반복문에서)**

```java
public class Main
{
    public static void main(String[] args)
    {
        StringBuilder stringBuilder = new StringBuilder();
        ArrayList<String> list = new ArrayList<>();
        list.add("첫 번째, ");
        list.add("두 번째, ");
        list.add("세 번째, ");
        list.add("네 번째, ");
        list.add("다섯 번째");
        for (int i = 0; i < list.size(); i++)
        {
            stringBuilder.append(list.get(i));
        }
        System.out.println(stringBuilder); // 첫 번째, 두 번째, 세 번째, 네 번째, 다섯 번째
    }
}
```



> **StringBuilder 주요 함수💥**
> 
- **.append()**: 문자열을 추가한다. (sb.append("bbb"), sb.append(4))
- **.insert(int offset, String str)**: offset 위치에 str을 추가한다. (sb.insert(2, "ccc"))
- **.replace()**: 첫번째와 두번째 파라미터로 받는 숫자 인덱스에 위치한 문자열을 대체한다. (.replace(3, 6, "ye"))
- **.substring(int start, (int end)):** 인덱싱. 파라미터가 하나라면 해당 인덱스부터 끝까지, 두개라면 시작점과 끝점-1 까지 인덱싱 (sb.substring(5), sb.substring(3, 7))
- **.deleteCharAt(int index)**: 인덱스에 위치한 문자 하나를 삭제한다. (sb.deleteCharAt(3))
- .**delete(int start, int end)**: start 부터 end-1 까지의 문자를 삭제한다. (sb.delete(3, sb.length()))
- **.toString()**: String으로 변환한다. (sb.toString())
- **.reverse()**: 해당 문자 전체를 뒤집는다. (sb.reverse())
- **.setCharAt(int index, String s)**: index 위치의 문자를 s로 변경
- **.setLength(int len)**: 문자열 길이 조정, 현재 문자열보다 길게 조정하면 공백으로 채워짐, 현재 문자열보다 짧게 조정하면 나머지 문자는 삭제
- **.trimToSize()**: 문자열이 저장된 char[] 배열 사이즈를 현재 문자열 길이와 동일하게 조정, String 클래스의 trim()이 앞 뒤 공백을 제거하는 것과 같이 공백 사이즈를 제공하는 것, 배열의 남는 사이즈는 공백이므로, 문자열 뒷부분의 공백을 모두 제거해준다고 보면 됨

```java
import java.lang.StringBuilder;

public class sb {
    public static void main(String[] args) throws IOException{
        StringBuilder sb = new StringBuilder("aaa");

        // 문자열 추가
        System.out.println(sb.append("bbb")); // aaabbb
        System.out.println(sb.append(4)); // aaabbb4

        // 문자열 삽입
        System.out.println(sb.insert(2, "ccc")); // aacccabbb4
        
        // 문자열 치환, 문자열 교체
        System.out.println(sb.replace(3, 6, "ye")); // aacyebbb4

        // 인덱싱, 문자열 자르기
        System.out.println(sb.substring(5)); // bbb4
        System.out.println(sb.substring(3, 7)); // yebb

        // 문자 삭제
        System.out.println(sb.deleteCharAt(3)); // aacebbb4

        // 문자열 삭제
        System.out.println(sb.delete(3, sb.length())); // aac

        // 문자열 변환
        System.out.println(sb.toString()); // aac

        // 문자열 뒤집기
        System.out.println(sb.reverse()); // caa

        // 문자 대체, 문자 교체, 문자 치환
        sb.setCharAt(1, 'b');
        System.out.println(sb); // cba

        // 문자열 길이 조정
        sb.setLength(2);
        System.out.println(sb); // cb
    }
}
```

**String**                :  문자열 연산이 적고 멀티쓰레드 환경일 경우

**StringBuffer**    **** :  문자열 연산이 많고 멀티쓰레드 환경일 경우

**StringBuilder**   :  문자열 연산이 많고 단일쓰레드이거나 동기화를 고려하지 않아도 되는 경우
