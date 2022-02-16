---
layout: single
title: "React에서 CORS 설정하기"
---

API를 이용해서 데이터를 가져오려고 시도할 때

```markdown
Access to XMLHttpRequest at 'http://xxx' from origin
'http://localhost:3000' has been blocked by CORS
policy: Response to preflight request doesn't
pass access control check: No 'Access-Control-Allow-Origin'
header is present on the requested resource.
```

위와 같은 오류를 자주 접한다.

package.json 파일에 proxy를 추가해주면 CORS 문제를 해결할 수 있다.

![](https://images.velog.io/images/skagns211/post/06627da7-4687-46f6-9b2c-bcfb3d6bdd3b/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-02-17%2001.38.18.png)

react 공식 문서에서는 위와 같이 설명되어 있다.

```jsx
// package.json
{
  ...,
  "proxy": "http://api.com",
}
```

위와 같이 proxy 항목에 원하는 API 주소를 입력한다.

이 때, 접속하고자 하는 API 주소의 루트 URL만 입력해준다.

실제로 http 요청을 전송하는 코드에서는

위의 루트 URL을 뺀 뒤의 부분만 작성한다.

## 예시

```jsx
{
  "proxy": "https://openapi.naver.com"
}
```

package.json에 위와 같이 naver openapi를 입력해줬다.

```jsx
const URL = "https://openapi.naver.com/v1/datalab/shopping";
const getDate = () => {
  axios.get(URL)
  .then((res) => {
  console.log(res)
}
```

axios를 이용해 http 요청을 보내는 기존 코드가 위와 같다면,

proxy를 추가해줬으므로

```jsx
const URL = "v1/datalab/shopping";
const getDate = () => {
  axios.get(URL)
  .then((res) => {
  console.log(res)
}
```

위와 같이 수정해준다.
