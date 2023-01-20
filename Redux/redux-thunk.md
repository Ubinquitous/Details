## redux-thunk

redux-thunk는 프로젝트 내에서 리덕스를 사용할 때 사용하는 비동기 작업 처리 라이브러리이다.  
thunk 함수를 만들어서 디스패치할 수 있게 도와준다. 설치방법은 다음과 같다.

```
$ yarn add redux-thunk
```

index.js 파일, 즉 스토어를 생성하는 파일에 applyMiddleware에 thunk를 추가하자.

```js
...
import thunk from 'redux-thunk';

...

const store = createStore(reducer, applyMiddleware(thunk))

const root = ...
```

redux-thunk는 액션 생성 함수에서 함수를 반환해준다. 비동기 함수를 만들어주어 변경시키면,  
처음 디스패치될 때 액션이 함수 형태로 디스패치가 된 다음 비동기 처리 후 액션 객체가 반환된다.

## axios 비동기 작업 처리하기

먼저 액션 타입을 한 요청 당 3개를 만들어야 한다.  
새로운 리듀서를 만들어 비동기 작업을 처리해보자.

```js
const GET_USER = 'sample/GET_USER'
const GET_USER_SUCCESS = 'sample/GET_USER_SUCCESS'
const GET_USER_FAILURE = 'sample/GET_USER_FAILURE'

export const getUser = (id) => async (dispatch) => {
	dispatch({ type: GET_USER })
	try {
		const res = await // 불러올 api
		dispatch({
			type: GET_USER_SUCCESS, // success type 액션 실행
			payload: res.data,
		})
	} catch (err) {
		dispatch({
			type: GET_USER_FAILURE, // failure type 액션 실행
			payload: err,
			error: true,
		})
		throw err
	}
}

export default sample = handleAction({
	[GET_USER]: (state) => ({
		...state,
		loading: {
			...state.loading,
			GET_USER: true,
		},
	}),
	[GET_USER_SUCCESS]: (state, action) => ({
		...state,
		loading: {
			...state.loading,
			GET_USER: false,
		},
		user: action.payload,
	}),
	[GET_USER_FAILURE]: (state) => ({
		...state,
		loading: {
			...state.loading,
			GET_USER: false,
		},
	}),
	init,
})
```

이제 API 요청을 사용해보면 비동기 작업으로 잘 처리된다는 것을 알 수 있다.
