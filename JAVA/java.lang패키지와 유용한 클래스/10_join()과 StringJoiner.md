# 10_join()과 StringJoiner
> **join()은** 여러 **문자열 사이에 구분자를 넣어서 결합**한다.
구분자로 문자열을 자르는 ***split()과 반대의 작업***을 한다.
> 

### 01_ex) - join()

```java
String animals = "dog,cat,bear";
String[] arr = animals.split(",");   // 문자열을 ','를 구분자로 나눠서 배열에 저장.
String str = **String.join**("-",arr);   // 배열의 문자열을 **'-'로 구분해서 결합.**
System.out.println(str);          
```

**실행 결과**

```java
dog-cat-bear
```

- java.util.StringJoiner클래스를 사용하여 문자열을 결합할 수도 있는데,
- 사용 방법은 아래와 같다.

---

### 02_ex) - StringJoiner

```java
StringJoiner sj = new StringJoiner("," , "[", "]");  
// public StringJoiner(CharSequence **delimiter**, CharSequence **prefix**, CharSequence **suffix**)

String[] strArr = {"aaa", "bbb", "ccc"};

for(String s : strArr)
			sj.add(s.toUpperCase());

System.out.println(sj.toString());
```

**실행 결과**

```java
[AAA,BBB,CCC]
```

---

### 코드 예제

```java
/*
join()과 StringJoiner
 */
public class Ex9_9 {
    public static void main(String[] args) {

        String animals = "dog,cat,bear";
        String[] arr = animals.split(",");

        System.out.println(**String.join**("-",arr));

        **StringJoiner** sj = new **StringJoiner**("/", "[", "]");

        for(String s : arr) {
            sj.add(s);
        }
        System.out.println(sj.toString());
    }
}
```

**실행 결과**

```java
dog-cat-bear
[dog/cat/bear]
```
