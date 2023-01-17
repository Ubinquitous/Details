## reducer

리듀서는 useReducer 훅과 똑같다. useReducer로 두 파라미터를 받아오면 두 값을 참고하여 새로운 상태를 반환한다.  
리듀서 코드는 useReducer와 같이 다음과 같다.

```js
const initState = {
  counter: 1,
  value: "",
};

function reducer(state = initState, action) {
  switch (action.type) {
    case INCREMENT: // 문자열 없이 사용
      return {
        counter: state.counter + 1,
        value: "값이 변경되었습니다!",
      };
    default:
      return state; // 해당하는 타입이 없을 경우 기본 상태 반환
  }
}
```

useReducer와의 차이점은 case문에 따로 문자열을 사용하지 않는다는 특징이 있다.

## dispatch

dispatch를 이용해 액션 객체를 파라미터로 넣어 호출할 수 있다.  
함수가 호출되면 스토어가 리듀서 함수를 실행시켜 새로운 상태를 만들어준다.
