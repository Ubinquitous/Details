## IP 프로토콜

IP 프로토콜은 트랜스포트 계층에게 데이터를 받은 다음,  
목적지를 특정하는 번호를 기록한 `IP 헤더`를 붙여 데이터 링크 계층에 전달한다.  
데이터에 IP 헤더를 붙인 것을 `IP 데이터그램`이라고 한다.

IP 데이터 전송은 Best Effort 방식이다. '노력은 하지만 결과는 보장하지 않는다' 라는 의미로,  
헤더가 깨지지 않았는지 확인이나 목적지의 존재 여부 정도의 판단 처리는 하지만, 재전송은 하지 않는다.

수신측에서는 IP 헤더에 쓰여진 목적지의 주소를 확인하고 자기 앞으로 온 데이터만 받는다.

## IP 주소 - IPv4

IPv4는 32자리 비트열로 이루어지며, 기본적으로는 네트워크부와 호스트부로 나누어진다.  
왼쪽의 16자리 비트열을 네트워크부라고 하며, 네트워크 고유의 번호가 들어간다.  
같은 네트워크 내라면 네트워크부의 IP 주소는 똑같다.

오른쪽의 16자리 비트열을 호스트부라고 하며, 각 컴퓨터를 나타내는 번호가 들어간다.  
똑같은 주소를 가지고 있는 컴퓨터가 여러 대 존재하면 목적을 이룰 수 없다.

따라서 번호의 중복을 피하기 위해 ICANN이라는 기관이 전 세계의 IP 주소를 관리한다.

### 서브넷 마스크

IP 주소만으로는 네트워크부와 호스트부의 경계를 알 수 없기 때문에,  
서브넷 마스크라는 값을 사용하여 경계를 나타낸다.

서브넷 마스크는 네트워크부에 대응하는 비트를 전부 1로 만든다.

## IP 주소 - IPv6

IPv4로 나타낼 수 있는 IP 주소는 약 43억 개이다. 허나 인터넷이 계속 보급됨에 따라  
부족해지기 시작해서, 해결책으로 IPv6가 출시되었고 이는 128비트로 이루어져있다.  
IPv4와 IPv6 사이의 호환성은 존재하지 않는다.

|             | IPv4    | IPv6                           |
| ----------- | ------- | ------------------------------ |
| 주소의 길이 | 32비트  | 128비트                        |
| 주소의 개수 | 약 43억 | 약 340간 ( 340조 _ 1조 _ 1조 ) |
| 표기 방법   | 10진법  | 16진법                         |
| 암호화 기능 | 옵션    | 기본                           |
| 멀티캐스트  | 비대응  | 대응                           |

IPv6는 주솟값을 16비트마다 콜론으로 구분하고, 16진수로 표기한다.

## 라우팅

라우터는 네트워크간을 연결해 패킷이 목적지에 전달될 때까지 길을 안내한다.  
컴퓨터 사이의 거리를 통과한 라우터의 개수로 나타내는데, 이때 사용하는 단위를 `홉`이라 한다.