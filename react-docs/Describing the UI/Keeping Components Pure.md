## 컴포넌트를 pure function만으로 작성하는 것은 코드 베이스가 커짐에 따라 발생할 수 있는 원인 모를 버그를 예방한다.

### **Purity: Components as formulas**

- pure function
  - It minds its own business.
  - **Same inputs, same output.**
- 리액트는 작성하는 모든 컴포넌트를 pure function으로 가정한다.
  - 즉, same inputs, **same JSX return**
  - **리액트는 오직 JSX만을 리턴하며, 렌더링 하기 전에 존재하는 객체나 변수를 변경하지 않는다!!**
  - 잘못된 예
    - 변수를 함수 외부에 선언하여 컴포넌트가 렌더링 될 때마다 다른 JSX를 반환
  - 수정
    - prop으로 전달함으로써 prop에 의존하도록 변경

### **Detecting impure calculations with StrictMode**

- 렌더링 하는 동안 읽을 수 있는(read-only) 3가지 inputs → `**props**` `**state**` **`context`**
- 무언가를 변경하고 싶으면 변수를 작성하는 것 대신 `**set state**`
- 리액트는 개발 환경에서 컴포넌트를 두번 호출하는 **‘Strict Mode’**를 제공하면서, 이 규칙을 깨는 컴포넌트를 발견할 수 있도록 돕는다.
  → 순수 함수는 계산만 하므로 어떤 것도 변경시키지 않는다!!
  - Strict Mode has no effect in production.

### **Local mutation: Your component’s little secret**

- **렌더링 하는 동안 방금 만든 변수와 객체를 변경하는 것은 괜찮다!**
  - 렌더링 중에 만들었기 때문에 컴포넌트 외부에서는 모른다 → **local mutation**

### **Where you *can* cause side effects**

- 그렇다면 사이드 이펙트는 어디에서 실행되야 하는 것일까? → **event handlers**
  - 이벤트 핸들러는 컴포넌트 내부에 있어도 렌더링 하는 동안 실행되지 않으므로 순수함수일 필요가 없다!
- 가능한 한, JSX 안에서 논리를 표현하라, 뭔가를 변경해야 하는 경우 이벤트 핸들러, 최후의 수단으로 useEffect를 사용! → 이것이 리액트 패러다임의 힘

---

**💡컴포넌트를 pure하게 유지해야 하는 이유, StrictMode를 통해 실수 방지**

### 참고

https://react.dev/learn/keeping-components-pure
