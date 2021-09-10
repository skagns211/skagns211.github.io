---
layout: single
title: '[Algorithm] Fibonacci, 효율적 계산'
---

피보나치의 수열 중 n번째 항의 수를 리턴해야 한다.
-  피보나치 수 → 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ...

입력
인자 : n
- number 타입의 n (n은 0 이상의 정수)

출력
- number 타입을 리턴한다.

주의사항
- 재귀함수를 이용한다.
- for, while 반복문 사용 금지.

```jsx
function fibonacci(n) {
// 피보나치 수의 0번째, 1번째 idx의 수를 배열에 미리 넣어준다.
  let memo = [0, 1]
  const fib = (n) => {
// memo[n]의 값이 있다면 (이미 계산된 것이라면) memo[n]을 리턴한다.
    if (memo[n] !== undefined) return memo[n];
// 그게 아니라면 memo[n]은 피보나치 점화식을 이용해 값을 넣어준다.
    memo[n] = fib(n-2) + fib(n-1);
    return memo[n];
  };
  return fib(n);
}
```

부족했던 부분
- 재귀함수가 여전히 와닿지가 않아서 헷갈렸다.
재귀함수에서 꼭 알아둬야 할 것은, 
재귀함수가 실행된다는 것은 해당 함수에 재진입하는것이 아니라,
해당 함수에 인자를 넣고 그대로 복사해서 스택에 쌓는것이다.
그 복사한 함수를 실행하다가 재귀함수가 실행되면 또다시
해당 함수에 인자를 넣고 그대로 복사해서 스택에 쌓고.. 반복하다가
더이상 쪼개질 수 없을때에 다달으면 되돌아가면서 리턴된 값들을 해당 자리에 넣어주며 계산한다.