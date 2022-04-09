---
layout: single
title: "TIL-76, interface와 type"
---

만약에, 아래와 같이

```tsx
const car = (): { name: string, price: number, discount: boolean } => {
  const bmw = {
    name: '520i',
    price: 60000000,
    discount: true,
  };
  return bmw;
};
```

함수 `car` 의 리턴값이 object이고, 해당 object들의 값의 타입들을 정해줬을 때,

코드가 한없이 길어지고 복잡해지게 된다.

이럴때는 Type 또는 interface를 사용하면 코드가 간결하고 짧아지게 된다.

```tsx
// type을 사용
type Car = {
  name: string;
  price: number;
  discount: boolean;
};

// interface를 사용
interface Car = {
  name : string;
  price: number;
  discount: boolean;
}

const car = (): Car => {
  const bmw = {
    name: "520i",
    price: 60000000,
    discount: true,
  };
  return bmw;
};
```

위와 같이 변수를 선언해주는 것처럼 type 또는 interface를 이용해 Type을 지정해준다.

그렇다면 type과 interface의 차이점은 무엇일까?

바로, 타입을 확장하는 방법에 차이가 있다.

```tsx
interface type1 {
  age: number
}

interface type2 extends type1 {
  name: string
}

const ironMan: type2 = {
  age: 40,
  name: 'tony stark'
};
```

위와 같이, interface에서는 type2에 type1을 합쳐 확장시키는 방법으로 extends를 사용한다.

(마치 class와 같다)

또한,

```tsx
interface type {
  age: number
}

interface type {
  name: string
}

const ironMan: type = {
  age: 40,
  name: 'tony stark'
};
```

같은 이름으로 정의해 타입을 확장시킬 수도 있다.

```tsx
type type1 = {
  age: number
};

type type2 = type1 & {
  name: string
};

const ironMan: type2 = {
  age: 40,
  name: 'tony stark'
};
```

반면, type에서는 위와 같이 &을 사용하고,

같은 이름으로 정의하게 되면 ‘type이 중복되었다' 라는 에러가 뜬다