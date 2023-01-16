## 동적으로 Context 사용하기

이제 Context 값을 업데이트해야 할 경우 어떻게 할 수 있는지 알아보자.

## 함수 전달하기

Context값에는 무조건 상태 값만 있어야하는게 아니라, 함수도 전달이 가능하다.  
Provider 값에 상태값은 state로, 함수는 actions로 묶어 전달해보자.

```jsx
import { createContext, useState } from "react";

const ColorContext = createContext({
  state: { color: "black", subcolor: "red" },
  actions: {
    setColor: () => {},
    setSubColor: () => {},
  },
});

const ColorProvider = ({ children }) => {
  const [color, setColor] = useState("black");
  const [subcolor, setSubcolor] = useState("red");

  const value = {
    state: { color, subColor },
    actions: { setColor, setSubcolor },
  };

  return (
    <ColorContext.Provider value={value}>{children}</ColorContext.Provider>
  );
};

const ColorConsumer = ColorContext.Consumer;

export { ColorsProvider, ColorConsumer };

export default ColorContext;
```

위 코드의 Provider에서는 상태와 함수를 각각 분리해서 전달해준다.  
이렇게 분리를 시켜주면 나중에 Context값을 사용할 때 편하다.  
이제 Context를 불러오거나 수정할 때 다음과 같은 함수를 통해 값을 핸들링할 수 있다.

```js
<ColorConsumer>
  {({ actions, color }) => (
    <div>
      <button onClick={() => actions.setColor("green")}>BUTTON</button>
    </div>
    <div style={{ background-color: color }}></div>
  )}
</ColorConsumer>
```

다음과 같이 Function as a child 형식을 사용하여 함수를 불러와서,  
동적으로 Context값을 바꿀 수 있다!
