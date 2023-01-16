## useContext 사용해보기

useContext는 내가 제일 좋아하는 Context API의 기능 중 하나이다.  
Provider나 Consumer등을 사용할 때에는 컴포넌트 안에서만 렌더링하였으나,  
이 방식을 사용하면 컴포넌트 바깥에서도 값을 핸들링하고 파싱할 수 있다.  
코드를 통해 알아보자. 다음은 Context를 만들어주는 코드이다.

```js
const userInfo = {
  id: 3,
  name: "우빈",
  isLogin: false,
};
const UserContext = createContext(userInfo);
```

이렇게 만들어준 코드를 useContext 키워드를 사용해서 쉽게 불러올 수 있다.

```jsx
const MyPage = () => {
  const user = useContext(UserContext);

  return (
    <div>
      <h1>유저 아이디 : {user.id}</h1>
      <h1>이름 : {user.name}</h1>
      <h1>{user.isLogin ? "로그인중" : "로그인하지않음"}</h1>
    </div>
  );
};
```

이런 식으로 return문 밖에서도 값을 불러와 사용할 수 있다.
