# Stream
### **1) 스트림이란?**

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/dc008e31-9854-4dcf-ac21-acfbdd4470e0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220702%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220702T074517Z&X-Amz-Expires=86400&X-Amz-Signature=781407b6d78eda079db2cdb2a2cb40d3497af6d8332827033bcc966334d9db4c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

> 자바 8에서 추가된 스트림(Stream)은 기존 자바 I/O에서 나오는 InputStream, OutputStream과는 다른것으로 함수형 프로그램에서 단계적으로 정의된 계산을 처리하기 위한 인터페이스 입니다.
> 

스트림은 데이터의 흐름으로 배열 또는 컬렉션 인스턴스에 함수를 조합하여 원하는 결과를 필터링하고 가공된 결과를 손쉽게 처리할 수 있습니다. 자바 입출력 프로그램에서 말하는 스트림과 연속된 데이터의 흐름이라는 관점에서는 비슷하지만 내용적으로는 다른것으로 특히 데이터를 다루는 여러 분야에서 유용하게 사용할 수 있으며 코딩 테스트 등에 나오는 문제들을 풀때도 도움이 많이 됩니다.

스트림은 데이터 소스를 추상화 하고 있으므로 데이터 소스에 상관없이 같은 방식으로 처리할 수 있다는 장점이 있으며 데이터를 다루는데 자주 사용되는 메서드들을 정의해 두고 있어 기존의 방식보다 간결하고 유연한 구현이 가능 합니다.

이해를 돕기 위해 간단한 예를 통해 기존의 방식과 스트림을 사용한 방식을 비교해 봅니다. 예제 구성은 다음과 같습니다.

- 동일한 데이터를 가지는 배열과 리스트를 선언.
- 각각 데이터 정렬을 위한 메서드를 통해 데이터를 정렬함.
- 정렬된 값을 확인하기 위해 출력문을 이용해 출력.

```java
**String**[] strArr = { "data1", "data2", "data3" }
**List**<**String**> strList = **Arrays**.asList(strArr);
```

### **`기존방식`**

데이터 정렬을 위해 각각 Arrays, Collections 의 sort 메서드를 이용해 정렬한 다음 for 문을 이용해 결과를 출력하는 형식 입니다.

```java
**Arrays**.sort(strArr);
**Collections**.sort(strList);

**for**(**String** str : strArr) {
  **System**.out.println(str);
}

**for**(**String** str : strList) {
  **System**.out.println(str);
}
```

### **`Stream API 사용`**

데이터 소스(배열 혹은 리스트)로 부터 스트림을 생성하고 정렬을 위해 sorted() 메서드를 호출한다음 출력을 위해 forEach() 메서드를 호출.

```java
strList.stream().sorted().forEach(**System**.out::println);
**Arrays**.stream(strArr).sorted().forEach(**System**.out::println);
```

여기에서 forEach는 `void forEach(Consumer<? super T> action)` 로 정의되어 있으며 Cosumer 함수형 인터페이스를 인자로 가집니다. 9장에서 배운것 처럼 메서드 레퍼런스를 사용하지 않고 람다식으로 표현하면 다음과 같습니다.

```java
strList.stream().sorted().forEach(x -> **System**.out.println(x));
```

### **2) 스트림과 컬렉션**

자바에서 데이터를 다루기 위한 기본은 컬렉션 프레임워크 입니다. 컬렉션은 자료구조에 대한 구현체 즉, 데이터 소스에 해당하는 것이고 스트림은 자료구조를 다루는 방법을 제공하는 것으로 이해할 수 있습니다.

기존의 컬렉션에서도 메서드를 통해 데이터를 추가, 수정, 삭제 하거나 정렬하는 등의 처리가 가능 했습니다. 다만 데이터 처리를 위해서는 각 요소들을 순회 하면서 처리해야 하고 하나의 단계가 끝나고 다른 단계를 진행하는 절차적인 구조를 가지고 있었습니다.

