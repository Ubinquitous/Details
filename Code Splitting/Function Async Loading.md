## 자바스크립트 함수 비동기 로딩

버튼을 클릭하면 alert창을 띄워주는 간단한 코드를 작성해보자.  
리액트의 App.js 기본 세팅에서 바로 작성해보도록 하자.

```js
App.js

...
import notify from './notify';

function App() {
	const onClick = () => {
		notify()
	}

	return (
		<div className="App">
			<header className="App-header">
				<img src={logo} className="App-logo" alt="logo" />
				<p onClick={onClick}>Hello, React.</p> {/* onClick 달아주기 */}
			</header>
		</div>
	)
}
```

```js
notify.js
export default function notify() {
	alert('Hello?')
}
```

코드를 이렇게 작성하고 빌드하면 notify 코드가 main 파일 안으로 들어간다.  
허나 상단에서 import하는게 아닌 import()함수 형태로 메서드 내에서 사용하면, 파일을 분리시켜 저장한다.  
그리고 함수가 필요한 지점에 파일을 불러와 사용할 수 있다.

```js
const onClick = () => {
	import('./notify').then((result) => result.default())
}
```

import를 함수로 사용하는 문법은 웹팩에서 지원하는 문법이다. 아직 표준 자바스크립트 문법은 아니다.  
이제 빌드 후 확인해보면, 클릭 이벤트가 일어날 때마다 새로운 자바스크립트 파일을 불러올 것이다,
