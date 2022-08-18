# Stack,Queue
# Stack

- 뒤에서 부터 꺼내기
- **LIFO = Last In First Out**
- “가장 나중에 들어간 값이 가장 먼저 나온다”
- 스택은 저금통처럼 양 옆과 바닥이 막혀 있어서 위로만 뺄수 있는 # Stack

- 뒤에서 부터 꺼내기
- **LIFO = Last In First Out**
- “가장 나중에 들어간 값이 가장 먼저 나온다”
- 스택은 저금통처럼 양 옆과 바닥이 막혀 있어서 위로만 뺄수 있는 구조!!

![스크린샷 2022-06-14 오후 4.52.57.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f81ddcc1-c6c4-414f-aff9-ae919615c79f/스크린샷_2022-06-14_오후_4.52.57.png)

- `boolean empty()` - Stack이 비어있는지 알려준다.
- `Object push(Object item)` - Stack에 객체(item)을 저장한다.
- `Object pop()` - Stack의 맨 위에 저장된 객체를 꺼낸다. (비었을 때는 EmptyStackException발생)
- `Object peek()` - Stack의 맨 위에 저장된 객체를 반환. pop()과 달리 Stack에서 객체를 꺼내지는 않음. (비었을 때는 EmptyStackException 발생)
