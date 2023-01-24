## React Query

리액트 쿼리는 서버의 값을 클라이언트에 가져오거나, 캐싱, 값 업데이트, 에러핸들링 등 비동기 과정을 더욱 편하게 도와주는 라이브러리다.  
리액트 쿼리를 통해 서버 데이터와 클라이언트 데이터를 분리하여 관리할 수 있다. 또한 여러가지 장점이 있는데, 다음과 같다.

## 장점

- update시 자동으로 get 수행
- 데이터가 오래 되었다고 판단시 다시 get 수행
- 동일 데이터를 여러번 요청할 경우 한번만 요청
- 무한 스크롤 가능
- 비동기 과정을 선언적으로 관리 가능
- 리액트 훅과 비슷한 문법으로 친근한 사용법

이렇듯 여러가지 장점이 있다.  
설치방법은 다음과 같다.

```
$ yarn install react-query
```

리액트 쿼리는 리액트의 index 파일에서 세팅을 해주어야 한다.  
queryClient를 new 키워드를 사용해 생성하고, 리액트 쿼리에서 지원하는 컴포넌트로 App을 감싸주면 된다.  
또한 queryClient의 디폴트 값도 설정해줄 수 있다.

```js
import { QueryClient, QueryClientProvider } from 'react-query'
import { ReactQueryDevtools } from 'react-query/devtools'

const queryClient = new QueryClient({
    defaultOptions: {
    queries: {
      retry: 0, // 요청 실패했을 경우 재요청 횟수
      suspense: true // React.Suspense를 사용할 때
    }
  }
})

const root = ReactDOM.createRoot(document.getElementById('root') as HTMLElement)
root.render(
	<QueryClientProvider client={queryClient}>
		<ReactQueryDevtools initialIsOpen={true} />
		<App />
	</QueryClientProvider>
)
```

## QueryCache

QueryCache 또한 React Query가 지원하는 것인데, 쿼리에 대해 성공과 실패를 전처리할 수 있다.

```js
const queryClient = new QueryClient({
	queryCache: new QueryCache({
		onError: (error) => {
			console.log(error)
		},
		onSuccess: (data) => {
			console.log(data)
		},
	}),
})
```
