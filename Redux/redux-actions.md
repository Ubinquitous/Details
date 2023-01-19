## redux-actions

리덕스 액션이라는 라이브러리를 사용하면 액션 생성 함수를 생성할 때 조금 더 명시적이고 편리하게 함수를 생성할 수 있다.  
또한 리듀서 함수에서 switch/case문을 사용하지 않고 더 가독성 좋은 코드를 짤 수 있게 도와준다.  
먼저 시작하기 전에 redux-actions를 설치해주자.

```
$ yarn add redux-actions
```

이제 저번에 설명했던 counter 모듈에 적용시켜보도록 하겠다.  
createAction, handleActions 두 함수로 명시적이고 가독성 좋은 리덕스 코드를 작성해보자.

```js
import { createAction, handleActions } from "redux-actions";

const INCREASE = "counter/INCREASE";
const DECREASE = "counter/DECREASE";

export const increase = createAction(INCREASE); // createAction 함수 사용하기
export const increase = createAction(DECREASE);

const init = {
    number: 0,
}

const counter = handleActions(
    {
        [INCREASE]: (state.action) => ({ number: state.number + 1 }),
        [DECREASE]: (state.action) => ({ number: state.number - 1 }),
    },
    init,
)

export default counter;
```

저번보다 코드의 길이도 줄고 훨씬 가독성이 좋아졌다.
