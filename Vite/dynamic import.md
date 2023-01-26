## dynamic import

Vite는 dynamic import 또한 지원한다.
변수 file은 깊이가 1인 파일에서만 나타낼 수 있으며, 만약 변수명에 /가 섞여들어간다면 정상적으로 파일을 import하지 못할 수 있다.

```js
const module = await import(`./dir/${file}.js`)
```
