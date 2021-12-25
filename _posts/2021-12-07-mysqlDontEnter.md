---
layout: single
title: "[Err Handling] mysql  접속 불가"
---

## 어떤 에러?

새로운 PC에서 개발환경을 셋팅하고,

mysql을 실행하려고 하는데,

```jsx
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)
```

위와 같은 2002 에러가 떴다.

서버에 접속을 할 수 없다는데, 원인이 무엇인고 하니

DB Server가 열려있지 않은 것이었다.

설치는 했지만 실행은 되지 않았기 떄문에

DB Server를 오픈해준다.

## 어떻게 해결?

linux는 service를 이용하고,

나는 Mac을 사용하기 때문에

```jsx
$ mysql.server start
```

위와 같이 Start를 해준다.

이 후 다시 mysql을 실행하면 정상적으로 실행이 된다.
