## containers

컨테이너 컴포넌트를 만들어보자.  
컨테이너는 상태 관리를 할 리덕스의 함수들을 정의해놓고, 사용할 컴포넌트에게  
props로 상태값과 함수들을 넘겨주어 관리하는 기능을 한다. 간단하니 바로 코드를 보자.

```js
import { bindActionCreators } from "redux";
import { connect } from "react-redux";
import Counter from "../components/Counter"; // 따로 생성한 컴포넌트
import { increase, decrease } from "../modules/counter"; // 리듀서 함수

const CounterContainer = ({ number, increase, decrease }) => {
  return <Counter num={number} onIncrease={increase} onDecrease={decrease} />;
};

export default connect(
  (state) => ({
    // connect 함수 파라미터에 상태값을 넘겨줌
    number: state.counter.number,
  }),
  (dispatch) =>
    bindActionCreators(
      {
        increase,
        decrease,
      },
      dispatch
    )
)(CounterContainer);
```

이후 CounterContainer를 사용을 원하는 곳에 컴포넌트로 import하면 잘 작동한다.  
bindActionCreators는 액션 함수를 쉽게 넘겨주게 도와주는 함수이다.  
저 자리에 바로 객체 형태로 액션 함수를 넣어주면 더욱 쉬운 문법으로 리덕스를 사용할 수 있다.

```js
...
state => ({
    number: state.counter.number,
}),
{
    increase,
    decrease,
},
...
```
