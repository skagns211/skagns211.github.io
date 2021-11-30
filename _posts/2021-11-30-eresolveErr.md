---
layout: single
title: "[Err Handling] NPM install시 ERESOLVE 에러"
---

jwt-redis npm을 인스톨 하는데

```jsx
npm ERR! code ERESOLVE
npm ERR! ERESOLVE unable to resolve dependency tree
...
```

위와 같은 오류를 만났다.

npm intall jwt-redis 뒤에

**`-save --legacy-peer-deps` 를 붙여주니**

정상적으로 install 되었다.
