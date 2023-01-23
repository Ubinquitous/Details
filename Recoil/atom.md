## atom

atom은 상태의 단위로, 상태를 만들 때에 사용하는 키워드이다.  
다음 코드와 같이 사용할 수 있다.

```js
const fontSizeState = atom({
	key: 'fontSizeState',
	default: 14,
})
```

key와 default라는 속성을 기본적으로 받는데, key 속성에는 다른 atom과 구분할  
수 있는 고유한 ID가 들어가야한다.  
default값은 상태의 기본값을 지정해준다. 객체나 배열, 숫자, 문자 등 여러가지를 정의할 수 있다.

## atom effects

atom effects는 atom이 처음 생성되었을 때 어떤 작업을 할 수 있게 도와주는 속성이다.  
클린업 함수와 같이 사용 가능하며, useEffect와 비슷하게 작동한다.

```js
const myStateFamily = atom({
  key: 'MyKey',
  default: null,
  effects: param => [
    () => {
      console.log('hello!') // atom이 생성될 경우
      return () => ... // cleanup 함수
    },
  ],
});
```
