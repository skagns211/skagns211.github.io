---
layout: single
title: "TR-3, Clinet 및 Server Setting"
---

SR이 전부 끝나고, 팀원들이 Project Repository를 Fork하기 전에

Client 및 Server Setting를 진행했다.

# Client

Client에서는 Create-react-app을 이용해

React 개발 환경을 Setting하고 불필요한 React 기본 파일, 내용들을 전부 삭제해

깨끗한 상태로 만들어준 뒤,

앞으로 사용할 aws-sdk, axios, react-router-dom, redux, styled-components 등을

npm install 해줬다.

그 후 새로 사용하게 된 Redux를 위해 store, reducer, action을 다루는 폴더와 js파일을

생성해 줬고, 각각의 Page와 앞으로 조립하게 될 모든 Component들을 생성,

바로 사용할 수 있게 기본적인 내용들을 전부 채워넣었고,

.gitignore로 예외 파일들을 설정해줬다.

![](https://images.velog.io/images/skagns211/post/a1c556fc-6f30-4074-b6d3-7d4a95ed9043/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-03%2001.14.36.png)

# Server

Server에서는 express를 이용해 서버 개발 환경을 Setting했고,

npm start가 가능하게 index.js파일 등을 수정 작성해줬다.

그 후 앞으로 사용하게 될 axios, cors, dotenv, fs, jsonwebtoken, mysql, mysql2, sequelize, sequelize-cli를 dependencies로 install 해주고, nodemon을 devDependencies로 install 해줬다.

이렇게 npm install이 끝난 뒤에는

sequelize init을 통해 DB 연동을 준비했다.

각각 생성된 config, migrations, models, seeders등을 제외한 불필요한 파일들을 삭제해준 뒤,

config 폴더의 config.json을 config.js로 바꾸며 내용도 js 형식으로 수정한 뒤,

models 폴더의 index에서 config 경로/파일명을 수정해주고

.env 파일을 생성해 DB 연동에 필요한 정보들을 전부 담아주었다.

그 후 sequelize를 이용해 DB의 Table들을 Schema에 맞게 생성해주고,

migrate 해준 뒤에 models 폴더의 table 파일들에서 Schema 관계를 설정해줬다.

그 후 최소한의 Dummy 내용을 seed 해주는 걸로 DB 연동 작업은 마무리 했고,

routes 분기 작업을 해줬다.

routes 폴더에 API에 맞게 js파일들을 전부 생성해주고, index.js에서 router.use를 통해

각각을 분기 후 해당 경로의 js파일에서 다시 한번 HTTP Method와 path에 맞게

Controllers에 분기 해줬다.

Controllers의 js파일들에서 모든 Method와 path에

res.end()를 입력해 Postman에서의 Test가 가능하게 만들었고,

최종적으로 Postman으로 모든 요청을 보내 Test해본 결과

전부 정상적으로 응답을 보내는걸 확인한 걸 마지막으로 Route를 끝마쳤고,

.gitignore 파일을 작성함으로 Server Setting을 끝냈다.

![](https://images.velog.io/images/skagns211/post/958680f2-a70f-48a1-807e-20855603c285/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-12-03%2001.14.58.png)
