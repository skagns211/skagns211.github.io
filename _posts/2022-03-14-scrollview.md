---
layout: single
title: "TIL-73, ScrollView"
---

React-Native에서 Scroll을 하는법을 알아보자.

RN은 View 컴포넌트로 구성되어있는데, 이 View는 ‘컴포넌트이기 때문에' 스크롤이 되지 않는다.

때문에 View가 아닌 스크롤이 가능한 컴포넌트를 사용해줘야 하는데,

그것이 바로 `ScrollView` 컴포넌트이다.

이 `ScrollView` 컴포넌트는 정말 많은 props를 가지고 있는데,

아주 유용한 것들이 많다. 공식 문서에서 확인하도록 하고, 몇가지만 알아보도록 하자.

## contentContainerStyle

가장 먼저, `ScrollView` 는 CSS를 적용할 때 다른 컴포넌트들처럼 style을 사용하면 안된다.

바로 `contentContainerStyle` 라는 props를 사용해야 한다.

```jsx
...
<ScrollView contentContainerStyle={style.이름}>
  ...
</ScrollView>
...
```

적용법은 간단한데, 기존 style={style.이름} 과 같은 방식에서 style 대신

`contentContainerStyle` 를 넣어준다.

## pagingEnabled

다음으로, 스크롤을 페이지화 시켜주는 props이다.

scrollView만 사용하면 페이지 구분 없이 주르륵 스크롤 되는데,

pagingEnabled를 사용하면 페이지가 나뉘어 분간하여 사용할 수 있다.

```jsx
...
<ScrollView pagingEnabled>
  ...
</ScrollView>
...
```

이 역시 적용법은 간단한데, `pagingEnabled` 속성을 넣어주면 된다.

기본값은 true이고, 사용하지 않으려면 false를 넣어준다.

이렇게 paging을 적용해줄 때, 각 휴대폰마다 딱 맞는 사이즈 (width, height)를 맞춰줘야 보기에 아름다운데,

이 때 유용하게 사용하는 API가 있다.

## Dimensions (API)

Dimensions라는 API인데, 해당 휴대폰 (장치)의 width, height의 값을 구해준다.

이를 이용해 각 휴대폰마다 딱 맞는 사이즈로 페이지를 작성할 수 있다.

```jsx
import { dimensions, ... } from "react-native";

const { width, height } = Dimensions.get("window");
console.log(width); // 장치의 width
console.log(height); // 장치의 height

...
// StyleSheet
page: {
  width, // width를 Dimensions의 width로 적용
}
```

이렇게 scroll을 구현해보면, 하단 또는 우측에 스크롤바 (indicator)가 보이는데,

보통은 거슬리는 부분이기 때문에 이 부분을 없애주기 위한 props도 존재한다.

**`showsHorizontalScrollIndicator`**

**`showsVerticalScrollIndicator`**

위의 두개인데, 말 그대로 HorizontalScroll과 VerticalScroll의 indicator 설정을 해준다.

true와 false를 전달해준다.

이처럼 ScrollView 컴포넌트에는 많은 props가 있는데,

이 중에서도 안드로이드, IOS 각각의 OS만 지원하는 props도 있으니 잘 살펴보자.
