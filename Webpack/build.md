## build하기

본격적으로 리액트 앱을 실행해보려면, 몇 가지 알아야하는 것이 있다. 바로 webpack 세팅이다.  
webpack 세팅에서는 몇 가지의 중요한 키워드를 사용하는데, 이 키워드를 통해 리액트 앱을 실행해보자.

## mode

mode 키워드는 현재 웹팩이 어떤 모드로 돌아가고 있는지를 명시하는 키워드이다.  
이 키워드를 사용해서 개발 모드에서만 보이는 테스트 기능들을 세부적으로 설정할 수 있다.

```js
module.exports = {
	mode: 'development', // or 'production',
}
```

## entry

entry는 webpack이 한 파일로 묶어줄 때에 시작점을 지정해주는 키워드이다.  
한 파일 안에 프로젝트의 모든 정보가 들어가 있거나 import되어있는 곳을 entry로 잡아주면 된다.

```js
// Single Page Application ( React )
module.exports = {
	entry: './src/index.tsx',
}
```

```js
// Multi Page Application ( React )
module.exports = {
    entry: {
        Home: './src/Home.tsx',
        Detail: './src/Detail.tsx',
        ...
    },
}
```

## output

output은 webpack을 실행한 후의 결과물 파일을 지정해주는 키워드이다.  
보통 build 디렉터리 안에 많이 위치해준다. 이름은 자유롭게 해도 무관하다.

```js
const path = require('path')

module.exports = {
	output: {
		filename: 'bundle.js',
		path: path.resolve(__dirname + '/build'), // User/desktop/my-project/build
	},
}
```

## module

제일 중요한 키워드로, 파일들을 어떤 로더로 번들링해줄 것인지 정해주는 키워드이다.  
loader를 지정해줄 때에 주의할 점은, 따로 명령어를 통해 설치를 해야한다.  
프로젝트에서 많이 사용되는 여러가지 로더들이 있으니 참고하길 바란다.

```
$ yarn add html-loader babel-loader
```

```js
module.exports = {
	module: {
		rules: [
			{
				test: /\.(js|jsx)$/, // 모든 .js .jsx 파일
				exclude: /node_modules/,
				use: 'babel-loader', // js-loader 사용
			},
			{
				test: /\.html$/, // 모든 html 파일
				use: [
					{
						loader: 'html-loader', // html-loader 사용
						options: { minimize: true },
					},
				],
			},
		],
	},
}
```

## plugins

html 파일을 build할 때에 build 디렉터리 내에 생성하려면 HTML 플러그인이 필요하다.  
require문을 통해서 import할 수 있으며, template 키워드는 기준이 될 html 파일,  
filename은 생성될 html 파일의 이름을 정하는 키워드이다.

```js
const HtmlWebPackPlugin = require('html-webpack-plugin')

module.exports = {
	plugins: [
		new HtmlWebPackPlugin({
			template: './public/index.html',
			filename: 'index.html',
		}),
	],
}
```

## 종합

이제 위의 코드들을 전부 종합해서 webpack.config.js 파일을 작성해보자.

```js
const path = require('path')
const HtmlWebPackPlugin = require('html-webpack-plugin')

module.exports = {
	mode: 'development',
	entry: './src/index.js',
	output: {
		filename: 'bundle.js',
		path: path.resolve(__dirname + '/build'),
	},

	module: {
		rules: [
			{
				test: /\.(js|jsx)$/,
				exclude: /node_modules/,
				use: ['babel-loader'],
			},
			{
				test: /\.html$/,
				use: [
					{
						loader: 'html-loader',
						options: { minimize: true },
					},
				],
			},
		],
	},
	plugins: [
		new HtmlWebPackPlugin({
			template: './public/index.html',
			filename: 'index.html',
		}),
	],
}
```

이렇게 파일을 설정한 후, 다음 명령어를 입력한 뒤 build 폴더에 접근해 index.html 파일을 열어보자.  
프로젝트가 잘 반영되어있을 것이다.

```
$ yarn build
```
