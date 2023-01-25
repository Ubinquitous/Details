## Vite

Vite는 모던 웹 프로젝트 개발 경험에 초점을 맞춰 탄생한 빌드 도구이다.  
브라우저에서 ESM을 지원하기 전까지는 개발자들은 번들링을 해야 했다. 그렇기에 Webpack, parcel, Rollup  
등의 도구들이 나온 것이다. 허나 몇 천개의 모듈이 있는 대규모 프로젝트에서 이 도구들이 병목 현상이 발생하며,  
테스트를 하는 데 오랜 시간을 기다리는 등의 비합리적인 상황이 벌어졌기에 Vite를 사용한다고 한다.

따라서 Vite를 사용하면 훨씬 빠르게 테스트 서버를 구동시킬 수 있다. 대규모 프로젝트에서 정말 유용한 라이브러리이다.  
설치방법은 다음과 같다.

```
$ yarn create vite my-app --template # <- 원하는 템플릿
```

Vite가 현재 지원하고 있는 템플릿은 다음과 같다.

| JavaScript | TypeScript |
| ---------- | ---------- |
| vanilla    | vanilla-ts |
| vue        | vue-ts     |
| react      | react-ts   |
| preact     | preact-ts  |
| lit        | lit-ts     |
| svelte     | svelte-ts  |

이렇게 바이트로 프로젝트를 생성하고 나서, 다음과 같은 코드를 작성하면 Vite로 서버가 열릴 것이다.

```
$ yarn dev
```
