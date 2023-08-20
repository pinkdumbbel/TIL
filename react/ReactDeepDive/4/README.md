# React lifecycle

![](https://goidle.github.io/static/83aa2072b273a11e7b733979b439d735/ea64c/react-lifescycle.png)

---

### Render phase

React Element -> Fiber 노드로 확장된 자바스크립트 객체가 추가, 수정, 삭제 되는 단계 이며 VDom의 `재조정(reconciliation)`이 일어나는 단계 이다.

VDOM 재조정 프로세스

- **Work**를 **Scheduler**에 등록
  - Work: reconciler가 컴포넌트의 변경을 DOM에 마운트 하기 위해 수행하는 일
- **reconciler**가 담당 하며 Scheduler에 Work를 등록한다.

---

### Commit phase

**재조정이 완료된 VDOM을 실제 DOM에 마운트 lifecycle을 실행하는 단계**이며 브라우저 에서 페인트를 하는 단계는 아님

또한 이 단계에서 일관적인 화면의 업데이트를 위해 동기적으로 실행 됨

즉 비동기와 같은 순서에 변화를 주는 작업들은 render phase에서 처리하고 재조정이 끝난 VDOM을 DOM에 마운트 하는 작업은 동기적으로 처리 하면서 화면의 일관적인 변화를 보장한다.

이 단계는 동기적으로 실행 되기 때문에 중간에 브라우저가 화면을 페인트 할 수 없다.

---

### 브라우저 paint

Commit phase 의 작업들이 모두 끝나고 **콜스택이 비워진 후**에 페인트를 할 수 있다.
