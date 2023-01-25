## render 설정으로 Wrapper 적용하기

만약 Wrapper, 즉 자기 자신이 children으로 들어가있는 컴포넌트를 테스트할 때에는  
test 파일의 render에 Wrapper를 따로 작성해주어야한다. 그러나 render를 재정의하는 파일을 하나 만들어주면  
하나하나 변경하지 않고 간편하게 사용할 수 있다. 아래 코드는 Recoil를 사용했을 때의 예시다.

src/test/util/render.tsx

```js
import * as React from 'react'
import { ReactElement } from 'react'
import { render as reactRender } from '@testing-library/react'
import { RecoilRoot } from 'recoil'

const render = (ui: ReactElement, { ...options } = {}) =>
	reactRender(ui, {
		wrapper: ({ children }) => <RecoilRoot>{children}</RecoilRoot>,
		...options,
	})

export * from '@testing-library/react'
export { render }
```

다음과 같은 render를 test 파일에서 모듈로 import하여 사용하면 자동으로 Wrapper가 적용되어 테스트된다.
