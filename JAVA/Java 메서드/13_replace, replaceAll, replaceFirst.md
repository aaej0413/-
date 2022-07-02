# 자바 특정 문자 & 특수 문자 제거/치환하기 -> (replace / replaceAll / replaceFirst)
### 1. replace

> replace(char oldchar, char newChar)
→ 문자열.replace(바꾸고 싶은 문자, 바꿀 문자)
> 
- ex_01)

```java
public static void main(String[] args) {
	
	String old = "abcdabcd";
	String newchar = old.replace("a","z");

	System.out.println(newchar);     // **z**bcd**z**bcd
}
```

- ex_02)

```java
public static void main(String[] args) {
	
	String old = "abcd.abcd";
	String newchar = old.replace(".","z");

	System.out.println(newchar);     // abcd**z**abcd
}
```

### 2. replaceFirst

> replaceFirst(String regax, String replacement)
→ 문자열.replaceFirst(기존문자, 대체문자) 
    = 바꾸고 싶은 문자열에서 처음으로 찾은 문자만 반환.
> 

```java
public static void main(String[] args) {
	
	String old = "abcdaaefg";
	String newchar = old.replaceFirst("a","z");

	System.out.println(newchar);     // **z**bcdaaefg
}                                  // 첫 번째로 찾은 문자 a만 z로 변환.
```

### 3. replaceAll

> replaceAll(String regax, String replacement)
→ 문자열.replaceAll(정규식, 대체문자) 
    = 그냥 문자열을 바꾸고 싶을 때는 replace와 동일한 출력 값을 내지만, 특수문자를 변환하고 싶을 때는 
       결과가 다르게 나옴.
> 

- ex_01)

```java
public static void main(String[] args) {
	
	String old = "abcdabcd";
	String newchar = old.replaceAll("a","z");

	System.out.println(newchar);     // **z**bcd**z**bcd
}                                  // 기존 replace랑 같음.
```

- ex_02)

```java
public static void main(String[] args) {
	
	String old = "abcd.abcd";
	String newchar = old.replace(".","z");

	System.out.println(newchar);     // zzzzzzzzz
}                                  // "."은 모든 자릿수를 대체함.
```

- ex_03)

```java
public static void main(String[] args) {
	
	String old = "0123456789변환";
	String newchar = old.replace("[0-9]","숫자");  //[0-9]는 숫자를 찾아주는 정규식.

	System.out.println(newchar);     // 숫자숫자숫자숫자숫자숫자숫자숫자숫자숫자변환
}                                  // []안에 있는 문자들을 전부 변환.
```
