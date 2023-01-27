## Create Store

Store를 만들어보자. 만드는 방법은 정말 간단하다. zustand가 지원하는 create라는 키워드를 사용하여 만들 수 있다.  
코드는 다음과 같다.

```js
import create from 'zustand'

const useStore = create((set) => ({
	bears: 0,
	increasePopulation: () => set((state) => ({ bears: state.bears + 1 })),
	removeAllBears: () => set({ bears: 0 }),
}))
```

이렇게 store 안에서 원하는 함수도 선언해줄 수 있으며, set 함수를 통해서 상태를 제어할 수 있다.  
다음은 user를 제어하는 예제이다.

```js
import create from 'zustand'

const userStore = create((set) => ({
	id: 0,
	name: '',
	age: 0,
	isLogin: false,
	setUser: () =>
		set((state) => ({
			id: 3,
			name: 'ubin',
			age: 18,
			isLogin: true,
		})),
}))
```

이제 이 값을 어떻게 사용할 수 있을까?

## Store 사용하기

방법은 간단하다. 만들어놓은 사용할 store를 import해준 다음, 화살표 함수로 가지고올 상태를 지정해주면 된다.  
코드로 이해하는 것이 더 편할 것이다. 다음과 같다.

```js
function BearCounter() {
	const bears = useBearStore((state) => state.bears)
	return <h1>{bears} around here ...</h1>
}

function Controls() {
	const increasePopulation = useBearStore((state) => state.increasePopulation)
	return <button onClick={increasePopulation}>one up</button>
}
```

이렇게 state에서 원하는 상태값을 화살표 함수로 리턴하여 가져올 수 있다. 지정하지 않으면 모든 상태가 전부 가져와진다.
