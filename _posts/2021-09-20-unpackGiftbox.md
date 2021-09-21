---
layout: single
title: "[Algorithm], unpackGiftbox, 재귀"
---

```
💡 선물 상자에 대한 정보를 담은 배열과 문자열을 입력받아 조건에 맞는 선물이 있는지 여부를 리턴.
```

```jsx
⌨️ 입력
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
```

```jsx
function unpackGiftbox (giftBox, wish) {
  if (giftBox.length === 0 || wish === '') return false;
  
  for (let arr of giftBox) {
    if (arr === wish) return true;
    if (Array.isArray(arr)) {
      if (unpackGiftbox(arr, wish) {
        return ture;
      }
    }
  }
  return true;
}

```
