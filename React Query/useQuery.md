## useQuery

useQuery는 데이터를 get 하기 위한 api다.  
첫번째 파라미터로 고유한 키가 들어가고, 두번째 파라미터로 api 호출 함수가 들어간다.  
고유 키를 다른 컴포넌트에서도 사용하여 호출할 수 있기 때문에, 모듈화하여 사용이 가능하다.  
비동기로 작동하며, enabled라는 키워드를 통해 동기적으로 작동시킬 수 있다.

```js
const Hello = () => {
	const { isLoading, isError, data, error } = useQuery('hello', () => axios.get(''), {
		refetchOnWindowFocus: false, // 사용자가 해당 창을 재방문 했을 때 재실행 여부
		retry: 0, // 실패시 재호출 횟수
		onSuccess: (data) => {
			console.log(data)
		},
		onError: (e) => {
			console.log(e.message)
		},
	})
}
```

이런 식으로 따로 state를 사용하지 않고도 값을 핸들링할 수 있는 장점이 있다.

```js
const { status, data, error } = useQuery('todos', () => axios.get(''))
```

이렇게 따로 isLoading과 isError를 나누지 않고 status로도 처리할 수 있다.

## 동기적으로 실행하기

다음 코드는 world가 true일 때 useQuery를 실행하는 코드이다.  
이런식으로 enabled라는 키워드를 통해 동기 작업 또한 가능하다.

```js
const { status, data, error } = useQuery('hello', () => axios.get(''), {
	enabled: !!world,
})
```
