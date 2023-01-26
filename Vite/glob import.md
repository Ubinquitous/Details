## glob import

Vite는 glob import 기능을 지원한다. glob import는 import문 하나로 여러 개의 모듈을 한 번에 import할 수 있는 기능이다.

```js
const modules = import.meta.glob('./dir/*.js')

// vite가 변환한 glob import 코드
const modules = {
	'./dir/foo.js': () => import('./dir/foo.js'),
	'./dir/bar.js': () => import('./dir/bar.js'),
}
```

동적으로 import하는 것이 아니라 직접 모듈을 가져오고자 한다면, 두 번 째 인자로 { eager: true } 객체를 전달해주면 된다.

```js
const modules = import.meta.glob('./dir/*.js', { eager: true })

// vite가 변환한 glob import eager: true 코드
import * as __glob__0_0 from './dir/foo.js'
import * as __glob__0_1 from './dir/bar.js'
const modules = {
	'./dir/foo.js': __glob__0_0,
	'./dir/bar.js': __glob__0_1,
}
```

## glob import as

glob import한 모듈을 대상으로 alias를 지정해줄 수도 있다.

```js
const modules = import.meta.glob('./dir/*.js', { as: 'raw' })

// vite가 변환한 glob import as 코드
const modules = {
	'./dir/foo.js': 'export default "foo"\n',
	'./dir/bar.js': 'export default "bar"\n',
}
```

## glob pattern array

두 경로를 묶어 glob하여 import하는 것도 가능하다.

```js
const modules = import.meta.glob(['./dir/*.js', './another/*.js'])
```

## negative glob pattern

import 경로에 ! 를 사용하여 not을 표시할 수 있다.

```js
const modules = import.meta.glob(['./dir/*.js', '!**/bar.js'])

// vite가 변환한 negative glob pattern 코드
const modules = {
	'./dir/foo.js': () => import('./dir/foo.js'),
}
```
