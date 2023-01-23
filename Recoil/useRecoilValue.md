## useRecoilValue

useRecoilValue는 상태 값을 불러오는 함수이다.  
사용법은 간단하다. 선언문에 useRecoilValue를 대입해주고,  
파라미터에 불러올 상태(atom)을 넣어주면 된다.

```js
const value = useRecoilValue(textState)
```

이렇게 값을 불러오면, value라는 값을 통해 상태를 읽을 수 있다.
