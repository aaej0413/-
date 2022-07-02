# 숫자 및 문자 여부 확인

> **Character.isDigit**
> 
- 문자가 숫자인지 확인하는 함수이다.

```java
import java.util.Arrays;

public class IsDigit {

	public static void main(String[] args) {

		String data = "5안3녕hi";
		char arr[] = data.toCharArray();		
		
		for(int i=0; i<arr.length; i++) {
			if(Character.isDigit(arr[i]) == true) {
				System.out.println(arr[i]+" : "+"숫자");  //숫자
			}
			else {
				System.out.println(arr[i]+" : "+"문자");
			}
		}
	}
}
```

<aside>
💡 [isDigit을 활용한 문제로 이동하기.](https://www.notion.so/22-05-14-713a3a81ff754a7ab2def08e1ba83f80)

</aside>