그러나 점점 데이터 양이 많아지고 프로그램에서 데이터를 다루는 방법이 복잡해 지면서 병렬처리의 효과적인 구현방법에 대한 필요성이 증가하고 코드의 간결화와 성능 향상이 요구 되었습니다.

파이썬과 같은 언어는 특히 데이터를 다루는데 최적화된 기능을 제공해 동일한 기능을 자바로 처리하는 것 보다 훨씬 간단한 방법으로 처리 할 수 있어 데이터에 기반한 프로그램이나 연구 목적의 프로그램 구현에 널리 사용되고 있습니다.

람다와 함께 스트림 API는 바로 이러한 문제점들을 해결하기 위한 방법으로 최신의 프로그램 언어들과 유사한 방법으로 자바에서도 데이터를 핸들링 할 수 있습니다. 스트림의 주요 특징은 다음과 같습니다.

- 스트림에서 요소들은 저장되지 않고 하부 컬렉션에 보관 되거나 필요할 때에만 생성해 사용된다.
- 스트림 연산은 원본 데이터를 바꾸지 않고 결과를 저장한 새로운 스트림을 반환한다.
- 스트림은 가능한 지연(Lazy)처리를 기본으로 한다.
- 스트림은 한번 사용되고 버려진다. -> 재활용이 안됨.
- 로직을 잘 못 설계하면 스트림을 반복해서 사용하게 되고 이는 실행 성능에 문제가 될 수 있다.
- 병렬 처리가 컬렉션 내부에서 처리되므로 많은 데이터 처리시 성능 향상의 효과가 있다.(parrallelStream 사용시)



### 02: 스트림 연산 구조와 생성

### **1) 스트림 연산 구조**

스트림은 어떻게(How)가 아니라 무엇(What)을 할것인지에 목적을 두고 사용해야 하며 연산의 파이프 라인은 스트림 생성(Create) -> 중간연산(Intermediate operating) -> 최종연산(Final operation) 의 형태를 가지며 이들은 `.`를 이용한 메서드 체이닝(Method Chanining)으로 구현 됩니다.

`Collections같은 객체 집합.스트림생성().중간연산().최종연산()`

- 중간연산 메서드는 리턴 타입이 스트림이므로 계속해서 다른 스트림 메서드를 연결해 사용할 수 있음.
- 최종연산 메서드는 리턴 타입이 스트림이 아닌것으로 메서드 체이닝을 끝내는 역할을 함.
- 최종연산이 실행 되어야 중간연산도 처리되기 때문에 중간연산들만으로 구성된 메서드 체인은 실행되지 않음.

다음은 전형적인 스트림 사용예로 중복 데이터를 제거하고 데이터를 5개로 제한해서 정렬한 다음 출력하는 코드 입니다.

```java
**Arrays**.stream(strArr)
	.distinct() // 중복제거
	.limit(**5**)   // 데이터를 5개로 제한
	.sorted()   // 정렬한 다음
	.forEach(**System**.out::print);   //하나하나 다 출력.
```

### 2) Stream 생성

컬렉션, 배열, 문자열, 파일등으로 부터 스트림을 생성 할 수 있습니다.

### **Empty Stream**

비어 있는 스트림을 생성하기 위해서는 empty() 메서드를 사용합니다.

**Stream**<**String**> streamEmpty = **Stream**.empty();

### **Array Stream**

배열로 부터 스트림을 생성하는 방법은 여러가지가 있습니다.

```java
**Stream**<**String**> arrayStream = **Stream**.of("a", "b", "c");

**String**[] arr = **new** **String**[]{"a", "b", "c"};

**Stream**<**String**> arrayFullStream = **Arrays**.stream(arr);

**Stream**<**String**> arrayPartStream = **Arrays**.stream(arr, **1**, **3**);
```

### **Collection Stream**

