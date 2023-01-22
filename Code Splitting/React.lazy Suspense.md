## React.lazy & Suspense

React.lazy는 이런 코드 스플리팅을 더우 쉽게 해주는 유틸 함수이다.  
컴포넌트를 렌더링하는 시점에서 비동기적으로 로딩할 수 있게 해준다.  
사용법은 다음과 같다.

```js
const About = React.lazy(() => import('./About'))
```

Suspense는 코드 스플리팅된 컴포넌트를 로딩하도록 발동시킬 수 있고,  
로딩이 끝나지 않았을 때 보여줄 특정 UI를 설정할 수 있다.

```js
import { Suspense } from 'react';
...
<Suspense fallback={<h1>Loading...</h1>}>
    <About/>
</Suspnse>
```

fallback이라는 props를 통해 로딩 중 보여 줄 UI를 설정할 수 있다.
