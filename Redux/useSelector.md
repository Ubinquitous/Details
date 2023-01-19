## useSelector

useSelector는 connect 함수를 사용하지 않고 상태를 조회할 수 있게 도와주는 훅이다.

사용법은 정말 간단하다.

```js
import { useSelector } from "react-redux";

const CounterContainer = () => {
  const number = useSelector((state) => state.counter.number);
  return <h1>{number}</h1>;
};

export default CounterContainer;
```

이런 식으로 connect 함수를 사용하지 않고 정말 편하게 상태를 불러올 수 있다.
