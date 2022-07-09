# 13_연결된 예외(chained exeption)
> **한 예외가 다른 예외를 발생시킬 수도 있다.** 예를 들어 예외 A가 예외 B를 발생시켰다면,  
A를 B의 “원인 예외(cause exception)”라고 한다.
> 

  

ex)

```java
try {
      startInstall();   // SpaceException 발생 
      copyFile();
  } catch (SpaceException e) {
      InstallException ie = new InstallException("설치중 예외발생");  // 예외 생성
      **ie.initCause(e)**;  // InstallException의 원인 예외를 SpaceException으로 지정
      throw ie;         // InstallException을 발생시킴.
  } catch (MemoryException me) {
			...
```

![스크린샷 2022-07-09 오후 8.08.14.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e42058f6-427f-4dd1-8fd8-61b8bbaa6421/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-07-09_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_8.08.14.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220709T110828Z&X-Amz-Expires=86400&X-Amz-Signature=ab61e091d10d958a0eac7adfef5db79cad27c93e83a32bf8a78c7408055d4c2f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-07-09%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25208.08.14.png%22&x-id=GetObject)

## 원인 예외 사용 이유

1. 여러 예외를 하나로 묶기 위해서.

1. checked 예외를 unchecked예외로 바꿀 때 사용
    
    ```java
    static void startInstall() throws SpaceException, MemoryException {
        if(!enoughSpace())		// 충분한 설치 공간이 없는 경우
        	throw new SpaceException("설치할 공간이 부족합니다.");
    
        if(!enoughMemory())		// 충분한 메모리가 없는 경우
        	throw new MemoryException("메모리가 부족합니다.");
    }
    ```
    
    위 코드를 아래와 같이 변경 가능
    
    ```java
    static void startInstall() throws SpaceException {
        if(!enoughSpace())		// 충분한 설치 공간이 없는 경우
        	throw new SpaceException("설치할 공간이 부족합니다.");
    
        if(!enoughMemory())		// 충분한 메모리가 없는 경우
        	throw new RuntimeException(new MemoryException("메모리가 부족합니다.")); // 원인 예외로 등록
    } // startInstall 메서드 끝
    ```
    
    <aside>
    👉🏻 RuntimeException(Throwable cause) → 원인 예외를 등록하는 생성자.
    
    </aside>
    

# 연결된 예외(chained exception)예제

```java
public class Ex8_13 {
    public static void main(String[] args) {
        try {
            install2();
        } catch (InstallException2 e) {
            e.printStackTrace();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    static void install2() throws InstallException2 {
        try {
            startInstall2();
            copyFiles2();
        } catch (SpaceException2 e) {
            InstallException2 ie = new InstallException2("설치중 예외발생");
            ie.initCause(e);
            throw ie;
        } catch (MemoryException2 me) {
            InstallException2 ie = new InstallException2("설치중 예외발생");
            ie.initCause(me);
            throw ie;
        } finally {
            deleteTempFiles2();
        }
    }

   static void startInstall2() throws SpaceException2,MemoryException2 {
        if(!enoughSpace2()) {
            throw new SpaceException2("설치할 공간이 부족합니다.");
        }
        if(!enoughMemory2()) {
            throw new MemoryException2("메모리가 부족합니다.");
        //  throw new RuntimeException(new MemoryException("메모리가 부족합니다."));
        }
    }

    static void copyFiles2() {}
    static void deleteTempFiles2() {}

    static boolean enoughMemory2() {
        return true;
    }

    static boolean enoughSpace2() {
        return false;
    }

    static class InstallException2 extends Exception {
        InstallException2(String msg) {
            super(msg);
        }
    }

    static class SpaceException2 extends Exception {
        SpaceException2(String msg) {
            super(msg);
        }
    }

    static class MemoryException2 extends Exception {
        MemoryException2(String msg) {
            super(msg);
        }
    }
}
```
