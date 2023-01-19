## Store 생성 및 사용하기

리액트에서 리덕스를 사용해보자. 먼저 리덕스를 프로젝트에 설치하자.

```
$ yarn add redux
$ yarn add react-redux
```

다 깔렸다면 본격적으로 리덕스를 사용해보자!

## 리듀서 함수 생성하기

먼저 리듀서 함수를 프로젝트에 생성해주어야 한다. 여기서는 카운터로 구현해볼 것이다.

```js
// counter.js

const INCREASE = "coutner/INCREASE"; // 타입을 미리 변수로 지정해줌
const DECREASE = "coutner/DECREASE";

// 액션 생성 함수
export const increase = () => ({ type: INCREASE });
export const decrease = () => ({ type: DECREASE });

// 초깃값 설정
const init = {
  number: 0,
};

// 리듀서 함수 생성
function counter(state = init, action) {
  switch (action.type) {
    case INCREASE:
      return {
        number: state.number + 1,
      };
    case DECREASE:
      return {
        number: state.number - 1,
      };
    default:
      return state;
  }
}

export default counter;
```

## 루트 리듀서 만들기

만약 프로젝트에서 리듀서 함수를 여러개 만들었다면,  
redux에서 지원하는 combineReducers 함수를 이용해 리듀서들을 묶어주어야 한다.

combineReducers 함수의 파라미터 안에 객체형식으로 리듀서 함수들을 넣어주자.  
파일 이름은 꼭 index.js로 설정해준 다음, modules 폴더에 넣자. import 구문이 명확해진다.

```js
import { combineReducers } from "redux";
import counter from "./counter";
// import ...그 외 여러가지 리듀서 함수들 불러오기

const reducer = combineReducers({
  counter,
  // ...그 외 여러가지 리듀서 함수들 넣어주기
});

export default reducer;
```

## 스토어 만들기

스토어를 생성해보자. 리액트의 src/index.js 파일에서 createStore 함수로 생성해줄 수 있다.  
createStore의 파라미터에는 우리가 combineReducers를 통해 묶어준 reducer를 넣자.  
또 Provider라는 컴포넌트로 App을 감싸주고, store를 props로 전달해주면 된다.

```js
...
import { createStore } from 'redux';
import reducer from './modules';
import { Provider } from 'react-redux';

const store = createStore(reducer); // store 생성하기

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
    <Provider store={store}> {/* Provider로 감싸주기 */}
        <App/>
    </Provider>
)
```

이렇게 전달해주면 프로젝트 내에서 어디서든 리덕스로 상태 관리를 할 수 있다!
