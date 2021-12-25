---
layout: single
title: "[Err Handling] _blank 사용시 security risk"
---

React를 Start 하면,

Console창에 노란 글씨로

**`Using target=_blank without rel=noopener noreferrer is a security risk`**

이런 오류 (또는 경고)가 계속해서 떴다.

렌더될 때 마다 이런 오류가 Console에 쌓이면 좋을건 없어보이기에,

지워보기로 했다.

이 오류는 link, a태그를 새 창으로 띄워주는 `target=_black` 속성을 단독으로 사용했을 때

A사이트에서 해당 링크를 눌러 새 창으로 B사이트를 띄워주고,

B사이트를 종료하고 다시 A사이트에 돌아올 때 A사이트 처럼 보이는 피싱 사이트로 변하게 만드는

Tabnabbing 이라는 피싱에 당할 수 있기 때문에 띄워주는 오류이다.

`target="_black"` 속성을 사용한 link, a태그 등에

`rel="noopener noreferrer"` 속성을 추가하면 오류가 사라진다.
