## module load

import 키워드를 사용한 파일을 테스트하려고 하면 Jest가 올바르게 인식을 하지 못한다.  
보통 트랜스파일러를 이런 상황에서 사용하지만, 여기서는 타입스크립트를 사용해보겠다.  
먼저 패키지를 설치해보자.

```
$ yarn add -D ts-jest
$ npx ts-jest config:init
```

명령어를 실행하고 나면 jest.config.js 파일이 최상위 디렉터리에 생성된다.  
명령어가 정상적으로 작동하지 않거나 파일이 생성되지 않았을 경우, 직접 생성해주어도 된다.  
jest.config.js 파일의 내용을 다음과 같이 바꿔주자.

```js
/** @type {import('ts-jest/dist/types').InitialOptionsTsJest} */
module.exports = {
	preset: 'ts-jest',
	testEnvironment: 'node',
}
```

이제 test 파일을 생성하고, yarn test를 실행해보면 정상적으로 test가 진행된다.
