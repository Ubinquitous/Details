## 절대 경로 사용하기

이번엔 webpack을 사용해서 절대경로를 사용하는 법을 알아보자.  
먼저 tsconfig.json 혹은 jsconfig.json 파일을 만든 다음, 다음과 같이 작성하여 jsx를 지원하자.

```json
{
	"compilerOptions": {
		"outDir": "./build/",
		"noImplicitAny": true,
		"module": "es6",
		"target": "es5",
		"lib": ["ES2020", "DOM"],
		"jsx": "react",
		"allowJs": true,
		"moduleResolution": "node",
		"allowSyntheticDefaultImports": true,
		"esModuleInterop": true
	}
}
```

절대경로를 사용하기위해서는 tsconfig.json (혹은 jsconfig.json) 파일에 경로를 지정해주어야 에러가 나지 않는다.  
다음과 같이 작성하면, components, pages, utils 폴더를 import할 때 '../../' 등의 상대 경로가 아닌 @키워드를 사용해  
절대 경로로 파일을 import할 수 있다.

```json
{
	"compilerOptions": {
		"baseUrl": ".",
		"paths": {
			"@components/*": ["src/components/*"],
			"@pages/*": ["src/pages/*"],
			"@utils/*": ["src/utils/*"]
		}
	}
}
```

```js
import module from '@components/module.tsx'
```

또한 webpack config js를 열어 경로를 따로 지정해주면 끝난다.

```js
module.exports = {
	resolve: {
		extensions: ['.js', '.jsx', '.ts', '.tsx', '.json'],
		alias: {
			'@components': path.resolve(__dirname, '/src/components'),
			'@pages': path.resolve(__dirname, '/src/pages'),
			'@utils': path.resolve(__dirname, '/src/utils'),
		},
	},
}
```
