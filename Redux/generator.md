## 제네레이터 함수

한 함수에서, 여러가지 값을 리턴할 수 있는 방법은 없을까?

```js
const func = () => {
	return 1
	return 2
	return 3
	return 4
}
```

이 코드는 당연히 첫 번째 값만 리턴하고 끝날 것이다. 허나 제네레이터 함수는 값을 순차적으로 반환하고,  
함수의 흐름을 멈추고 다시 이어 진행할 수도 있다.

```js
function* func() {
	console.log('hello')
	yield 1
	console.log('world')
	yield 2
	console.log('function*')
	yield 3
	return 4
}
```

제네레이터 함수를 만들때는 function\* 키워드를 사용한다.  
함수를 호출했을 때 반환하는 객체를 제네레이터라고 부르며, next()를 통해  
함수가 순차적으로 값을 반환하게 만들어줄 수 있다.

```js
const generator = func()
generator.next()
// hello
// { value: 1, done: false }
generator.next()
// world
// { value: 2, done: false }
generator.next()
// funcion*
// { value: 3, done: false }
generator.next()
// { value: 4, done: true }
generator.next()
// { value: undefined, done: true }
```

순차적으로 여러 값을 반환시킬 수도 있다.

```js
function* func() {
	console.log('created')
	let a = yield
	let b = yield
	yield a + b
}

const generator = func()
generator.next()
// created
// { value: undefined, done: false }
generator.next(3)
// { value: undefined, done: false }
generator.next(5)
// { value: 8, done: false }
generator.next()
// { value: undefined, done: true }
```
