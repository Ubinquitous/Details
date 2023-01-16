## styled-components란 무엇인가?

먼저 styled-components를 Capitalize로 작성해서 죽빵을 갈기고 싶었던 분들에게 사과부터 드린다. ~~폴더이름 맞춰보고 싶었음~~
저번에 컴포넌트를 스타일링하는 방법 중 Sass라는 기술을 공부했었다. Sass 못지 않게 인기가 많고, 많이 사용되는 또 다른 기술이 있다.  
바로 styled-components다!

스타일드 컴포넌트는 자바스크립트 파일 안에 스타일을 선언하는 신기한 방식을 가지고 있다.  
이런 방식을 CSS-in-JS라고 부르는데, 실제로 많은 사람들이 프로젝트에서 사용하는 기술이다.

CSS-in-JS 와 관련된 라이브러리는 정말 많다! 다른 라이브러리도 궁금하다면 밑에서 확인해보길 바람  
<a href='https://github.com/MicheleBertoli/css-in-js'>https://github.com/MicheleBertoli/css-in-js</a>

## 왜 사용할까?

css 파일과 js 파일의 상호작용은 꽤 어렵다. js가 document에 접근하여 스타일을 바꾸는 방법 말고는 다른 방법이 거의 없다.  
허나 이 styled-components를 사용하면, 같은 js파일끼리 상호작용을 너무나도 쉽게 할 수 있다.  
styled-components는 매개변수를 사용할 수 있는데, 매개변수로 JS에서 값을 넘겨주고 손쉽게 상호작용하며 스타일링을 할 수 있는 장점이 있다.  
또 styled-components를 사용하면 JS 코드 또한 가독성이 높아진다. 자세한 건 다음 글에서 알아보좌!!
