## Webpack

Webpack은 자바스크립트 모듈 번들러이다.

<img src='https://media.discordapp.net/attachments/1036162758875549761/1068050253867130931/15PpB0JEPdB30wER8_XWuIQ.png'/>

사진처럼, 여러 개의 파일을 한 파일로 합쳐주는 역할을 한다.  
html에서 바닐라 js 코드들을 import할 때에 코드가 뒤엉키는 오류가 발생했다.

```html
<body>
	<script src="/app.js"></script>
	<script src="/script.js"></script>
</body>
```

다음과 같은 상황에서 html은 math.js 파일을 불러온 다음 script.js 파일을 불러온다.  
그래서 다음과 같은 코드 작성이 가능하다.

```js
// app.js
function HelloWorld() {
	console.log('Hello World!')
}
```

```js
// script.js
HelloWorld() // Hello World!
```

이렇기에 만약 script.js 파일에서 HelloWorld라는 함수가 또 선언이 된다면, app.js의 HelloWorld 함수는  
사용하지 못하고 덮혀버린다. 그렇기에 큰 프로젝트에서는 이와 관련된 오류가 많이 났으며, 이 외에도 여러가지 문제점이 있었다.  
그래서 웹팩이 출시되었다. 웹팩은 entry (시작점)를 시작으로 의존적인 모듈을 전부 찾아내 한 파일로 묶어준 후 output해준다.

설치 방법은 다음과 같다.

```
$ yarn add webpack webpack-cli webpack-dev-server
```

이제 성공적으로 프로젝트에서 webpack을 사용할 수 있다. 이 글에서는 웹팩으로 리액트를 렌더링하는 방법에 대해서 이야기해보겠다.