자바 컬렉션 인터페이스를 사용하는 Collection, List, Set 는 stream() 메서드와 parallelStream() 메서드를 사용할 수 있습니다. Map 의 경우 Key 혹은 Value 값만 리스트로 추출한 다음 스트림을 만들어 사용할 수 있습니다.

```java
**Collection**<**String**> collection = **Arrays**.asList("a", "b", "c");
**Stream**<**String**> collectionStream = collection.stream();

**List**<**String**> names = **new** **ArrayList**<>();
names.add("Kang");
names.add("Hong");
names.stream().forEach(**System**.out::println);
```

### **String Stream**

문자열을 다루는 클래스인 String, StringBuffer, StringBuilder는 문자열 시퀀스를 반환하는 chars() 메서드를 가지고 있는데 이를 통해 스트림을 생성하게 됩니다.

```java
**IntStream** charsStream = "abc".chars();
**String** str = "Hello World";
str.chars().filter(....)
```

### **File Stream**

파일의 경우 자바 NIO 의 Files클래스를 이용해 문자열 스트림 생성이 가능합니다.

```java
**Path** path = **Paths**.get("C:/Tmp/testfile.txt");
**Stream**<**String**> streamOfStrings = **Files**.lines(path);
**Stream**<**String**> streamWithCharset = **Files**.lines(path, **Charset**.forName("UTF-8"));
```

### **병렬 스트림(Parallel Stream)**

병렬 스트림은 내부적으로 `fork & join 프레임웍`을 이용해 자동적으로 연산을 병렬로 수행합니다. 병렬처리를 구현하기 위해 개발자가 신경써야 하는 많은 부분을 해결할 수 있으며 스트림 생성시 parallel() 메서드를 실행 하기만 하면 됩니다. 병렬 스트림 처리에서 병렬처리를 중단하려면 sequential()을 호출하면 됩니다.

```java
**int** sum = strStream.parallel()
                   .mapToInt(s -> s.length())
                   .sum();
```

스트림 활용 샘플 코드

```java
// Map에서 value 만 형변환 스트림.
**double**[] dresult = rr.values().stream().mapToDouble(i->i).toArray();
```



### 03: 중간 연산 메서드

대표적인 유형과 메서드는 다음과 같습니다.

- 스트림 필터링 : filter(), distinct()
- 스트림 변환 : map(), flatMap()
- 스트림 제한 : limit(), skip()
- 스트림 정렬 : sorted()
- 스트림 연산 결과 확인 : peek()
- 타입변환: asDoubleStream(), asLongStream(), boxed()

여기에서 사용되는 예제들은 모두 다음과 같은 리스트 데이터를 사용한다고 가정 합니다.

```java
**List**<**Integer**> intList = **Arrays**.asList(**1**,**2**,**3**);
**List**<**String**> strList = **Arrays**.asList("Hwang", "Hong", "Kang");
```

### **1) filter(), distinct()**

> 스트림 요소를 필터링 하기 위한 메서드 입니다.
> 

filter()는 스트림 요소 마다 비교문을 만족(true)하는 요소로 구성된 스트림을 반환 합니다. 즉, 특정 조건에 맞는 값만 추리기 위한 용도로 사용합니다. distinct() 는 요소들의 중복을 제거하고 스트림을 반환 합니다.

```java
intList.stream().filter(x -> x<=**2**).forEach(**System**.out::println);  // 1,2
**Arrays**.asList(**1**,**2**,**3**,**2**,**5**).stream().distinct().forEach(**System**.out::println); // 1,2,3,5
```

### **2) map()**

> 스트림의 각 요소마다 수행할 연산을 구현할때 사용합니다.
> 

```java
intList.stream().map(x -> x*x).forEach(**System**.out::println); // 1,4,9
```

### **3) flatMap()**

> 기존의 요소를 새로운 요소로 대체한 스트림을 생성 합니다.
> 

