---
layout: single
title: "TIL-79, redux-toolkit"
---

기존에 사용해봤던 redux에 이어 redux-toolkit을 공부해보자.

redux-toolkit은 redux 팀에서 공식적으로 지원하는 라이브러리다.

기존에 redux의 불편해던 점들을 보완하기 위해 여러개의 라이브러리를 사용했는데,

toolkit에서 그런 라이브러리들의 기본적인 기능들을 모두 지원한다.

(사전 준비)

```jsx
$ npm i @reduxjs/toolkit react-redux
```

@reduxjs/toolkit과 react-redux를 설치한다

## Store 생성

```jsx
// app/store.js
import { configureStore } from "@reduxjs/toolkit";

export const store = configureStore({
  reducer: {},
});
```

기본적인 store생성 폼이다.

configureStore를 import해온 뒤, reducer를 구성하면 된다.

## Store 연결

```jsx
// index.js
import React from 'react';
import ReactDom from 'react-dom';
import App from './App';
import { store } from './app/store';
import { Provider } from 'react-redux';

ReactDom.render(
  <Provider store={store}>
    <App />
  </Provider>
  document.getElementById('root')
)
```

App을 Provider로 감싸주고, store를 연결한다.

## 리듀서 및 액션

```jsx
import { createSlice } from "@reduxjs/toolkit";

const initialState = {
  value: 0,
};

const counterSlice = createSlice({
  name: "counter",
  initialState,
  reducers: {
    increment(state) {
      state.value++;
    },
    decrement(state) {
      state.value--;
    },
    incrementByAmount(state, action) {
      state.value += action.payload;
    },
    decrementByAmount(state, action) {
      state.value -= action.payload;
    },
  },
});

/* button을 클릭한 뒤 1초 뒤에 counter가 증가하는 함수
export const incrementAsync = (amount) => (dispatch) => {
  setTimeout(() => {
    dispatch(incrementByAmount(amount));
  }, 1000);
};

export const decrementAsync = (amount) => (dispatch) => {
  setTimeout(() => {
    dispatch(decrementByAmount(amount));
  }, 1000);
};
*/

export const { increment, decrement, incrementByAmount } = counterSlice.actions;
export default counterSlice.reducer;
```

createSlice를 이용해 초기 state, reducer, action등을 생성한다.

## Store에 리듀서 추가

```jsx
// app/store.js
import { configureStore } from "@reduxjs/toolkit";
import counterReducer from "./reducer경로";

export const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});
```

처음 생성했던 Store에 방금 생성한 리듀서를 추가해준다.

counter로 설정했기 때문에 state.counter로 상태를 참조할 수 있다.

## 상태 사용

```jsx
// Counter.js

import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { decrement, increment, incrementByAmount } from './reducer경로';

const Counter = () => {
  const count = useSelector((state) => state.counter.value);
  const dispatch = useDispatch();

  return (
    <div>
      <div>
        <button
          aria-label="증가"
          onClick={() => dispath(increment())}
        >
          증가
        </button>
        <button
          aria-label="감소"
          onClick={() => dispath(dncrement())}
        >
          감소
        </button>
      <div>
    </div>
  )
}
```

기존 redux 사용과 동일하게 useSelector와 dispatch를 사용한다.

reducer에 만들어 놓은 incrementByAmount와 decrementByAmount 사용은

이전에 배운 `react-hook-form` 과 `styled-system` 을 이용해 만들어봤다.

그리고 추가적으로 incrementAsync와 decrementAsync를 만들어

버튼을 클릭하고 1초 뒤에 증가되도록 만들어 보았다.
