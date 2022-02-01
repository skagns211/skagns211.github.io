---
layout: single
title: "TIL-63, TypeScript 기초"
---

TypeScript를 공부하며 설치 방법 및 기초 문법들을 정리해보고자 한다.

## 설치 및 세팅

터미널에서 `npm install -g typescript` 를 입력해 간단하게 설치한다.

기존 js 확장자가 아닌 ts 확장자를 사용하게 되고,

tsconfig.json 파일을 별도로 만들어 es 버전 등을 설정해준다.

## 문법

JavaScript에서는 `3 - '1'` 의 결과가 `2`로 나온다.

number와 string을 뺐는데, 정상적으로 나오는 것이다.

이렇게 유연하고 자유로운 JavaScript의 특징은 장점이 될 수도 있지만

협업과 복잡한 서비스를 만들 때는 예기치 못한 오류를 범할 수 있다.

TypeScript는 이런 부분을 엄격하게 지정해서 사용한다.

```tsx
let food: string = "apple";
```

위의 예제와 같이 변수를 선언하면서 : 뒤에 원하는 타입을 지정해준다.

string, number, boolean, null, undefined, bigint, [], {} 등을 지정할 수 있다.

만약,

```tsx
let food: string = 10;
```

위와 같이 입력한다면,

`Type 'number' is not assignable to type 'string'.` 와 같이 문자열 형식에

숫자를 넣을 수 없다는 식의 친절한 에러코드를 뱉어준다.

또는,

```tsx
let food: string | number = 10;
```

위와 같이 or 연산자 '|' 를 이용해 여러 타입을 지정해 줄 수도 있다.

타입 지정이 너무 길어지면 아래와 같이 type을 이용해 변수로 지정해 줄 수도 있다.

```tsx
type Name = string | number;
let food: Name = 10;
// 또는 let food: Name = "apple";
```

type 변수의 첫글자는 대문자로 하도록 한다.

```tsx
let people: string[] = ["NH", "DS"];
```

배열은 위와 같이 사용한다.

```tsx
let people: { name: string; age: number } = {
  name: "NH",
  age: 30,
};
```

객체는 위와 같이 사용한다,

boolean, null, undefined 등 여러 타입들도 위의 방식과 같이 사용할 수 있으며,

마찬가지로 함수에서도 사용할 수 있다.

```tsx
const func = (n: number) => {
  return n;
};

func(10);
```

위와 같이 인자의 타입을 지정할 수 있고,

```tsx
const func = (n: number): number => {
  return n;
};

func(10);
```

위와 같이 return 값의 타입도 지정할 수 있다.

```tsx
type Menu = [string, number];
let food: Menu = ["apple", 10];
```

위와 같이 배열에 tuple 타입 지정도 해줄 수 있다.

```tsx
type People = {
  name: string;
  age: number;
};
let kim: People = {
  name: "nh",
  age: 30,
};
```

객체에서는 위와 같이 사용하는데, 키:값이 많아질 때는

```tsx
type People = {
  [key: string]: string;
};
let kim = {
  name: "NH",
  email: "skagns211@gmail.com",
};
```

위와 같이 사용할 수 있다.

여기까지 기초 문법을 알아보았고, 이제 직접 코딩을 하면서

손가락과 마음속에 익히도록 하자.
