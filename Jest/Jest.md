## Jest란?

Jest는 페이스북에서 리액트와 더불어 개발한 자바스크립트 테스팅 라이브러리이다.  
많은 개발자들이 사용하고 있는 테스팅 라이브러리이며, Jest 하나만 설치해도 테스트를 수월히 진행할 수 있다.  
Jest가 출시되기 이전에는 여러가지 라이브러리를 섞어서 사용하여 테스트를 했었는데, Jest의 출시 이후 훨씬  
테스트가 편해졌다고 한다.

설치방법은 다음과 같다.

```
$ yarn add -D jest
```

```
typescript ver

$ yarn add -D jest @types/jest
```

그리고 package.json의 scripts 안에 있는 test의 값을 "jest"로 바꿔주자.

```json
{
	"scripts": {
		"start": "craco start",
		"build": "react-scripts build",
		"test": "jest",
		"eject": "craco eject"
	}
}
```

이렇게 준비하면 Jest를 프로젝트에서 사용할 수 있다!
