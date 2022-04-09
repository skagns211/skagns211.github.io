---
layout: single
title: "TIL-78, react-hook-form"
---

어느 서비스던 입력 폼 (로그인, 회원가입 등 정보 입력)이 없는 서비스는 찾기 힘들다.

그만큼 많이 사용하는 form을 쉽게 관리하고, 생성하고, 유효성 검사까지 간편하게

할 수 있는 라이브러리가 react-hook-form이다.

당연히 아주 많은 API들이 있는데,

(useForm, useController, useFormContext, useWatch, useFormState, useFieldArray)

손에 익도록, 기억에 넣을 수 있도록 대표적인 예제만 정리해 보며 익혀보자.

## useForm

기본적으로 폼 양식을 쉽게 만들어줄 수 있는 hook이다.

여러가지 option들을 전달할 수 있다.

```jsx
useForm({
  mode: "onSubmit",
  reValidateMode: "onChange",
  defaultValues: {},
  resolver: undefined,
  context: undefined,
  criteriaMode: "firstError",
  shouldFocusError: true,
  shouldUnregister: false,
  shouldUseNativeValidation: false,
  delayError: undefined,
});
```

전체적인 부분과 자세한 설명은 공식문서 ([https://react-hook-form.com/api/useform](https://react-hook-form.com/api/useform))에 잘 나와있으니 참고하도록 하고, 몇가지만 알아보도록 하자.

`mode` : onChange, onBluer, onSubmit, onTouched, all 을 입력해줄 수 있다.

해당 옵션의 event가 발생할 경우, Validation을 진행한다.

`defaultvalues` : input의 default value를 설정한다. 밑에서 register를 배우겠지만,

register 이름과 원하는 value를 입력해준다.

```jsx
...
const { register } = useForm({
  defaultValues: {
    fisrt: "first input의 default value",
    second: "second input의 default value"
  },
});
...
<form>
  <input {...register("first")} />
  <input {...register("second")} />
</form>
...

```

## watch

입력된 value를 보여준다. 해당 method를 통해 조건부 렌더링 등을 구현할 때 유용하다.

```jsx
...
const result = watch("first");
console.log(result); // first input에 값 입력시, console에 값이 출력된다.
...
<form>
  <input {...register("first")} />
</form>
...
```

## handleSubmit

onSubmit 역할을 하는데, 엔터 입력시에도 submit이 되는 등 편리하게 구현이 되어있다.

input을 감싸는 form에서 적용해주면 된다.
