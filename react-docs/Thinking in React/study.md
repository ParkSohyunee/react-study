https://react.dev/learn/thinking-in-react

## 리액트에서 UI를 구현하기 위한 5가지 단계

### 1. UI를 컴포넌트 계층으로 나누기

- 프로그래밍 관점에서 **단일 책임 원칙** 기준으로 나누기
  - **컴포넌트는 한가지 일만 한다.**
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/77c4d16f-f557-4138-8798-29e914034d36/14d1e2ef-797b-4596-ab99-5d9be80e7c1d/Untitled.png)

### 2. 정적인 리액트 컴포넌트 UI 만들기

- 상호작용이 없는 컴포넌트 만들기 → `재사용가능한 컴포넌트`와 `props`를 사용, **state는 미사용**

### 3. **Find the minimal but complete representation of UI state**

- 인터랙티브한 UI를 만들기 위해 사용자가 **데이터를 변경**할 수 있게 만들어야 함 → state
- state를 구조화 하는 가장 중요한 원칙은 [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)하게 유지하는 것
  - 상태를 최소한으로 표현하기 ex. 장바구니 데이터만 저장하고 순서는 length 프로퍼티로 구함(저장x)
- **state vs props**
  - `props`는 함수에 전달하는 인수와 같다.
  - `state`는 컴포넌트의 메모리와 같다. 컴포넌트는 정보를 추적하고, 상호작용에 따라 변경할 수 있다.
  - 시간이 지나도 변함없이 유지되나요? → not state
  - 부모로부터 props로 전달되나요? → not state
  - 컴포넌트 안에서 기존 state, props 등으로 값을 계산할 수 있나요? → not state

### 4. **Identify where your state should live**

- **state 변경을 어떤 컴포넌트에서 해야할 지**
- **state를 어디서 소유해야할 지**
- **리액트는 단방향 데이터 흐름(one-way data flow)**
  - state를 사용하는 컴포넌트를 파악한다.
  - 이들의 공통 부모 컴포넌트를 찾는다.
  - state를 어디에 둬야할지 결정한다.
- \*\*`useState hook`을 사용해서 컴포넌트에 state를 추가

### 5. 역방향 데이터 흐름 추가

- state를 사용하는 컴포넌트에서 state 변화가 발생했을 때, state를 소유하는 컴포넌트의 데이터를 변경해 줘야 한다. → inverse data flow
  - **setState를 전달해서 업데이트!**

---

**💡단일책임 원칙 기준으로 컴포넌트 나누기, 데이터를 변경하는 것은 state이고, dry하게 유지하기**
