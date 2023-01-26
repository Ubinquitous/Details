## dependency import

Vite는 dependency import를 지원한다.  
따라서 import 구문을 작성할 때에, 경로를 표시해주는게 아니라 모듈의 이름만 작성하면 import가 정상적으로 작동한다.

```js
import { someMethod } from 'my-dep'
```

이는 Vite가 url을 이용해 ESM을 지원하는 브라우저에서 모듈을 가져올 수 있도록 import 구문을 수정하기 때문에 가능한 일이다.

## static asset

정적 에셋을 import할 경우, Vite는 public url을 반환한다.

```js
import imgUrl from './img.png'
document.getElementById('hero-img').src = imgUrl
```

쿼리를 이용하여 어떻게 asset을 가져올 것인지 명시할 수도 있다.

```js
// URL로 에셋 가져오기
import assetAsURL from './asset.js?url'
```

```js
// String 타입으로 에셋 가져오기
import assetAsString from './shader.glsl?raw'
```

```js
// 웹 워커 가져오기
import Worker from './worker.js?worker'
```

```js
// Base64 포맷의 문자열 형태로 웹 워커 가져오기
import InlineWorker from './worker.js?worker&inline'
```
