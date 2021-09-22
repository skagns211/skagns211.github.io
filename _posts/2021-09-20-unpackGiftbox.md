---
layout: single
title: "[Algorithm], unpackGiftbox, 재귀"
---

---

layout: single
title: "[Algorithm], unpackGiftbox, 재귀"

---

선물 상자에 대한 정보를 담은 배열과 문자열을 입력받아 조건에 맞는 선물이 있는지 여부를 리턴.

입력
인자1 : giftBox

- 문자열, 배열을 요소로 갖는 재귀적으로 정의된 배열
- 문자열은 선물 상자에 들어 있는 각 선물의 이름을 의미.
- 배열은 더 작은 선물 상자를 의미.

인자2 : wish

- string 타입의 문자열

출력

- boolean 타입을 리턴

주의사항

- 함수 unpackGiftbox는 재귀함수의 형태로 작성
- 반복문 (for, while) 사용 가능
- 입력받은 배열은 함수의 호출 뒤에도 처음 상태를 유지해야한다.
- 빈 배열 또는 빈 문자열을 입력받은 경우, false를 리턴

```jsx
function unpackGiftbox(giftBox, wish) {
  // 빈 배열 또는 빈 문자열일경우 false
  if (giftBox.length === 0 || wish === "") return false;

  // 변수 arr에 giftBox 요소들을 차례로 넣어준다
  for (let arr of giftBox) {
    // 만약 arr이 인자로 받은 문자열이라면, true리턴
    if (arr === wish) return true;
    // 만약 arr로 들어온 요소가 배열이면서
    if (Array.isArray(arr)) {
      // arr과 wish를 인자로 재귀 실행, 배열일시 계속 재귀 실행
      if (unpackGiftbox(arr, wish)) {
        // 실행중 arr === wish에서 true가 나오면, true 리턴
        return ture;
      }
    }
  }
  // 결국 아무것도 걸리지 않고, 빠져나오면 false;
  return false;
}
```
