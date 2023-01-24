## useQueries

useQueries는 useQuery를 하나로 묶어 처리하는 문법이다.

```js
const res = useQueries([
	{
		queryKey: 'getOne',
		queryFn: () => axios.get(''),
	},
	{
		queryKey: 'getTwo',
		queryFn: () => axios.get(''),
	},
])
```

res 값에 배열 형태로 값들이 들어오며, 배열 내에는 여러가지 상태와 data가 함께 들어가있다.
