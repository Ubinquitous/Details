## Sass를 왜 사용할까?

Sass를 사용하는 이유는 스타일 코드를 재활용할 수 있게 해주고, 코드의 가독성을 높여주기 때문이다. 그럼 어떤 기능들이 가독성을 높여준다는걸까? 여러가지 Sass의 강점들을 알아보도록 하자.

## 설치 방법

Sass는 npm이나 yarn으로 설치하면 된다!

```
npm install sass

or

yarn add sass
```

그 다음, .scss파일을 생성해 import하고 사용하면 된다.  
이제 본격적으로 Sass의 장점들을 알아보도록 하자!

## 1.구조

내가 생각하는 Sass의 최대장점 중 하나이다. Sass는 중괄호 안에 또 중괄호를 넣을 수 있다. 이게 무슨 말일까?  
코드를 통해 알아보자.

html 구조

```html
<div>
  <span>Sass에 대해 알아보자!</span>
</div>
```

css 문법

```css
div {
  width: 200px;
  height: 300px;
}

div span {
  font-size: 28px;
  color: white;
}
```

scss 문법

```scss
div {
  width: 200px;
  height: 300px;

  span {
    font-size: 28px;
    color: white;
  }
}
```

이런 식으로 Sass에서는 중괄호 안에 중괄호를 넣어 코드 길이를 줄여주고, 가독성을 높여준다.  
객관적으로 sass를 사용하다가 css를 사용했을 때 느끼는 불편함 중 1위는 중괄호 내 중괄호를 사용하지 못한다는 점이다.

## 2.변수 선언, 호출

Sass의 강점 중 하나는 변수이다. 물론 css에서도 변수 선언은 가능하다. 허나 Sass에서는 조금 더 편하게 변수를 사용할 수 있게 해준다.  
코드로 알아보자!

css 문법

```css
--main-color: green;

div {
  background-color: var(--main-color);
}
```

scss 문법

```scss
$main-color: green;

div {
  background-color: $main-color;
}
```

이렇게 Sass는 조금 더 간편하게 변수를 선언하고 사용할 수 있게 도와준다!

## 3.mixin

믹스인은 Sass에서만 있는 기능으로, 코드를 재활용할 수 있게 해준다.  
같은 코드가 중복될 때에 mixin을 사용하면 코드를 효율적으로 작성할 수 있다.  
@mixin으로 정의한 스타일시트를, @include 키워드를 통해 사용할 수 있다.  
코드를 통해 알아보자!

css 문법

```css
.div1 {
  background-color: green;
  width: 200px;
  height: 200px;
  border: 3px solid black;
}

.div2 {
  background-color: green;
  width: 200px;
  height: 200px;
  border: 3px solid black;

  position: fixed;
  top: 0px;
}
```

scss 문법

```scss
@mixin box-decoration {
  background-color: green;
  width: 200px;
  height: 200px;
  border: 3px solid black;
}

.div1 {
  @include box-decoration;
}

.div2 {
  @include box-decoration;

  position: fixed;
  top: 0px;
}
```

정말 편하다! 한번 스타일시트를 정의해두면 여기저기서 사용할 수 있다는 장점이 있다.  
또한 인자로 값을 전달하여 mixin을 만들 수도 있다.

```scss
@mixin size($widthSize, $heightSize) {
  width: $widthSize;
  height: $heightSize;
}

.div1 {
  @include size(500px, 200px); // 500x200
}

.div2 {
  @include size(300px, 300px); // 300x300
}
```

이런 식으로 같은 스타일을 지정해야하지만 값이 다를 경우, 인자로 넘겨주어 코드를 작성할 수도 있다.

## 4.조건문, 반복문

sass에서는 조건문과 반복문을 사용할 수 있다.

조건문을 이용해서 정적인 css에 동적인 효과를 줄 수 있다.  
코드로 알아보자!

```scss
@if $size >= 0 and $size <= 200px {
  @return 200px;
} @else {
  @return 800px;
}
```

이런 식으로 if문을 통해 조건에 맞게 다양한 스타일을 지정할 수 있다.  
반복문에 대해서 알아보자!

```scss
/* 1부터 3번 반복 */
@for $i from 1 through 3 {
  .through:nth-child(#{$i}) {
    width: 50px * $i;
  }
}

/* 1부터 3 직전까지만 반복(2번 반복) */
@for $i from 1 to 3 {
  .to:nth-child(#{$i}) {
    width: 50px * $i;
  }
}
```

from-through는 지정한 숫자부터 몇 번 반복해준다는 의미이다.  
from-to는 지정한 숫자부터 to 뒤에 지정한 숫자 이전까지만 반복한다는 의미이다.  
이런 식으로 Sass만이 지원하는 여러가지 키워드를 사용해서 코드의 길이를 줄이고, 가독성을 높일 수 있다.

개인적으로 가장 많이 사용하고 애용하는 CSS 라이브러리이다!  
CSS를 싫어하는 분들께 강추한다. CSS보다 작성해야하는 코드의 길이도 줄어들고, 디자인 가능한 범위가 넓어진다!  
Sass 화이팅
