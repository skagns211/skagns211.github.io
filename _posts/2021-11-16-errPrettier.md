---
layout: single
title: "[Err Handling] Prettier 설정 오류"
---

오류라고 보기는 어렵지만

협업을 할때 코드 스타일을 통일하기 위한

Prettier가 제대로 먹지 않는것은 문제가 되기 때문에

Err handling으로 작성해보고자 한다.

나를 포함한 모든 팀원들이 Prettier 확장프로그램을 설치했고,

Prettier의 Default값을 사용하기로 했는데

나만 다른 팀원들과 다른 방식으로 Document가 Formatting이 되었다.

Prettier의 설정들도 전부 동일하고,

다른 부분을 찾아보았으나, 모두 동일했다.

해결한 방법은

vsCode 상에서 `command + shift + P` 를 누르고 `format document` 를 입력하면

문서서식 프로그램이 나온다.

해당 칸을 클릭하면, 현재 설정되어 있는 기본 formatter가 나와있는데,

나같은 경우는 해당 formatter가 vsCode의 Default formatter로 설정되어 있었다.

때문에 pretteir를 Default로 설정해줬고,

다른 팀원들과 동일하게 Formatting 되는걸 확인할 수 있었다.