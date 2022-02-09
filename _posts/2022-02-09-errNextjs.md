---
layout: single
title: "[Err handling] Prop className did not match."
---

## 어떤 에러?

```jsx
Warning: Prop `className` did not match. Server: ~~~~
```

Next.js를 공부하면서 styled-components를 사용중인데,

처음 스타일들을 적용하고 렌더링 할때는 문제없이 스타일들이 렌더링 되는데,

새로고침을 하면 `Warning : Prop 'className' did not match.` 라는 오류가 뜨면서 스타일이 사라졌다.

Next.js는 SSR이므로 첫 페이지가 렌더링 될 때는

SSR로 작동이 되고, 이후 새로고침을 하게 되면 CSR로 작동이 되는데,

이때 처음 SSR로 작동됐을 때의 해시 + 클래스명과

새로고침 후 CSR로 작동됐을 때의 해시 + 클래스명이 달라서 스타일을 불러올 수 없는 오류였다.

## 어떻게 해결?

server와 client의 클래스명을 일치시켜주는 플러그인인 바벨 플러그인 `babel-plugin-styled-components` 를 설치한 뒤 바벨 설정을 추가했다.

프로젝트 루트경로에 `.babelrc` 파일을 추가한 뒤 아래와 같이 코드를 추가해준다.

```jsx
{
  "presets": ["next/babel"],
  "plugins": ["babel-plugin-styled-components"]
}
```

(Next.js에서 바벨 설정을 추가할 때는 `next/babel` 프리셋을 꼭 추가해야 한다)

이렇게 설정을 마친 뒤, 서버를 재시작 하면

오류 코드가 뜨지 않고, 새로고침을 해도 스타일이 유지된다.
