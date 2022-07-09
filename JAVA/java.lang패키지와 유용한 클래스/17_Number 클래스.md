# 17_Number 클래스
> Number클래스는 추상클래스로 내부적으로 숫자를 멤버변수로 갖는 래퍼 클래스들의 조상이다.  
아래의 그림은 래퍼 클래스(회색 바탕)의 상속계층도인데, 기본형 중에서 숫자와 관련된 래퍼 클래스들은  
모두 Number클래스의 자손이라는 것을 알 수 있다.
> 

![스크린샷 2022-07-09 오후 2.03.36.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/67a96974-31a7-4718-a21b-39b183c96089/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-07-09_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2.03.36.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220709T104733Z&X-Amz-Expires=86400&X-Amz-Signature=16ed0d67d2926698e3cc9c133899dac98aa0851d3d01cd339020f20805889fd8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-07-09%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25202.03.36.png%22&x-id=GetObject)

### 그 외에도, Number클래스 자손으로 BigInteger와 BigDecimal등이 있는데,

- **`BigInteger`** 는 ***long으로도 다룰 수 없는 큰 범위의 정수***를,
- **`BigDecimal`** 는 ***double로도 다룰 수 없는 큰 범위의 부동 소수점수***를 처리하기 위한 것으로
- 연산자의 역할을 대신하는 다양한 메서드를 제공한다.

## Number클래스의 실제 소스

```java
public **abstract** class **Number** implements java.io.Serializable {
    
    public **abstract** int intValue();

    public **abstract** long longValue();

    public **abstract** float floatValue();

    public **abstract** double doubleValue();

    public byte byteValue() {
        return (byte)intValue();
    }

    public short shortValue() {
        return (short)intValue();
    }
```
