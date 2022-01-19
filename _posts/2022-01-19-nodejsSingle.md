---
layout: single
title: "Node.js의 작동 방식"
---

JavaScript는 싱글스레드이다.

Node.js는 JavaScript를 기반으로 한 V8 엔진으로 빌드된 런타임 환경이다.

그렇다면 Node.js는 싱글스레드일까? 에 대한 궁금증에 대한 정리를 해보자.

## 스레드란?

우선 싱글 스레드에서 “스레드”란 무엇인지 알고가자.

실행 준비가 완료된 코드들의 묶음이 프로그램이고,

이 프로그램들이 실행되고 있어서 CPU의 처리 과정에 속하게 되면 Process, 프로세스라고 한다.

CPU가 처리해야 할 프로세스들이 쌓이면,

즉 CPU가 처리할 작업들이 쌓여있는 리스트를 스레드라고 할 수 있다.

또는, CPU의 “코어”라는 노동자의 팔 개수라고 비유하기도 한다.

## 싱글스레드와 멀티스레드란?

싱글스레드는 하나의 스레드만 가지고, 멀티스레드는 2개 이상의 스레드를 가지는 방식이다.

알아두고 가야 할 것은, 멀티스레드라고 싱글스레드보다 무조건 좋은 방식인 것은 아니다.

## Node.js는 싱글스레드인가 멀티스레드인가?

결론적으로 이야기 하자면, Node.js는 V8 엔진에 비동기 이벤트 처리 라이브러리(libuv)를 결합했는데,

비동기 이벤트 처리에 가장 적합한 방식은 싱글스레드 방식이기 때문에 Node.js는 싱글스레드이다.

## 이벤트 루프

그렇다면 이벤트 처리, 즉 이벤트 루프란 무엇일까?

```jsx
const eventLoop = () => {
  console.log(1);
  setTimeout(() => {
    console.log(2);
  }, 5000);
  setTimeout(() => {
    console.log(3);
  }, 0);
  console.log(4);
};
```

위의 코드대로 입력했을 때, 콘솔에는 어느 순서로 출력이 될까?

얼마 전에 알아봤던 Hoisting 포스팅에서 봤듯이, JavaScript는 인터프리터에 의해서

위에서부터 순차적으로 코드가 실행, 즉 동기적으로 실행되기 때문에

1이 찍히고, 5초뒤에 2, 곧이어 3과 4가 순서대로 출력될 것이라고 생각할 수 있지만,

setTimeout 함수는 비동기로 동작하는 Web API이기 때문에

1 → 4 → 3 → 2 의 순서대로 출력된다.

![](https://images.velog.io/images/skagns211/post/bb9fee90-4588-4c61-a874-3be2ebb5c394/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-20%2000.20.52.png)

가장 먼저 코드가 호출(main)되면서 Stack에 쌓이고, console.log(1)이 다음 Stack으로 쌓이고

실행이 된 뒤 Stack에서 빠지게 된다.

![](https://images.velog.io/images/skagns211/post/93b2df35-9aac-467f-ae01-288532cf0109/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-20%2000.21.08.png)

다음으로 첫번째 setTimeout 함수가 호출되면서 Stack에 쌓이고 실행이 된 뒤 빠지고,

Web API의 작업 영역에 setTimeout 함수를 넘긴 뒤 setTimeout 함수는 대기를 하게 된다.

두번째 setTimeout도 마찬가지로 Stack에 쌓인 뒤 실행되면서 빠지고, Web API에 넘어간다.

![](https://images.velog.io/images/skagns211/post/807455f0-308a-4fb1-9b1d-eaac8415ab7b/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-20%2000.21.28.png)

다음으로 console.log(4)가 호출되면서 Stack에 쌓이고, 실행되면서 빠지고,

main 역시 모든 작업이 끝났기 때문에 실행이 종료되어 Stack에서 빠진다.

현재까지 콘솔에는 1 → 4의 순서대로 찍혀있는 상태이다.

![](https://images.velog.io/images/skagns211/post/9f8f0826-73dd-4b2f-999e-4f0a98b5dd41/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-20%2000.21.44.png)

다음으로, Stack이 비었기 때문에 (Stack이 비어있을 때 Task Queue의 Callback을 Stack으로

push 할 수 있다)

Web API에서 대기중이던 setTimeout 함수들이 실행되어 Task Queue에 순서대로 쌓인 뒤

Stack에 push된다.

![](https://images.velog.io/images/skagns211/post/ffe1cb1c-f792-459d-a404-87252a89d109/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-20%2000.22.04.png)

Task Queue에 쌓여있던 Callback이 Stack에 쌓이고, 실행이 된 후 Stack에서 빠진다.

현재는 1 → 4 → 3 의 순서로 콘솔에 출력된 상태이다.

![](https://images.velog.io/images/skagns211/post/9090b0a5-537e-47b2-ae68-32a411bd04ad/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-20%2000.22.16.png)

마지막으로, Task Queue에 있던 Callback이 Stack에 쌓이고, 실행이 된 후 Stack에서 빠지면서

최종적으로 콘솔에 1 → 4 → 3 → 2 의 순서로 출력된 후 작업이 종료된다.

지금까지 이벤트 루프에 대해서 알아봤는데, 보다시피 싱글스레드 방식이다.

앞서 말했듯이 Node.js는 비동기 이벤트 처리 라이브러리를 결합했기 때문에,

당연히 “Node.js는 싱글스레드 방식”이다.
