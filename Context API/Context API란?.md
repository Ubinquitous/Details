## Context API란?

Context API는 전역적으로 상태를 관리할 때에 사용한다.  
예를 들면 사용자의 정보나 프로젝트 내의 환경 설정 등을 관리할 때 자주 사용된다.
리액트는 부모가 자식에게 props로 필요한 데이터를 전송하는 방식을 사용한다.  
허나 자식이 부모의 데이터를 바꾸고 싶을 때는 이런 방법을 사용할 수 없다.

또한 Root Component에 있는 속성을 만약 F Component에서 사용한다면,  
Root -> A -> C -> F 로 props를 전달하며 데이터를 사용해야할 것이다.  
이러한 방식은 너무 복잡하고 코드의 가독성을 해치며, 유지 보수성이 낮아질 가능성이 있다.

Context API를 사용하면 Context를 만들어 한 번에 원하는 값을 받아 사용할 수 있다.

<img src='https://media.discordapp.net/attachments/1036162758875549761/1064524507429220412/react-data-flow.png?width=1646&height=936' alt=''/>

다음은 리액트의 전역 상태 관리 플로우이다.  
G가 Root Component의 데이터를 사용하려면 많은 파일을 거쳐 사용해야 하는 불편함이 있다.  
Context에서는 어떻게 이런 불편함을 해소해줄까?

<img src='https://media.discordapp.net/attachments/1036162758875549761/1064524507135610890/context-data-flow.png?width=1646&height=936' alt=''/>

다음은 Context API의 전역 상태 관리 플로우이다.  
사진과 같이 Context API로 부모요소와 자식요소를 한 번에 처리할 수 있다.  
만약 G 컴포넌트에서 Root Component의 데이터를 사용하고 싶다면,  
Context를 불러오는 명령어를 사용한 다음 바로 불러오면 되는 것이다!

Consumer를 통해 원하는 값을 한번에 불러올 수 있고,  
Provider를 통해 Context에 있는 value를 변경할 수 있다.

Context API와 같이 상태를 관리하는 MobX, Redux와 같은 라이브러리들이 있다.  
다 배워두면 협업에 정말 도움이 될 것이다!
