---
layout: single
title: "[Err Handling] Mixed Content 에러"
---

## 어떤 에러?

AWS를 이용해 프로젝트 배포를 진행하던 중,

CloudFront와 S3를 이용한 Client https 배포 및 도메인 연결은 정상적으로

완료 되었는데, 서버와의 통신을 시도할 시

개발자도구의 콘솔에

```jsx
Mixed Content: The page at 'https://주소' was loaded over HTTPS,
but requested an insecure script
'http://주소'.
This request has been blocked; the content must be served over HTTPS.
```

위와 같은 Mixed Content 에러가 떴다.

원인이 무엇인고 하니,

https와 http가 함께 사용된 것이 원인이었다.

하지만 그 중에서도,

https 방식을 사용하는 클라이언트에서 http 방식으로 서버에 요청을 보내는것이 문제였다.

보안이 되지 않은 http에서 보안이 강화된 https로 요청을 보내는 것은 문제가 안되지만,

보안이 강화된 https에서 보안이 되지 않은 http의 정보를 요청 한다면

보안은 무용지물이 되는 것이기 때문에

에러가 발생하는 것이다.

## 어떻게 해결?

나같은 경우는

클라이언트의 axios 요청의 url을 https로 바꾸고,

server 역시 https 방식으로 run을 해주니

정상적으로 작동하게 됐다.
