## useSetRecoilState

useSetRecoilState는 useRecoilValue와 마찬가지로,  
상태 값을 변경하게 해주는 함수이다. 사용법은 똑같이, 첫 번째 파라미터에  
불러올 상태(atom)을 넣어주면 된다.

```js
const setUser = useSetRecoilState(userState)
```

이렇게 되면 이 setUser함수를 통해 atom의 값을 바꿀 수 있다.

```js
const Component = () => {
	const setUser = useSetRecoilState(userState)
	const user = useRecoilValue(userState)

	useEffect(() => {
		setUser({
			...user,
			nickname: '우빈',
			isLogin: true,
		})
	}, [])

	return (
		<div>
			<button onClick={() => console.log(user)}>유저</button>
		</div>
	)
}
```
