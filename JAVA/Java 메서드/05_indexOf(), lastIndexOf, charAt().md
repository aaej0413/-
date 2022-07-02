# 특정 문자 위치 찾기
> 1. indexOf()
> 
- 파라미터로 전달받은 문자열을 원본 문자열의 앞에서부터 찾음.
- .indexOf(”찾을 특정 문자", “시작할 위치") 형식으로 사용함.
- “시작할 위치"는 생략이 가능하며, 생략할 경우 0번째 즉 처음부터 찾기 시작.
- 만약 결과값을 찾지 못했을 경우는 -1을 반환함.
- 공백도 인덱스에 포함.

```java
public static void main(String[] args) {

			 String indexOfTestOne = "Hello world"; 
			 String indexOfTestTwo = "   Hello world  ";
 
			 System.out.println( indexOfTestOne.indexOf("o") ); // 4 
			 System.out.println( indexOfTestOne.indexOf("x") ); // -1 
			 System.out.println( indexOfTestOne.indexOf("o",5) ); // 7 
			 System.out.println( indexOfTestTwo.indexOf("o") ); //7
			 System.out.println( indexOfTestTwo.indexOf("el") ); //
	}
```

> 2. lastindexOf()
> 
- 파라미터로 전달받은 문자열을 원본 문자열의 뒤에서부터 찾음.
- 발견하지 못했다면 -1을 반환.

```java
//ex) 01
public class Main {
	public static void main(String[] args) {

		String str = "abcabc";

		System.out.println(str.lastIndexOf("c")); // 5
		System.out.println(str.lastIndexOf("c", 2)); // 2
	}
}

//ex) 02
String indexOfEx = "abcde123abcde"; 

	System.out.println( indexOfEx.lastIndexOf("a") ); //8 
	System.out.println( indexOfEx.lastIndexOf("1") ); //5 
	System.out.println( indexOfEx.lastIndexOf("de") ); //11 
	System.out.println( indexOfEx.lastIndexOf("a", 7) ); //0 
	System.out.println( indexOfEx.lastIndexOf("z") ); //-1
	
```

> 3. charAt()
> 
- String으로 저장된 문자열 중에서 해당위치에 있는 문자를 char타입으로 변환해줌.
- 괄호에는 인덱스 번호를 입력.
- charAt(0)이라면 문자열의 0번째 문자를 char타입으로 변환.

```java
public class Test {
	public static void main(String[] args) {
    // 변수 선언
    String example = "안녕하세요";
    char target1;
    char target2;
    char target3;
    
    target1 = example.charAt(0);
    target2 = example.charAt(1);
    target3 = example.charAt(2);
    
    System.out.println(target);   //안
    System.out.println(target2);   //녕
    System.out.println(target3);   //하
}
```

사용방법

```java
String str2 = "Hello World"; String Odd = ""; 
String Even = ""; int length = str2.length(); 

for(int i = 0; i < length; i++) { 
	if(i % 2 == 0) Odd = Odd + str2.charAt(i);{ 
	}
	else {
	Even = Even + str2.charAt(i); 
	}
} 
System.out.println(Odd); System.out.println(Even);
```
