## useState와 함께 Context API 사용하기

저번에 동적으로 Context API를 사용하는 법에 대해 알아보았는데, 이를 더 간편하게 하는 법이 있다.  
바로 상태 관리 훅인 useState와 함께 사용하는 것이다!

Context는 상태 값만이 아닌 함수도 Context에 담을 수 있다. 그 특성을 이용해서, 따로 상태 값을 변경하지 않고  
Context를 만들 때 useState를 활용해 그 안에 있는 함수를 넘겨주면 편하게 사용할 수 있다.

내가 프로젝트를 할 때 가장 많이 사용하고, 가장 애용하는 방법이다. 코드로 알아보자!

```js
const userInfo = {
  id: 0,
  name: "",
  isLogin: false,
};
const UserContext = createContext(userInfo);
const SetUserContext = createContext(() => {});
// TypeScript의 경우 밑의 코드로 생성하자.
// const SetUserContext = createContext((...props)=>{});

const App = () => {
  const [user, setUser] = useState(userInfo);

  return (
    <SetUserContext.Provider value={setUser}>
      <UserContext.Provider value={user}>...children</UserContext.Provider>
    </SetUserContext.Provider>
  );
};
```

다음과 같이 useState를 만들어 준 다음, value 값으로 넘기면 언제어디서든  
useContext 키워드를 이용하여 값을 핸들링할 수 있다!  
예시로 로그인페이지에서 유저의 값을 변경하는 코드를 알아보자.

```jsx
const Login = () => {
  const user = useContext(UserContext);
  const setUser = useContext(SetUserContext);

  useEffect(() => {
    setUser({
      id: 12,
      name: "세원",
      isLogin: true,
    });
  }, []);

  return (
    <div>
      <h1>{isLogin ? "로그인되었습니다!" : "비로그인 유저입니다."}</h1>
    </div>
  );
};
```

다음과 같이 값을 쉽고 편하게 핸들링할 수 있다. 이 점을 이용해서 axios로 백엔드에서  
불러오는 유저의 정보를 쉽게 Context에 저장하고 사용할 수 있다.  
정말 편하다! 많은 사람들이 알았으면 좋겠다.
