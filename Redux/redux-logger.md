## redux-logger

redux-logger는 오픈 소스로 올라와있는 미들웨어이다.  
커스텀으로 만든 미들웨어들보다 훨씬 깔끔하고 편하다.  
설치방법은 다음과 같다.

```
$ yarn add redux-logger
```

이제 index.js, 즉 스토어를 만드는 파일을 들어가 수정해보자.

```js
import { createLogger } from 'redux-logger'

const logger = createLogger()
const store = createStore(reducer, applyMiddleware(logger))

const root = ...
```

이제 액션이 디스패치될 때마다 콘솔을 확인해보면 액션 디스패치 시간이 잘 나타난다.  
이런 식으로 미들웨어는 직접 만들기보다는 라이브러리로 설치하여 사용하는 경우가 많다.
