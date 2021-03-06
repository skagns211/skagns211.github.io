---
layout: single
title: "LocalHost 연결 끊기, git 파일 초기화"
---

![](https://images.velog.io/images/skagns211/post/69bcf75d-9c5a-41fe-9180-e3318df7fa08/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-10-15%2023.45.45.png)

npm run start를 통해 포트를 열려고 시도했는데

기본적으로 배정되는 3000번 포트가 이미 열려있기 때문에

대신 다른 포트를 열것이냐고 물어본다.

기존에 터미널이나 vsCode에서 진행하던 어떤 작업에서 포트를 열었는지 기억하면

해당 창으로 가서 `control + c` 를 누르면 포트를 종료할 수 있는데,

어떤 창에서 포트를 열었는지 기억이 안나면

`netstat -an` 을 입력해 네트워크 상태를 모니터링할 수 있다.

![](https://images.velog.io/images/skagns211/post/15a0450a-ed85-42fa-b43c-1be80e4d4358/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-10-15%2023.46.00.png)

3000번 포트가 열려있다..

실행중인 모든 노드 프로세스를 종료하는

`killall node` 를 입력해 종료해주고,

npm run start로 포트를 열어주면 정상적으로 열리는 것을 확인할 수 있다.

clone해온 git 파일을

처음의 상태로 되돌리는 명령어

`git restore .`
