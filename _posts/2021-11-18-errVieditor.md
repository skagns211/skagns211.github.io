---
layout: single
title: "[Err Handling] Vi에디터 swp파일 오류"
---

'vi' 에디터 사용시

```jsx
E325: ATTENTION
Found a swap file by the name "<파일경로 및 파일명>"
```

위와 같은 오류를 만났다.

nano 에디만 사용하다가, 어쩌다 vi 에디터로 commit을 하게 됐는데

사용 미숙으로 인해서 작업중 비정상적으로 에디터가 종료된 후로

vi에디터로 다시 commit 하려고 했더니 만난 오류이다.

해당 오류를 해결하기 위해서 오류에 나와있는 대로 swp 파일을 찾아내어

삭제하였다.

우선은 .git폴더로 이동을 해주고,

swp파일은 숨김파일로 되어있기 때문에

`ls -a` 를 이용해 모든 파일을 조회해보면

아래와 같은 swp파일이 나온다

rm .COMMIT_EDITMSG.swp

해당 파일을 삭제한 후 다시 vi에디터로 commit을 시도하면

정상적으로 에디터에 들어갈 수 있다.

제대로 저장한 뒤 나오면 문제없이 완료가 된다.
