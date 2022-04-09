---
layout: single
title: "TIL-77, Styled-System"
---

기존에 컴포넌트 구조로 CSS 작업을 하는 Styled-Components를 사용했는데,

이번에 주니어로 입사 하면서, 팀에서 사용하는 Styled-System을 공부하게 됐다.

둘의 차이점은 무엇일까?? 그리고 Styled-System이란 무엇일까??

(사전준비)

```jsx
$ npm i styled-system styled-components
// styled-system과 styled-componets 설치
```

우선, Styled-Componets의 구조를 보자.

```jsx
import React from "react";
import styled from "styled-components";

const Test = () => {
  return <StyledTest>Hello</StyledTest>;
};

const StyledTest = styled.div`
  color: red;
  margin: auto;
  font-size: 10rem;
`;

export default Test;
```

import한 styled로 컴포넌트를 생성하고, 해당 선언문 내에서 CSS 스타일링을 해줬다.

이번에는 Styled-System의 구조를 보자.

```jsx
import React from "react";
import styled from "styled-components";
import { color } from "styled-system";

const Test = () => {
  return (
    <StyledTest color="red" m="auto" fontSize="10rem">
      Hello
    </StyledTest>
  );
};

const StyledTest = styled.div`
  ${color}
  ${space}
  ${typography}
`;

export default Test;
```

마찬가지로 styled를 import 하고 컴포넌트를 생성해주지만, 해당 선언문 내에서 CSS를

스타일링 하는게 아니고, 해당 선언문 내에서는 styled-system의 API만을 가져오고,

컴포넌트 태그 내에서 inline-style 방식으로 스타일링 한다.

이 때, styled는 “styled-componets”로부터 import해도 되지만,

@emotion/styled에서 import해서 사용할 수도 있다.

```jsx
import React from "react";
import styled from "@emotion/styled";
import { color } from "styled-system";

const Test = () => {
  return (
    <StyledTest color="red" m="auto" fontSize="10rem">
      Hello
    </StyledTest>
  );
};

const StyledTest = styled("div")(color, space, typography);
export default Test;
```

다만, 컴포넌트 생성에서 styled를 활용하는 방식이 다르니 유의하자.

Styled-Componets와 Styled-System의 차이점을 알아봤는데,

사실 무엇이 더 좋고 무엇이 더 나쁘다고 말 할 수 있을것 같지는 않다.

일을 진행하면서, 협업을 하면서, 필요에 의해 어떤 방식이 편리한지

합의 후에 편리하게 사용하면 될 것 같다. (뇌피셜)
