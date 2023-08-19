# VDom

> VDom은 공식문서에 따르면 프로그래밍 컨셉이며 메모리 상에 UI관련 정보를 저장하고 renderer패키지의 모듈에 의해 실제 Dom과 Sync를 맞춤 이 과정을 재조정(reconcilation) 이라고 하며 reconciler 패키지가 관여한다.

---

![](https://goidle.github.io/static/258b43ce623e7b6340fc6aed969199ed/374ac/vDOM.png)

VDom은 더블 버퍼링 구조로 되어 있으며 current트리 와 workInProgress트리로 구성 되어 있다.

더블 버퍼링 구조를 갖는 이유는 workInProgress에서 작업을 하다가도 언제든지 노드들을 삭제 하고 처음부터 다시 시작 할 수 있으며 또한 렌더링을 중지 했다가 다시 시작 할 수 있는등 우선순위에 맞게 유연하게 대처 하기 위함 이다.

---

### Root Node

Current 트리와 연결되어 있는 VDom 트리중 최상위 노드 이다.
흔히 사용되는 리액트 프로젝트 생성 템플릿인 CRA 코드를 통해 확인해 보면

```typescript
//index.tsx
//...import

/*
public/index.html 내부에 선언 된 <div id='root'></div>를 가져와 Root Node로 생성
*/
const root = ReactDOM.createRoot(
  document.getElementById("root") as HTMLElement
);

/*
생성된 Root Node에 실제 React 컴포넌트를 마운트
*/
root.render(<App />);
```

위와 같이 Root Node를 생성하고 React 컴포넌트를 마운트 하는것을 볼 수 있다.

---

### current 트리

Root Node 즉 실제 Dom 에 마운트 되어있는 Fiber노드 들로 이루어진 트리이다.

---

### workInProgress 트리

`render phase` 에서 Dom의 추가, 수정, 삭제 되는 작업들 즉 재조정(reconciliation)이 이루어 지고 있는 Fiber 노드들로 이루어진 트리이다.

해당 트리의 생성은 current트리를 자가 복제로 생성되며 이때 각각의 Fiber노드(자바스크립트 객체) 들은 `alternater`이라는 프로퍼티로 서로를 참조 하고 있는 구조이다.

재조정이 끝나고 `commit phase`를 지나 실제 Dom에 마운트 되면 **Root Node의 참조**가 **workInProgress트리** 로 변경되면서 **current트리** 가 되고 이 **current트리**에서 자가 복제를 통해 새로운 **workInProgress트리**를 생성함

위 과정을 반복적으로 수행

---

### VDom노드(Fiber)

자식 노드를 `child`프로퍼티로 참조 하며 `first child` 즉 첫번째 자식 노드만 참조 하며 나머지 같은 level에 있는 노드들은 `sibling`프로퍼티를 통해 참조
