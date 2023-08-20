# Fiber vs Stack

> React 16v 부터 도입된 `Fiber` 아키텍처 와 이전 버전에서 사용된 `Stack` 아키텍처 의 차이를 알아보며 왜 React에서 Fiber라는 아키텍처를 도입했는지 알아보기

### Stack

![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20221219100314/stack.drawio2.png)

**후입선출(Last In First Out)** 의 특징을 가진 아키텍처로 가장 마지막에 삽입된 노드가 가장 먼저 삭제 되는 구조를 갖고 있다.

---

### Fiber

![](https://blog.openreplay.com/images/react-fiber-explained/images/image02.png)

Stack과 달리 **삽입된 노드의 순서와 상관없이** 노드를 삭제 할 수 있는 아키텍처
때문에 VDOM을 재조정 하는 과정을 abort, stop, restart 할 수 있게 됨

```typescript
function FiberNode(tag, pendingProps, key) {
  // Instance
  this.tag = tag; // fiber의 종류를 나타냄
  this.key = key;
  this.type = null; // 추후에 React element의 type을 저장
  this.stateNode = null; // 호스트 컴포넌트에 대응되는 HTML element를 저장

  // Fiber
  this.return = null; // 부모 fiber
  this.child = null; // 자식 fiber
  this.sibling = null; // 형제 fiber
  this.index = 0; // 형제들 사이에서의 자신의 위치

  this.pendingProps = pendingProps; // workInProgress는 아직 작업이 끝난 상태가 아니므로 props를 pending으로 관리
  this.memoizedProps = null; // Render phase가 끝나면 pendingProps는 memoizedProps로 관리
  this.updateQueue = null; // 컴포넌트 종류에 따라 element의 변경점 또는 라이프사이클을 저장
  this.memoizedState = null; // 함수형 컴포넌트는 훅을 통해 상태를 관리하므로 hook 리스트가 저장된다.

  // Effects
  this.effectTag = NoEffect; // fiber가 가지고 있는 side effect를 기록
  this.nextEffect = null; // side effect list
  this.firstEffect = null; // side effect list
  this.lastEffect = null; // side effect list

  this.expirationTime = NoWork; // 컴포넌트 업데이트 발생 시간을 기록
  this.childExpirationTime = NoWork; // 서브 트리에서 업데이트가 발생할 경우 기록

  this.alternate = null; // 반대편 fiber를 참조
}
```

---

### React는 왜 Fiber 아키텍처를 도입했을까?

기존의 Stack 자료구조를 사용하게 되면 노드의 삭제 순서가 정해져 있기 때문에 렌더링 작업에서 유연하게 대응을 할 수 없다.

따라서 최근 18v에서 새로 나온 훅인 **useTransition** 과 같은 동시성 렌더링 작업을 처리 하기 위해 Fiber 아키텍처를 도입함
