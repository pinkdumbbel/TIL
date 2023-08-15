# React의 주요 패키지들

> React라는 거대한 라이브러리를 구성하고 있는 핵심 패키지 들에 대해 간단하게 어떤 역할을 하는지 알아보기

---

### react 코어 패키지

컴포넌트의 정의와 관련된 패키지로 대표적인 함수인 createElement 함수가 정의 되어 있으며 또한 React를 사용하는 개발자에게 다른 패키지의 모듈을 제공해주는 다리 역할을 함
이 패키지는 다른 패키지와 의존성을 갖고 있지 않기 때문에 다른 플랫폼(브라우저, 모바일)에 올려서 사용 할 수 있음

---

### renderer 패키지

react-dom(브라우저), react-native-renderer(모바일) 등 호스트 환경(플랫폼) 에 의존적인 패키지 이며 호스트(플랫폼)와 react를 연결하는 역할을 함

reconciler 패키지 와 legacy-events 패키지에 의존성을 가지고 있음

---

### event(legacy-events) 패키지

SyntheticEvent라는 명칭으로 내부적으로 개발된 이벤트 시스템으로 개발자의 호스트 환경에서 의 event를 wrapping 하여 추가적인 제어 및 기능을 수행 할 수 있도록 하는 역할을 함

---

### scheduler 패키지

리액트는 Task를 비동기적으로 실행함 이 Task의 실행 타이밍을 알고 있는 패키지

- Task: 예를들어 react에서 useState훅을 사용하여 상태를 업데이트 하는 setState 함수를 호출후에 바로 다음 라인에서 해당 state를 확인하면 이전 값이 담겨있는 것이 확인 되는데 이는 리액트가 상태 변경과 같은 Task들을 비동기로 실행 한다는 것을 확인 할 수 있다.

---

### reconciler

리액트의 핵심 패키지 이며 Fiber 아키텍처를 사용하여 VDom을 재조정 하는 역할을 하는 패키지

---

### 헷갈리는 용어 정의

- 렌더링: 컴포넌트를 호출하여 반한된 react element를 VDom(fiber)에 적용(재조정) 하는 과정

* 마운트: 렌더링 과정을 끝마친 후 VDom을 실제 Dom에 적용하는 과정

- 페인트: 마운트 된 Dom을 브라우저가 그리는 과정

* react element: 컴포넌트 호출시 반환된 컴포넌트 의 정보를 담은 객체로 `type`, `key`, `props`,`ref` 등의 프로퍼티를 갖고 있음

- fiber: VDom의 노드 객체 이며 컴포넌트를 호출하여 리턴받은 react element 객체를 Dom에 반영하기 위해 확장 시킨 객체이며 react elemet의 프로퍼티 외에 `컴포넌트의 상태`,`life cycle`, `hook` 이 관리됨
