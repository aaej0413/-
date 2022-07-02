# 문자열 자르기
> 1. **SubString**
> 

- 우선 문자열을 자르기에 앞서 문자열이 어떻게 배치되어 있는지 index값부터 살펴봐야함.
- 아래 사진처럼 String 클래스 자체가 char을 여러개 붙여놓은 효과를 줌.
- 때문에, String 클래스 해당 index값은 아래 사진과 같음.

![https://t1.daumcdn.net/cfile/tistory/997B4D3D5AD8B0CE21](https://t1.daumcdn.net/cfile/tistory/997B4D3D5AD8B0CE21)

**Substring 사용법**

```java
String.substring(start) //문자열  start위치부터 끝까지 문자열 자르기
String.substring(start,end) //문자열  start위치 부터 end전까지 문자열 발췌
		
//예제
String str = "ABCDEFG"; //대상 문자열
/*A=0 B=1 C=2 D=3 E=4 F=5 G=6의 index를 가진다.*/
		
str.substring(3); 
/*substring(시작위치) 결과값 = DEFG*/

str.substring(3, 6); 
/*substring(시작위치,끝위치) 결과값 = DEF*/
```

**Substring 활용예제**

```java
//1. 마지막 2글자
  String str = "ABCDEFG"; 
  String result = str.substring(str.length()-2, str.length());
	//str.length()-2 = str문자열 길이 -2

  System.out.println(result);
   //결과값 FG

//2. 특정문자 이후의 문자열 출력
  str = "ABCD/DEFGH";
  String result = str.substring(str.lastIndexOf("/")+1);
	// "/" 문자 이후 문자열부터 끝까지   
  System.out.println(result);  // end 값을 넣지 않을경우 값은 문자열 끝으로 잡힌다.
  //결과값 DEFGH

// 3. 특정단어(부분)만 자르기
  String str = "바나나 : 1000원, 사과 : 2000원, 배 : 3000원";
	String target = "사과";
	int target_num = str.indexOf(target);
 
	String result = str.substring(target_num,(str.substring(target_num).indexOf("원")+target_num));
	System.out.println(result+"원"); 
	//결과값 : 사과 : 2000원
	
```
