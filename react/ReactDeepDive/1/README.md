# Fiber vs Stack

> React 16v 부터 도입된 `Fiber` 아키텍처 와 이전 버전에서 사용된 `Stack` 아키텍처 의 차이를 알아보며 왜 React에서 Fiber라는 아키텍처를 도입했는지 알아보기

### Stack

![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20221219100314/stack.drawio2.png)

**후입선출(Last In First Out)** 의 특징을 가진 아키텍처로 가장 마지막에 삽입된 노드가 가장 먼저 삭제 되는 구조를 갖고 있다.

---

### Fiber

![](https://blog.openreplay.com/images/react-fiber-explained/images/image02.png)

Stack과 달리 **삽입된 노드의 순서와 상관없이** 노드를 삭제 할 수 있는 아키텍처

---

### React는 왜 Fiber 아키텍처를 도입했을까?

기존의 Stack 자료구조를 사용하게 되면 노드의 삭제 순서가 정해져 있기 때문에 렌더링 작업에서 유연하게 대응을 할 수 없다.

따라서 최근 18v에서 새로 나온 훅인 **useTransition** 과 같은 동시성 렌더링 작업을 처리 하기 위해 Fiber 아키텍처를 도입함
