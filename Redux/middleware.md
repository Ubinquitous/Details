## middleware

리덕스 미들웨어는 프로젝트 내에서 리덕스를 사용 중이고, 비동기 작업을 관리해야할 때에 쓰인다.  
액션을 디스패치했을 때 리듀서에서 처리하기 전에 지정된 작업들을 실행하는 중간자이다.

```
action -> middleware -> reducer -> store
```

리덕스 미들웨어는 전달받은 액션을 처리하기 전에 여러가지 작업을 남길 수 있다.  
콘솔에 정보를 기록하거나, 전달받은 액션을 취소하거나, 다른 액션을 추가로 디스패치 하는 등의 여러가지 작업이 가능하다.  
미들웨어를 직접 만들어보자.

```js
const loggerMiddleware = (store) => (next) => (action) => {
	console.group(action && action.type)
	console.log('prev', store.getState())
	console.log('action', action)
	next(action) // 다음 리듀서에게 전달
	console.log('next', store.getState())
	console.groupEnd()
}

export default loggerMiddleware
```

이제 createStore의 두 번째 파라미터에 이 미들웨어를 넘겨주면 작동한다.

```js
const store = createStore(reducer, applyMiddleware(loggerMiddleware))
```
