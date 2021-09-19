---
layout: single
title: "[Algorithm], findMatryoshka, 재귀"
---

러시아 전통 인형 마트료시카에 대한 정보를 담은 객체와 수를 입력받아 조건에 맞는 인형이 있는지 여부를 리턴해야 한다.

입력
인자1 : matryoshka

- 'matryoshka', 'size' 속성을 갖는 재귀적으로 정의된 객체
- 'matryoshka.matryoshka'는 null 또는 'matryoshka' 객체
- 'matryoshka.size'는 중첩될 수록 작아진다.

인자2: size

- number 타입의 수

출력

- boolean 타입을 리턴한다.

주의사항

- **함수 `findMatryoshka`는 재귀함수의 형태로** 작성한다.
- 반복문(`for`, `while`) 사용은 금지된다.
- 입력받은 객체는 함수의 호출 뒤에도 처음 상태를 유지해야 한다(immutability).
- 빈 객체를 입력받은 경우, false를 리턴해야 한다.

## 사전지식 복습

빈 객체 판별하는 방법?

→ Object.keys(obj).length가 0이면, 빈 객체이다.

Object.keys(obj)는 obj의 key를 배열로 반환한다.

그 배열의 length가 0이면 key가 없다는 뜻이므로, 빈 객체이다.

```jsx
function findMatryoshka(matryoshka, size) {
  // 빈 객체를 입력받으면 false를 리턴한다.
  if (Object.keys(matryoshka).length === 0) return false;

  // 만약 matryoshka의 size가 인자로 주어진 size와 같다면 true를 리턴.
  if (matryoshka.size === size) return true;
  /* matryoshka의 size와 인자로 주어진 size가 다르고,
  matryoshka의 matryoshka가 null이면 (더이상 내려들어가지 않으면) false를 리턴. */ else if (
    matryoshka.size !== size
  ) {
    if (matryoshka.matryoshka === null) {
      return false;
    }
  }
  // findMatryoshka의 인자로 matryoshka.matryoshka, size를 전달한다.
  return findMatryoshka(matryoshka.matryoshka, size);
}
```
