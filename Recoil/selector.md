## selector

selector는 상태 값을 얻어와서 원하는 형식으로 반환해주는 함수이다.  
get 키워드를 통해 상태를 불러온다음, return하여 새로운 값을 반환할 수 있다.

```js
const filteredTodoListState = selector({
	key: 'filteredTodoListState',
	get: ({ get }) => {
		const filter = get(todoListFilterState)
		const list = get(todoListState)

		switch (filter) {
			case 'Show Completed':
				return list.filter((item) => item.isComplete)
			case 'Show Uncompleted':
				return list.filter((item) => !item.isComplete)
			default:
				return list
		}
	},
})
```

이런 식으로 사용할 수 있으며, 이 값은 useRecoilValue로 읽을 수 있다.

```js
const todoList = useRecoilValue(filteredTodoListState)
```

상태를 파싱하여 다르게 보여줄 때 보통 함수를 만들어 사용했는데, 이런 식으로  
selector를 사용하면 useRecoilValue라는 키워드를 사용하며 더욱 명시적으로  
코드를 짜고, 가독성을 높일 수 있을 것 같다.