```java
**Arrays**.asList(intList,**Arrays**.asList(**2**,**5**)).stream()
	.flatMap(i -> i.stream())
	.forEach(**System**.out::println); // 1,2,3,2,5

strList.stream()
	.flatMap(message -> **Arrays**.stream(message.split("an")))
	.forEach(**System**.out::println);  // Hw, a, Hong, K, g
```

앞의 distinct() 예제에서 중복데이터 추가를 위해 Arrays.asList()를 사용했는데 flatMap()을 이용하면 다음과 같이 작성할 수 있습니다.

```java
**Arrays**.asList(intList,**Arrays**.asList(**2**,**5**)).stream()
	.flatMap(i -> i.stream())
	.distinct().forEach(**System**.out::println); // 1,2,3,5
```

### **4) limit()**

> 스트림의 시작 요소로 부터 인자로 전달된 인덱스 까지의 요소를 추출해 새로운 스트림을 생성 합니다.
> 

```java
intList.stream().limit(**2**).forEach(**System**.out::println); // 1,2
```

### **5) skip()**

> 스트림의 시작 요소로 부터 인자로 전달된 인덱스 까지를 제외하고 새로운 스트림을 생성 합니다.
> 

```java
intList.stream().skip(**2**).forEach(**System**.out::println); // 3
```

### **6) sorted**

> 스트림 요소를 정렬하는 메서드로 기본적으로 올림차순으로 정렬합니다.
> 

sorted() 를 활용하는 방법은 몇가지가 있는데 스트림 원소 객체가 Comparable 인터페이스를 구현하고 있는 상태라면 다음과 같이 하면 됩니다. Comparable 인터페이스 구현은 올림차순이라고 가정 합니다.

```java
**Arrays**.asList(**1**,**4**,**3**,**2**).stream().sorted().forEach(**System**.out::println); // 1,2,3,4
**Arrays**.asList(**1**,**4**,**3**,**2**).stream().sorted((a,b) -> b.compareTo(a)).forEach(**System**.out::println); // 4,3,2,1
**Arrays**.asList(**1**,**4**,**3**,**2**).stream().sorted( (a,b) -> -a.compareTo(b)).forEach(**System**.out::println); // 4,3,2,1
```

- 두번째와 세번째 방법은 올림차순 구현을 활용해 내림차순으로 처리할때 사용할 수 있는 방법 입니다.
- 내림차순 정렬을 위한 또다른 방법은 `a.compareTo(b)` 를 사용하는 것인데 직관적이지 못해 권장하지는 않습니다.

정렬에 사용되는 또다른 방법은 Comparator를 사용하는 것으로 새로운 정렬 조건을 지정하고자 한다면 `sorted((a,b) -> { })`와 같이 코드를 작성하면 됩니다.

```java
**Arrays**.asList(**1**,**4**,**3**,**2**).stream().sorted( **Comparator**.reverseOrder()).forEach(**System**.out::println); // 4,3,2,1
```

### **7) peak()**

> 결과 스트림의 요소를 사용해 추가로 동작을 수행합니다.
> 

원본 스트림을 이용하는 것이 아니므로 스트림 연산 과정에서 중간 중간 결과를 확인할 때 사용할 수 있습니다. 최종 연산인 `forEach()` 처럼 반복해서 요소를 처리하는 메서드 이며 중간연산이므로 최종연산 메서드가 실행되지 않으면 지연되기 때문에 반드시 최종연산 메서드가 호출되어야 동작 합니다.

앞의 filter() 예제를 보면 최종 연산으로 forEach() 를 이용해 출력하고 있습니다. 만일 최종 연산이 forEach() 가 sum() 이나 다른 최종연산이라면 값을 출력해볼 방법이 없습니다. 그렇다고 변환된 컬렉션을 가지고 출력을 위해 다시 스트림 연산을 한다면 불편할 수 있습니다. 이 경우 peak() 이 유용하게 사용될 수 있습니다.

