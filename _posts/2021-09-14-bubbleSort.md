---
layout: single
title: "[Algorithm], BubbleSort, 버블 정렬"
---

정수를 요소로 갖는 배열을 입력받아 오름차순으로 정렬하여 리턴해야 합니다.
버블 정렬(bubble sort)은 여러 정렬 알고리즘(삽입 정렬, 퀵 정렬, 병합 정렬, 기수 정렬 등) 중 가장 기본적인 알고리즘입니다.버블 정렬 알고리즘은 아래와 같습니다.

1. 첫 번째 요소가 두 번째 요소보다 크면, 두 요소의 위치를 바꿉니다. (swap)
2. 두 번째 요소와 세 번째 요소보다 크면, 두 요소의 위치를 바꿉니다. (swap)
3. 1, 2를 마지막까지 반복합니다. (마지막에서 두 번째 요소와 마지막 요소를 비교)
4. 1~3의 과정을 한 번 거치게 되면, 가장 큰 요소가 배열의 마지막으로 밀려납니다.
5. 1~3의 과정을 첫 요소부터 다시 반복합니다.
6. 5를 통해 두 번째로 큰 요소가 배열의 마지막 바로 두 번째로 밀려납니다.
7. 1~3의 과정을 총 n번(배열의 크기) 반복합니다.

이 모습이 마치 '거품이 밀려 올라가는 것과 같은 모습'과 같아서 bubble sort라고 부릅니다.

입력
인자1 : arr

- number 타입을 요소로 갖는 배열
- arr[i] 는 정수
- arr[i] 의 길이는 1,000 이하

출력

- number 타입을 요소로 갖는 배열을 리턴
- 배열의 요소는 오름차순으로 정렬
- arr[i] ≤ arr[j] ( i < j )

주의사항

- 위에서 설명한 알고리즘을 구현해야 합니다.
- arr.sort 사용은 금지됩니다.
- 입력으로 주어진 배열은 중첩되지 않은 1차원 배열입니다.

```jsx
const bubbleSort = function (arr) {
  for (let i = 0; i < arr.length; i++) {
    let temp;
    /* 앞에서부터 큰 숫자가 맨 뒤로 이동하기 때문에, 이미 정렬된 맨 끝은 계산할 필요가 없으므로
       -i를 해준다. */
    for (let j = 0; j < arr.length - 1 - i; j++) {
      // 앞의 숫자와 뒤의 숫자를 비교해서, 앞의 숫자가 더 크면
      if (arr[j] > arr[j + 1]) {
        // temp에 앞의 숫자를 할당
        temp = arr[j];
        // arr[j]는 뒤의 숫자를 할당
        arr[j] = arr[j + 1];
        // arr[j+1]은 앞의 숫자를 할당한다
        /* (정리 -> 앞의 숫자가 뒤의 숫자보다 크면 앞의 숫자는 뒤로 이동해야 하므로,
				앞의 숫자를 temp로 저장해준뒤, 앞의 숫자와 뒤의 숫자의 자리를 바꿔치기한다. */
        arr[j + 1] = temp;
      }
    }
    // temp가 undefined라면 (모든 앞의 숫자들이 뒤의 숫자보다 작을때) 반복문 탈출
    if (temp === undefined) {
      break;
    }
  }
  return arr;
};
```