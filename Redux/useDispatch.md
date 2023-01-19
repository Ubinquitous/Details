## useDispatch

useDispatch는 useSelector와 비슷하게, 액션을 디스패치하는 함수이다.

```js
import { useSelector } from "react-redux";

const CounterContainer = () => {
  const number = useSelector((state) => state.counter.number);
  const dispatch = useDispatch();

  const increase = useCallback(() => dispatch(increase()), [dispatch]);
  const decrease = useCallback(() => dispatch(decrease()), [dispatch]);

  return (
    <div>
      <h1>{number}</h1>
      <button onClick={increase}>+1</button>
      <button onClick={decrease}>-1</button>
    </div>
  );
};

export default CounterContainer;
```

다음과 같이 디스패치도 커넥트 함수 없이 쉽게 사용할 수 있다.  
버튼이 onClick될 때마다 함수가 재생성되기 때문에 useCallback을 사용하여 최적화 시키면 좋을 것 같다.

connect를 사용할 때에는 컨테이너 컴포넌트가 리렌더링될 때 props가 바뀌지 않으면 리렌더링이 방지된다.  
허나 useSelector를 사용할 때에는 최적화 작업이 이루어지지 않기 때문에, React.memo를 컨테이너 컴포넌트에 사용해야 한다.
