---
layout: single
title: "Web Browser와 Node.js의 차이점"
---

## 먼저, 공통점

![](https://images.velog.io/images/skagns211/post/9cb22363-ca38-4758-b1fb-2d4b83465646/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-12%2002.50.03.png)

Web Browser (Chrome, Safari, FireFox 등) 는 자바스크립트 엔진을 기반으로 동작한다.

자바스크립트 엔진으로는 Chrome의 V8, Safari의 Webkit, FireFox의 Gecko 등이 있다.

Node.js는 이 중 Chrome의 V8을 기반으로 빌드 되었고, 당연히 자바스크립트 엔진을

기반으로 동작하기 때문에, Web Browser와 Node.js는 자바스크립트라는 프로그래밍 언어를

사용한다는 공통점이 있다.

## 차이점

1. 존재 목적과 사용상의 차이

   Web Browser는 HTML, CSS, JS를 실행해 UI를 나타내는게 존재 목적이고,

   Node.js는 자바스크립트를 Web Browser에서만 동작하는게 아닌 다른 환경에서도

   동작하게 해주는 런타임 환경으로, 주로 서버 개발 환경을 제공하는 것이 목적이다.

1. 사용 API의 차이
   Web Browser와 Node.js는 각자가 제공하는 내장 API가 있다.
   Web Browser는 DOM, BOM, Canvas, fetch 등의 API를 제공하고,
   Node.js는 서버 사이드 개발에 필요한 모듈, 파일 시스템, HTTP 등의 내장 API를 제공한다.
