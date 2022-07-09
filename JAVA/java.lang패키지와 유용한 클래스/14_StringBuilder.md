# 14_StringBuilder
- **StringBuffer는 멀티쓰레드에 안전(thread safe)하도록 동기화**되어 있다.
- **동기화**는 StringBuffer의 **성능을 떨어뜨릴 수 있다.**
- *멀티쓰레드로 작성된 프로그램이 아닌 경우, StringBuffer의 동기화는 불필요하게 성능만 떨어 뜨린다.*

### 그래서‼️

- StringBuffer에서 쓰레드의 동기화만 뺀 **StringBuilder가 새로 추가**되었다.
- StringBuilder는 StringBuffer와 완전히 똑같은 기능으로 작성되어 있어서, 소스코드에서 StringBuffer대신 StringBuilder를 사용하도록 바꾸기만 하면 된다.

![스크린샷 2022-07-08 오후 9.01.22.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/99d74a8e-5cd5-49f1-9133-d03f1c735778/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-07-08_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_9.01.22.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220709%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220709T103920Z&X-Amz-Expires=86400&X-Amz-Signature=176985b729ae2539f0bd6e6fad7758f200446f68e92dac9ae35f0993c76b26ea&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-07-08%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25209.01.22.png%22&x-id=GetObject)

- StringBuffer도 충분히 성능이 좋기 때문에 성능향상이 반드시 필요한 경우를 제외하고는 굳이 바꿀 필요는 없다.
