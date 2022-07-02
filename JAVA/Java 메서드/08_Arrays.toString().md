# 배열의 내용 출력 (배열의 주소값이 아닌 내용을 출력할 경우 사용)
> **Arrays.toString**
> 

 자바에서 배열 내용을 출력해보려고 배열 자체에서 toString()을 사용하면  

 배열의 내용이 아니라 **배열의 주소값**이 출력됩니다. 

```java
double[] values = {1.0, 1.1, 1.2};

System.out.println(values.toString()); //이렇게 하면 [D@46a49e6 같은 값이 나옵니다.
```

 **배열의 내용을 출력하려면 Arrays.toString()을 사용**해야 합니다. 예제 코드는 아래와 같습니다.

```java
System.out.println(**Arrays.toString**(**values**)); 
// 이렇게 하면 [1.0, 1.1, 1.2] 이 출력됩니다
```