```java
**int** sum = intList.stream().filter(x -> x<=**2**)
	.peek(**System**.out::println)
	.mapToInt(**Integer:**:intValue).sum();
**System**.out.println("sum: "+sum);
```



### 04: 최종 연산 메서드

대표적인 유형과 메서드는 다음과 같습니다. 대부분의 최종연산은 결과값만 리턴되므로 별도의 출력문을 연결해 사용하기 어렵습니다. 각 메서드 설명에 사용된 예제에서는 주석으로 결과를 표기 했으며 일부 가능한 경우만 직접 출력하고 있습니다.

- 요소의 출력 : forEach()
- 요소의 소모 : reduce()
- 요소의 검색 : findFirst(), findAny()
- 요소의 검사 : anyMatch(), allMatch(), noneMatch()
- 요소의 통계 : count(), min(), max()
- 요소의 연산 : sum(), average()
- 요소의 수집 : collect()

### **1) forEach()**

> 스트림의 요소들을 순환 하면서 반복해서 처리해야 하는 경우 사용 합니다.
> 

```java
intList.stream().forEach(**System**.out::println); // 1,2,3
intList.stream().forEach(x -> **System**.out.printf("%d : %d\n",x,x*x)); // 1,4,9
```

### **2) reduce()**

> map 과 비슷하게 동작하지만 개별연산이 아니라 누적연산이 이루어진다는 차이가 있습니다.
> 

두개의 인자 즉 n, n+1 을 가지며 연산결과는 n 이 되고 다시 다음 요소와 연산을 하게 됩니다. 즉 1,2 번째 요소를 연산하고 그 결과와 3번째 요소를 연산하는 식입니다.

```java
**int** sum = intList.stream().reduce((a,b) -> a+b).get();
**System**.out.println("sum: "+sum);  // 6
```

### **3) findFirst(), findAny()**

> 두 메서드는 스트림에서 지정한 첫번째 요소를 찾는 메서드 입니다.
> 

보통 filter() 와 함께 사용되고 findAny() 는 parallelStream() 에서 병렬 처리시 가장 먼저 발견된 요소를 찾는 메서드로 결과는 스트림 원소의 정렬 순서와 상관 없습니다.

```java
strList.stream().filter(s -> s.startsWith("H")).findFirst().ifPresent(**System**.out::println);  //Hwang
strList.parallelStream().filter(s -> s.startsWith("H")).findAny().ifPresent(**System**.out::println);  //Hwang or Hong
```

- findAny() 를 parralelStream() 과 함께 사용하는 경우 일반적으로 findFirst() 와 결과가 같다.(보장되는 것은 아님)
- parallelStream() 과 사용한 경우 실제 스트림 순서와는 다르게 선택될 수 있음.
- findFirst() 와 findAny() 의 리턴값은 Optional 이므로 ifPresent() 를 이용해 출력.

### **4) anyMatch(), allMatch(), noneMatch()**

> 스트림의 요소중 특정 조건을 만족하는 요소를 검사하는 메서드
> 

원소중 일부, 전체 혹은 일치하는 것이 없는 경우를 검사하고 boolean 값을 리턴합니다. noneMatch()의 경우 일치하는 것이 하나도 없을때 true.

```java
**boolean** result1 = strList.stream().anyMatch(s -> s.startsWith("H"));  //true
**boolean** result2 = strList.stream().allMatch(s -> s.startsWith("H"));  //false
**boolean** result3 = strList.stream().noneMatch(s -> s.startsWith("T")); //true
**System**.out.printf("%b, %b, %b",result1,result2, result3);
```

### **5) count(), min(), max()**

> 스트림의 원소들로 부터 전체 개수, 최소값, 최대값을 구하기 위한 메서드 입니다.
> 

min(), max() 의 경우 Comparator 를 인자로 요구 하고 있으므로 기본 Comparator 들을 사용하거나 직접 람다 표현식으로 구현해야 합니다.

