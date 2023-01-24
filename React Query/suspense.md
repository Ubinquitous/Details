## suspense

suspense는 React.Suspense와 함께 사용할 수 있는 옵션이다.  
queryClient의 defaultOptions에 suspense를 true로 설정해주면 전처리하여 사용할 수 있다.

```js
const queryClient = new QueryClient({
	defaultOptions: {
		queries: {
			retry: 0,
			suspense: true,
		},
	},
})
```

또는 함수마다 별개로 suspense를 적용시킬 수 있다.

```js
const { data } = useQurey("user", ()=>axios.get(''), { suspense: true });

return (
  <Suspense fallback={<div>loading</div>}> {/* loading때 보여주는 UI */}
    <ErrorBoundary fallback={<div>error</div>}> {/* error가 났을 때 보여주는 UI */}
      <div>{data}</div> {/* loading 후 보여지는 data */}
    </ErrorBoundary>
  </Supense>
);
```
