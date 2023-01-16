## Provider를 사용하여 값 변경하기

Provider를 사용하면 Context의 값을 변경할 수 있다! 바로 코드로 알아보자.

```js
import UserContext from "../context/user";

const MyPage = () => {
  return (
    <UserContext.Provider value={{ id: 3, name: "비누", isLogin: true }}>
      {(value) => (
        <div>
          <h1>유저 아이디 : {value.id}</h1>
          <h1>이름 : {value.name}</h1>
          <h1>{value.isLogin ? "로그인중" : "로그인하지않음"}</h1>
        </div>
      )}
    </UserContext.Provider>
  );
};
```

다음과 같이 Context의 값을 변경하여 사용할 수 있다.  
Provider는 반드시 value가 명시되어야 한다. 만약 Provider를 사용했는데  
value가 명시되어있지 않으면 오류가 발생한다! 그렇기 때문에 조심하여 잘 사용하자!!
