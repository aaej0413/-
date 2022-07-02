# 문자열을 char타입의 배열로 변환하기

> **String.toCharArray()**
> 
- 문자열을 한 글자씩 쪼개서 이를 char 타입의 배열의 집어넣어주는 함수.
- 즉, String(문자열)을 char형 배열로 바꾼다.

```java
public class Main {
	public static void main(String[] args) {

		String str = "abc";
		
		char[] charArr = str.toCharArray();

		// 3. char 배열 출력
		for(int i = 0; i < charArr.length; i++) {
		System.out.println(charArr[i]);
		}
	}
}

//결과 a
      b
      c
```