```java
intList.stream().count();	// 3
intList.stream().filter(n -> n !=**2** ).count(); 	// 2
intList.stream().min(**Integer:**:compare).ifPresent(**System**.out::println);; 		// 1
intList.stream().max(**Integer:**:compareUnsigned).ifPresent(**System**.out::println);; // 3

strList.stream().count();	// 3
strList.stream().min(**String:**:compareToIgnoreCase).ifPresent(**System**.out::println);	// Hong
strList.stream().max(**String:**:compareTo).ifPresent(**System**.out::println);	// Kang
```

### **6) sum(), average()**

> 스트림 원소들의 합계를 구하거나 평균을 구하는 메서드 입니다.
> 

reduce() 와 map() 을 이용해도 구현이 가능 합니다. 이경우 리턴값이 옵셔널이기 때문에 ifPresent()를 이용해 값을 출력할 수 있습니다.

```java
intList.stream().mapToInt(**Integer:**:intValue).sum();	// 6
intList.stream().reduce((a,b) -> a+b).ifPresent(**System**.out::println); // 6

intList.stream().mapToInt(**Integer:**:intValue).average();	// 2
intList.stream().reduce((a,b) -> a+b).map(n -> n/intList.size()).ifPresent(**System**.out::println); // 2
```

### **7) collect()**

> 스트림의 결과를 모으기 위한 메서드로 Collectors 객체에 구현된 방법에 따라 처리하는 메서드 입니다.
> 

최종 처리후 데이터를 변환하는 경우가 많기 때문에 잘 알아 두어야 합니다. 용도별로 사용할 수 있는 Collectors 의 메서드는 기능별로 다음과 같습니다.

- 스트림을 배열이나 컬렉션으로 변환 : toArray(), toCollection(), toList(), toSet(), toMap()
- 요소의 통계와 연산 메소드와 같은 동작을 수행 : counting(), maxBy(), minBy(), summingInt(), averagingInt() 등
- 요소의 소모와 같은 동작을 수행 : reducing(), joining()
- 요소의 그룹화와 분할 : groupingBy(), partitioningBy()

```java
strList.stream().map(**String:**:toUpperCase).collect(**Collectors**.joining("/"));	 	// Hwang/Hong/Kang
strList.stream().collect(**Collectors**.toMap(k -> k, v -> v.length()));	// {Hong=4, Hwang=5, Kang=4}

intList.stream().collect(**Collectors**.counting());
intList.stream().collect(**Collectors**.maxBy(**Integer:**:compare));
intList.stream().collect(**Collectors**.reducing((a,b) -> a+b));	// 6
intList.stream().collect(**Collectors**.summarizingInt(x -> x));	//IntSummaryStatistics{count=3, sum=6, min=1, average=2.000000, max=3}

**Map**<**Boolean**, **List**<**String**>> group = strList.stream().collect(**Collectors**.groupingBy(s -> s.startsWith("H")));
group.get(**true**).forEach(**System**.out::println);  // Hwang, Hong

**Map**<**Boolean**, **List**<**String**>> partition = strList.stream().collect(**Collectors**.partitioningBy(s -> s.startsWith("H")));
partition.get(**true**).stream().forEach(**System**.out::println);  // Hwang, Hong
```

- toMap() 을 사용해서 문자열 스트림의 값을 키로 하고 문자열의 길이를 값으로 하는 맵으로 변환.
- counting, maxBy, reducing 은 각각 count(), max(), reduce() 메서드와 동일한 결과.
- summarizingInt 는 IntSummaryStatistics 를 리턴하며 count, sum, min, average, max 값을 참조할 수 있음.
- groupingBy는 특정 조건에 따라 데이터를 구분해서 저장.
- partitioningBy는 특정 조건으로 데이터를 두그룹으로 나누어 저장.
