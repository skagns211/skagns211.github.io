---
layout: single
title: '[Algorithm] isSubsetOf,두 개의 배열 부분집합 판별'
---

두 개의 배열 (base, sample)을 입력받아 sample이 base의 부분집합인지 여부 리턴.

입력
인자1 : base
- number 타입을 요소로 갖는 임의의 배열
- base.length는 100 이하

인자2 : sample
- number 타입을 요소로 갖는 임의의 배열
- sample.length는 100 이하

출력
- boolean 타입을 리턴한다.

주의사항
- base, sample 내에 중복되는 요소는 없다고 가정한다.

## 사전지식 복습

배열의 오름차순 정렬 방법

→ arr.sort((a, b) ⇒ a - b);

리턴값이 0보다 작을경우 a가 b보다 앞으로 가고, 0보다 클경우 b가 a보다 앞으로 온다.

```jsx
const isSubsetOf = function (base, sample) {
  base.sort((a, b) => a - b);
  sample.sort((a, b) => a - b);

const findItemInSortedArr = (item, arr, from) => {
  for (let i = from; i < arr.length; i++) {
    if (item === arr[i]) return i;
  }
  return -1;
};

  // 시간복잡도를 개선하기 위한 baseIdx
  let baseIdx = 0;
  // 배열 sample이 base에 포함되는지만 확인하면 되므로 sample 길이만큼만 반복해준다
  for (let i = 0; i < sample.length; i++) {
  // baseIdx의 값으로 위에서 만들어준 함수에 인자로 sample의 요소, base, baseIdx를 전달해준 값을 할당.
    baseIdx = findItemInSortedArr(sample[i], base, baseIdx);
  // baseIdx가 -1이면 (위에서 만들어준 함수에 의해 sample가 base에 포함되지 않는 경우) false 리턴
    if (baseIdx === -1) return false;
  }
  // 걸리지 않았으면 true 리턴
  return true;
}
```