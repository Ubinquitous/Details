## named import

Vite는 named import 기능을 지원한다.  
named import 기능은 import문에 이름을 붙여 사용할 수 있는 기능이다.

```js
const modules = import.meta.glob('./dir/*.js', { import: 'setup' })

// vite가 변환한 named import 코드
const modules = {
	'./dir/foo.js': () => import('./dir/foo.js').then((m) => m.setup),
	'./dir/bar.js': () => import('./dir/bar.js').then((m) => m.setup),
}
```
