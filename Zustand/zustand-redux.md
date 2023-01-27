## Redux와 함께 사용하기

Zustand를 Redux처럼 사용하여 상태를 관리할 수 있다. 코드는 다음과 같다.

```js
const types = { increase: 'INCREASE', decrease: 'DECREASE' }

const reducer = (state, { type, by = 1 }) => {
	switch (type) {
		case types.increase:
			return { grumpiness: state.grumpiness + by }
		case types.decrease:
			return { grumpiness: state.grumpiness - by }
	}
}

const useGrumpyStore = create((set) => ({
	grumpiness: 0,
	dispatch: (args) => set((state) => reducer(state, args)),
}))

const dispatch = useGrumpyStore((state) => state.dispatch)
dispatch({ type: types.increase, by: 2 })
```

이런 식으로 redux와 함께 섞어 사용할 수 있다. redux middleware또한 zustand에서 지원한다.

```js
import { redux } from 'zustand/middleware'

const useGrumpyStore = create(redux(reducer, initialState))
```
