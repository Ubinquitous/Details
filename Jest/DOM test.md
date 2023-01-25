## DOM 테스트하기

DOM을 테스트하려면 추가적인 라이브러리가 필요하다. 다음 명령어를 통해 설치하자.

```
$ yarn add -D @testing-library/jest-dom @testing-library/react
```

그리고 나서 setupTests.ts 파일을 생성해 다음과 같은 코드를 작성해주고 저장하면 된다.  
보통 setupTests.ts 파일은 cra로 리액트 프로젝트를 생성했을 때 디폴트로 설정되어있다.  
이는 react-scripts로 실행하는 test도 jest와 똑같은 설정이 필요하기 때문이다.

```js
require('@testing-library/jest-dom')
```

그 다음 jest.config.js 파일을 바꿔주자.

```js
module.exports = {
	preset: 'ts-jest',
	testEnvironment: 'jsdom',
	setupFilesAfterEnv: ['<rootDir>/setupTest.js'],
	globals: {
		'ts-jest': {
			tsconfig: 'tsconfig.jest.json',
		},
	},
}
```

이제 테스트 파일을 작성하여 테스트하면 테스트가 잘 이루어질 것이다.
