## useRecoilState

useRecoilState는 useRecoilValue와 useSetRecoilState를  
useState처럼 동시에 사용할 수 있게 해주는 함수이다.  
사용법은 useState와 같으며, 파라미터에 똑같이 불러올 상태(atom)을 넣어주면 된다.

```js
const [user, setUser] = useRecoilState(userState)
```

set 함수나 상태값의 이름은 어떻게 지어도 상관없다.  
이렇게 useRecoilState를 사용하면 읽기/쓰기를 두 가지 다 할 수 있다.  
문법도 친근하고 훨씬 편하다!

```js
const Component = () => {
	// const setUser = useSetRecoilState(userState)
	// const user = useRecoilValue(userState)
	const [user, setUser] = useRecoilState(userState)

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
