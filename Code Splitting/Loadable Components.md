## Loadable Components

Loadable Components는 코드 스플리팅을 편하게 도와주는 라이브러리다.  
React.lazy와 Suspense와는 다르게, SSR를 지원하며, 렌더링하기 전에 필요할 때 스플리팅된 파일을 미리 불러올 수도 있다.

사용법은 React.lazy와 똑같다. 대신, Suspense를 사용하지 않아도 된다.  
설치방법은 다음과 같다.

```
$ yarn add @loadable/component
```

사용법은 다음과 같다.

```js
import loadable from '@loadable/component'
const About = loadable(() => import('./About'))

...
function App(){
    return (
        <About/>
    )
}
```

Suspense처럼 로딩 중 다른 UI를 보여주고 싶다면 loadable의 두 번째 파라미터로 값을 넘겨주면 된다.

```js
const About = loadable(() => import('./About'), {
	fallback: <h1>Loading...</h1>,
})
```
