## Consumer를 사용하여 상태 관리하기

본격적으로 Context API를 사용해보자.  
Context API는 리액트에서 지원하기 때문에 따로 라이브러리를 다운받을 필요가 없다!

## Context 생성하기

Context를 만들 때는 마음대로 경로를 지정해주어도 상관없다.  
바로 Context를 생성해보는 코드를 알아보자.

```js
import { createContext } from "react";

const UserContext = createContext({
  id: 1,
  name: "우빈",
  isLogin: false,
});

export default UserContext;
```

다음과 같이 Context를 생성할 수 있다. 위 코드는 유저의 정보를 관리하는 코드이다.  
파라미터에는 Context의 기본값을 지정한다. 다음과 같이도 지정할 수 있다.

```js
import { createContext } from "react";

const userInfo = {
  id: 1,
  name: "우빈",
  isLogin: false,
};

const UserContext = createContext(userInfo);

export default UserContext;
```

개인적으로는 이 방법을 더 선호한다. 코드가 깔끔해지고 직관적으로 바뀌기 때문이다.  
이제 Consumer를 사용해 본격적으로 상태를 관리해보자.

## Consumer 사용하기

Consumer를 사용해 상태를 관리하는 법은 아주 간단하다.  
사용하고싶은 코드의 부모 요소가 되는 위치에 Context.Consumer 태그를 감싸주면 된다.

```js
import UserContext from "../context/user";

const MyPage = () => {
  return (
    <UserContext.Consumer>
      {(value) => (
        <div>
          <h1>유저 아이디 : {value.id}</h1>
          <h1>이름 : {value.name}</h1>
          <h1>{value.isLogin ? "로그인하지 않음" : "로그인 중"}</h1>
        </div>
      )}
    </UserContext.Consumer>
  );
};
```

\* 꼭 함수 안을 소괄호로 감싸야 html 요소가 렌더링된다! \*

다음과 같이 태그를 감싸준 후, 중괄호를 열어 함수를 넣어준 다음 return하여 사용하면 된다.  
props로 받아서 오는 방식보다 더욱 깔끔하고 코드의 길이가 줄어들며 편리하다.  
이렇게 컴포넌트의 children이 있을 자리에 함수가 있는 것을 Function as a child 혹은 Render Props라고 부른다.
