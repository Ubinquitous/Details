## useMutation

useMutation은 서버에 데이터 변경 작업을 요청할 때 사용한다.  
mutationFn은 프로미스 처리가 이루어지는 함수로, 보통 axios등의 요청 함수를 넣는다.

```js
const savePerson = useMutation({
	mutationFn: () => axios.post('', ''),
})
```

## mutate

mutate를 통해서 이벤트가 발생되었을 때 값을 useMutation에 저장해줄 수 있다.  
mutate를 사용하면 작성한 내용이 실행된다. 또한 세 번째 인자를 통해 try catch finally 구문과  
같이 데이터를 따로 처리할 수 있다.

```js
const [person, setPerson] = useState({
	id: 1,
	name: '',
	nickname: '',
	isLogin: false,
})

const users = useMutation((user) => axios.post('http://localhost:8080/user', user), {
	onSuccess: (res) => {
		console.log(res)
	},
	onError: (err) => {
		console.log(err)
	},
	onSettled: () => {
		console.log('end') // finally
	},
}) // useMutate 정의

const onSavePerson = () => {
	// mutate에서도 사용 가능
	users.mutate(person, {
		onSuccess: (res) => {
			console.log(res)
		},
		onError: (err) => {
			console.log(err)
		},
		onSettled: () => {
			console.log('end') // finally
		},
	})
}
```

## invalidateQueries

invalidateQueries를 통해 리액트 쿼리의 유효성을 제거해주어 새롭게 서버에 요청을 보낼 수 있다.  
useQuery에 값이 저장되어있는 상태에서 useMutation을 사용하고 나면 캐싱된 값을 읽어오기 때문에,  
유효성을 제거해준 다음 다시 요청을 보내게 하여 새로 업데이트된 값을 불러오게 도와주는 키워드이다.

```js
const queryClient = useQueryClient() // 등록된 quieryClient 가져오기

const users = useMutation((user) => axios.post('', user), {
	onSuccess: (res) => {
		console.log(res)
		queryClient.invalidateQueries('user') // useQuery에서 사용하는 유효성 제거
	},
	onError: (err) => {
		console.log(err)
	},
	onSettled: () => {
		console.log('end') // finally
	},
})
```

## setQueryData

setQueryData는 invalidateQueries를 통해 유효성을 제거하지 않고 값을 업데이트하는 방식이다.

```js
const queryClient = useQueryClient()

const users = useMutation((user) => axios.post('', user), {
	onSuccess: (res) => {
		console.log(res)
		queryClient.setQueryData('user', (data) => {
			const res = data
			res.data.push(user)

			return res
		})
	},
	onError: (err) => {
		console.log(err)
	},
	onSettled: () => {
		console.log('end') // finally
	},
})
```

이렇게 코드를 짜면 서버에 다시 요청을 보내지 않고도 값을 업데이트할 수 있다.
