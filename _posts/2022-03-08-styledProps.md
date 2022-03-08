---
layout: single
title: "Styled-Components Props 전달"
---

Styled-Components의 장점 중에 한가지는

Props로 Data를 전달할 수 있다는 점이다.

styled가 말 그대로 component이기 때문에 가능한 일인데, 어떤식으로 전달되는지 알아보자.

```jsx
import React, { useState } from "react";
import styled from "styled-components";

const App = () => {
  const [isLogin, setIsLogin] = useState(false);

  retrun(<StyleApp isLogin={isLogin} />);
};

const StyleApp = styled.div`
  background-color: ${(props) => (props.isLogin ? "red" : "black")};
`;

export default App;
```

위와 같은 식으로 styled component에 props를 넘겨주고,

styled 작성 부분에서 ${(props) ⇒ props} 식으로 작성한다.
