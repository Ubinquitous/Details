## Sass란 무엇인가?

리액트를 사용할 때 많이 쓰이는 스타일시트 중 하나로 손꼽히는 Sass에 대해 알아보자.  
그럼 과연 Sass가 무엇이고, 왜 많이 사용할까?

공식 문서에서는 Sass에 대해 이렇게 말한다.
<img src='https://media.discordapp.net/attachments/1036162758875549761/1064453730868670525/sass.png?width=1920&height=681' />

"Sass is the most mature, stable, and powerful professional grade CSS extension language in the world."
번역하면 "Sass는 세계에서 가장 발달하고, 안정적이고, 가장 강력한 CSS 확장 언어이다." < 발번역 ㅈㅅ ㅎㅎ;

말그대로 Sass는 CSS의 확장 언어이다. Sass의 뜻은 Syntactically Awesome Style Sheets로,  
"문법적으로 정말 멋진 스타일시트!"라는 의미이다. 이름에서부터 자신을 강력하게 어필하는 매력적인 전처리기이다.

Sass는 코드를 재활용할 수 있게 해주고 가독성을 높여주는 등 유지 보수 측면에서 여러가지 도움을 준다.
Sass는 총 두 가지의 확장자를 지원한다. .sass와 .scss를 지원하는데, 두 확장자의 문법이 꽤 다르다.  
코드를 비교해보도록 하자.

.sass

```scss
$fontweight: Open Sans, sans-serif
$primary-color: #ccc

body
    font: 100% $font-stack
    color: $primary-color
```

.scss

```scss
$fontweight: Open Sans, sans-serif
$primary-color: #ccc

body {
    font: 100% $font-stack;
    color: $primary-color;
}
```

큰 특징으로는 .sass 확장자는 괄호와 세미콜론을 사용하지 않는다. sass가 처음 나올 때에는 .sass 확장자만  
있었으나, 개발자들의 요청에 의해서 .scss 확장자가 생긴 것이라고 한다.
보통 scss 문법이 더 자주 사용되기 때문에, 나는 앞으로 .scss 확장자를 사용하여 글을 써보겠다!  
다음에는 scss의 매력적인 문법들을 알아보도록 하자!!
