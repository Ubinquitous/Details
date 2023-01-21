## redux-saga

리덕스 사가 또한 redux-thunk처럼 비동기 작업을 관리하는 라이브러리이다.  
기존 요청을 취소해야 하거나, 액션이 발생할 때 다른 액션을 발생시키거나, 또  
리덕스와 관계없는 코드를 실행하거나 웹소켓을 사용할 때, 재요청을 할 때 등등의 상황에서 redux-thunk보다  
리덕스 사가가 더 유용하다.

리덕스 사가는 제네레이터 함수를 이용한 디스패치하는 액션을 모니터링하여 필요한 작업을 수행할 수 있는 미들웨어이다.  
리덕스 사가를 통해서 비동기식 카운터를 만들어보자.

설치 방법은 다음과 같다.

```
$ yarn add redux-saga
```

## 비동기 카운터 만들기

먼저 액션 타입을 선언하고, 액션 생성 함수도 만든 다음, 제네레이터 함수를 만들자.  
이 제네레이터 함수를 '사가'라고 부른다.

```js
import { delay, put, takeEvery, takeLatest } from 'redux-sage/effects'

const INCREASE_ASYNC = 'counter/INCREASE_ASYNC'
const DECREASE_ASYNC = 'counter/DECREASE_ASYNC'

export const increaseAsync = createAction(INCREASE_ASYNC, () => undefined)
export const decreaseAsync = createAction(DECREASE_ASYNC, () => undefined)

function* increaseSaga() {
	yield delay(1000) // 1초 기다리기
	yield put(increase()) // 특정 액션을 디스패치한다.
}

function* decreaseSaga() {
	yield delay(1000) // 1초 기다리기
	yield put(decrease()) // 특정 액션을 디스패치한다.
}

export function* counterSaga() {
	yield takeEvery(INCREASE_ASYNC, increaseSaga) // 들어오는 모든 액션에 대해 특정 작업 처리
	yield takeLatest(DECREASE_ASYNC, decreaseSaga) // 마지막으로 실행된 작업만 수행
}
const init = 0

const counter = handleActions(
	{
		[INCREASE]: (state) => state + 1,
		[DECREASE]: (state) => state - 1,
	},
	init
)

export default counter
```

또 modules/index.js에서 루트 사가를 만들어주자.

```js
export function* rootSaga() {
	yield all([counterSaga()]) // 여러 사가를 합쳐주는 역할
}
```

그 다음 리액트의 index.js에서 redux-saga 미들웨어를 apply해주자.

```js
const sagaMiddleware = createSagaMiddleware()

const store = createStore(reducer, applyMiddleware(sageMiddleware))
sagaMiddleware.run(rootSaga)
```

이제 +1 카운터를 빠르게 여러 번 눌러보면, INCREASE_ASYNC 액션이 여러 번 디스패치 된 다음,  
1초 후 INCREASE 액션을 발생시켜준다.

-1 카운터를 빠르게 여러 번 눌러보면, 단 한 번만 디스패치된다. takeLatest는 여러 액션이 중첩되어있을 때,  
기존 것들을 무시하고 가장 마지막 액션만 처리하기 때문이다.
