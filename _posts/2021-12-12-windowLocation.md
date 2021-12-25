---
layout: single
title: "[Err Handling] Window.location.href is not a function"
---

## 어떤 에러?

로그아웃을 눌렀을 때 현재 페이지로 location 시키기 위해

window.location.href(currentUrl) 을 입력했는데

window.location.href is not a function이라는 에러가 떴다.

## 어떻게 해결?

```jsx
window.location.href(currentUrl);
// 위의 코드를
window.location.href = currentUrl;
// 이렇게 변경하니 오류 해결
```

위와 같이 해결했다.
