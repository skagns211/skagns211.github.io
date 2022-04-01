---
layout: single
title: "window에서 node version 변경시 exit status 1 Err"
---

window에서 nvm을 설치 한 뒤에 node까지 설치를 마무리 했고, nvm use로 node를 선택하려 하는데,

`exit status 1` 과 함께 외계어가 출력됐다.

또한, window에서는 node를 설치한 후에 nvm use로 버전을 선택해줘야

node사용이 정상적으로 이루어진다는 글을 봤기에,

`node -v` 를 입력해도 `‘node’ 용어가 cmdlet, 함수, 스크립트, 또는 실행할 수 있는 프로그램 이름으로 인식되지 않습니다.` 라는 에러를 뱉어냈다.

결국 nvm use 에러를 해결해야 했는데, 해결법은 아주 간단했다.

바로 terminal을 window 관리자 권한으로 실행하는 것이었다.

관리자 권한으로 실행한 뒤 nvm use ‘버전’ 을 입력하니 정상적으로 버전이 선택됐고,

node -v 을 입력하니 선택한 버전의 node가 출력됐다.
