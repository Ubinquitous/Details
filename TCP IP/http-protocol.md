## HTTP 프로토콜

HTTP 프로토콜은 한 요청에 한 응답을 반환하는 간단한 프로토콜이다.  
페이지를 구성하는 파일 수만큼 이 작업을 반복하여 웹사이트에 사용자에게 표시된다.

HTTP 프로토콜에서는 request와 response라는 패킷을 사용하여 텍스트 기반 주고받기를 수행한다.

클라이언트가 서버에게 보내는 패킷은 여러가지이다.  
요청의 종류인 메소드 (GET, POST...), 요청 헤더 (클라이언트의 정보), 공백 줄 (헤더와 본문의 경계), 본문(요청에 필요한 데이터, GET일 경우 비어있음) 등의 데이터가 보내진다.

서버가 클라이언트에게 응답하는 패킷도 여러가지이다.

요청의 처리 결과인 상태 줄, 전달할 데이터에 관한 정보인 응답 헤더, 공백 줄, 본문 등의 데이터가 보내진다.

HTTP는 요청된 데이터를 반환하는 것을 목적으로 만들어졌기에,  
한 번의 요청과 응답으로 통신은 완결되고, 과거에 수행한 통신과 관련을 맺게 되는 경우는 없다.

이렇게 한 번으로 끝나는 프로토콜을 상태 비보존형 프로토콜이라고 한다.

## 쿠키

클라이언트측에 HTTP 프로토콜의 주고받기에 관한 정보를 저장하면 어떨까?  
그리고 통신할 때에 그 정보를 제시하고 서버가 사용자를 지정하면 상태 보존형 프로토콜로 취급할 수 있을 것이다.  
이때 주고받는 정보를 쿠키라고 한다.

쿠키는 클라이언트로부터 요청에 맞게 웹 페이지를 작성하는 장치와 함께 사용한다.