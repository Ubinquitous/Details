## React App 직접 만들기

Webpack을 사용하여 create react app과 react-scripts를 사용하지 않고 리액트 프로젝트를 생성해보자.  
먼저 프로젝트 디렉터리를 원하는 이름으로 생성하자.

```
$ mkdir my-project
```

그 다음 프로젝트 디렉터리에 진입하여 package.json 파일을 만들어주자.

```
$ cd my-project
or
$ code my-project

$ yarn init -y
```

설치하면 초기설정만 되어있는 package.json 파일이 생성될 것이다. 이제 webpack build에 필요한 것들을 다운로드해보자.

```
$ yarn add webpack webpack-cli webpack-dev-server
```

그 다음 package.json 파일에서 scripts를 webpack으로 설정해주자!

```json
	"scripts": {
		"dev": "webpack-dev-server --mode=development --open --hot --progress",
		"build": "webpack --mode=production  --progress",
		"start": "webpack --mode=development  --progress"
	}
```

이제 프로젝트의 루트 디렉터리에 webpack.config.js 파일을 생성해주면 세팅은 끝이난다!  
\+ 리액트 파일이 들어갈 src 디렉터리와 index.html이 들어갈 public 폴더를 만들어주자.
