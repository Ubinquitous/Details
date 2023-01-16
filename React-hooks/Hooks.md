## React Hooks

리액트 훅은 최근에 도입된 기능으로 함수형 컴포넌트에서 할 수 없었던 다양한 작업을 할 수 있게 해준다.  
원래는 클래스형 컴포넌트에서만 상태 관리 및 라이프 사이클 메서드를 사용할 수 있었다. 이를 함수형 컴포넌트에서도  
사용할 수 있게 해주는 것이 React Hooks이다. 리액트 훅은 다양한 장점이 있다.

첫 번째로는 코드가 호환성이다. 리액트 훅은 호환성을 깨뜨리는 변화가 없으며, 일부 컴포넌트 안에서 선택적으로 사용할 수 있다.  
두 번째로는 라이프사이클이나 그 외 상태관리 등의 개념에 조금 더 직관적인 API를 제공한다는 것이다.

## 왜 만들어졌을까?

동기는 여러가지이다. 먼저 클래스형 컴포넌트 사이에서 상태 로직을 재사용하는 것이 어렵고,  
라이프사이클 메서드인 componentDidUpdate, componentDidMount, componentWillUnmount 등의 메서드는  
복잡하고 이해하기가 어려워 에러가 자주 발생했기 때문이다.

제일 치명적인 것은 자바스크립트의 트롤링이다! 자바스크립트의 클래스와 this의 작동방식은 다른 언어와는 다르게 이상하게  
작동하기 때문에 클래스에 어려움을 겪는 개발자들이 많아졌기 때문이다. 10일만에 만든 언어라 그런지 정상이 아니다...

이토록 여러가지 결함을 해결하기 위해 나온 함수형 컴포넌트와 리액트 훅에 대해서 자세히 알아보도록 하자!