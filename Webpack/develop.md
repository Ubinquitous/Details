## 개발 서버 실행하기

개발 서버를 실행하려면 webpack config에서 한 키워드가 추가로 필요하다.  
바로 알아보자!

## devServer

devServer는 테스트 서버를 지정해주는 키워드이다.

```js
module.exports = {
	devServer: {
		port: 3000,
		hot: true,
	},
}
```

hot은 저장을 했을 때에 HMR의 작동 여부를 뜻하고, port를 통해 포트번호를 지정할 수 있다.  
이렇게 지정을 해준 뒤 다음 명령어를 실행해보자.

```
$ yarn dev
```

성공적으로 테스트 서버가 열릴 것이다.

## CORS proxy 설정하기

```js
module.exports = {
	devServer: {
		port: 3000,
		hot: true,
		proxy: {
			'/api/': {
				target: 'http://localhost:3090',
				changeOrigin: true,
			},
		},
	},
}
```

proxy를 따로 설정하여 백엔드와 통신할 때에 CORS 에러를 막을 수 있다.
