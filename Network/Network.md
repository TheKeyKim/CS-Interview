# Network

1. OSI Layer 7에 대해 설명하시오.
```
- OSI : Open Systems Interconnection
- 통신에 필요한 동작을 7단계로 나누어 구분한 것이다.

L7 Application Layer
- 사용자가 직접 데이터를 작성하는 부분
L6 Presentation Layer
- 해당 데이터를 가공하는 영역
L5 Session Layer
- 어떤 방식으로 통신하는 지를 결정하는 영역(단방향, 양방향, 일문답)
L4 Transport Layer
- 목적지가 어디인지(PORT) 어떤방식으로 보낼지 결정하는 영역
L3 Network Layer
- 어떤 경로를 거칠지, 어떤 주소(ip)를 갖는지?
L2 DataLink Layer
- MAC(Media Access Control)을 찾는 영역
L1 Physical Layer
- 전기신호에 관한 영역
```

2. TCP / IP 에 대해 설명하시오.
```
- TCP / IP 는 IP를 기반으로 하는 보다 안정되고 보장된 패킷 전송방식이다.
- 기존 IP는 패킷의 전달 순서 혹은 전달 여부를 보증하지 않고, 안정성 측면에서 매우 떨어진다.
- TCP는 이런 IP 기반의 패킷 통신을 조절하는 전송 제어 프로토콜이라 볼 수 있다. 
- TCP / IP는 3-handshake라 부르는 기본적인 통신과정을 거친다.
    1. client -> server : sync 
    2. server -> client : sync ack
    3. clinet -> server : ack
- 여기서 sync 는 synclonize sequence number를 줄인 말이고, ack는 acknoledge의 준말이다.
- 각각은 비트를 이용한 플래그로 전달되며, 각각 고유의 값을 통해 전달한다. a라는 값을 sync로 보내면 ack에는 a+1의 값이 담겨 돌아온다.
- 또한 연결 해제에는 4-handshake라는 4단계를 거치는데 아래와 같다.
    1. client -> server : fin
    2. server -> client : ack
    3. server -> client : fin
    4. client -> server : ack
```
3. TCP / IP 4계층에 대해 설명하시오
```
L4 Application Layer
L3 Transport Layer
L2 Internet Layer
L1 Network Layer
```
4. 각 계층별로 설명하시오
```
L4 Application Layer
- 직접적으로 사용자와 맞닿은 영역. 
- 사용자 응용프로그램 인터페이스를 의미함
L3 Transport Layer
- 어떤 port를 이용할 것인지, 어떤 방식(TCP, UDP)을 사용할 것인지를 결정하는 영역
L2 Internet Layer
- 어떤 주소(IP)로 통할 것인지를 결정하는 영역
L1 Network Layer
- 물리적으로 데이터가 네트워크를 통해 어떻게 전송되는지를 결정하는 영역
- MAC(Media Access Control)이 해당 영역임.
```

5. 공개키와 대칭키란 무엇인가?
- 대칭키 
    - 하나의 키를 통해, 암호화 및 복호화가 가능한 키
- 공개키
    - 공개키 방식은 '공개키'와 '비공개키(비밀키, 개인키)' 두 가지 키를 갖음
    - 공개키로 암호화하고 비공개키로 복호화가 가능
    - 비공개키로 암호화하고 공개키로 복호화가 가능
    - 공개키 방식은 '전자서명'을 위하여 사용될 수 있음. 데이터의 제공자가 '비공개키'를 가지고 있는 사람이 맞는지 아닌지를, 데이터 + 공개키를 발송하는 방식을 이용하여 알 수 있음.
    - 데이터 + 공개키를 같이 발송할시, 중간에 공격자에 의해 탈취되더라도, 단순히 데이터 발송자가 암호키를 가지고 있는지에 대한 '신원 판별'이 목적이기 때문에 상관이 없음.

6. SSL 인증서의 동작방법을 설명하라
- SSL 인증서의 동작은 공개키 + 대칭키의 형태를 띔
- 전달하고자하는 데이터는 '대칭키'를 통해 이뤄짐.
- '대칭키'는 '공개키'를 이용한 동작으로 전달됨.
- 즉, 대칭키를 공개키를 이용해 암호화하고, 비공개키를 이용하여 복호화하여 클라이언트와 서버 모두 '대칭키'를 얻고, 이를 통해 데이터를 통신함.

7. HTTP와 HTTPS란 무엇이며 어떤 차이점을 갖는가?
- HTTP(HyperText Transfer Protocol)
    - 통신규약 중 하나이며, 텍스트를 교환하는 방식의 통신이다. 이는 중간에 텍스트가 탈취될 경우, 내용이 노출 되는 위험성이 존재한다.
- HTTPS(HTTP Secure)
    - 이는 HTTP의 통신방식을 차용하되, 거기서 추가적인 암호화를 거치는 방식이다.
    - SSL 프로토콜을 사용하여 텍스트를 암호화 한다.

8. HTTP 리퀘스트에는 어떤 메소드들이 존재하는가? 그 특징은?
- CRUD(Creation Read Update Delete)의 역할을 하는 method
    - post  : creation, 멱등성 X
    - get   : Read, 멱등성 O
    - put   : Update/Replace, 멱등성 O
    - patch : Update/Modify, 멱등성 O or X<br>
    (put은 완전한 교체이기 때문에 멱등성이 있으나, 수정은 멱등성이 없을 수 있음. 예를 들어 현 재값에 1을 더하는 방식을 이용할 경우 멱등성이 보장되지 않음)
    - delete: Delete, 멱등성 O
- 부가적인 역할을 하는 메소드들
    - options: 해당 리퀘스트가 어떤 메소드들을 지원하는지를 확인하는 용도.
    - head  : 해당 리퀘스트의 주체(서버)가 현재 응답을 하고 있는지를 확인하는 용도. (GET의 메서드 요청을 하지만, 리스폰스의 본문(body)를 받아오지 않고 헤더만을 받아오는 방식임.)

9. Restful API의 특징
- Restful API란 어떠한 '기술'이나 '프레임워크'가 아니라, 하나의 규격임. 어떤 조건을 충족시켜, 'Restful'한 규격을 맞춘 API를 Restful API라고 함.
- 요청 방식이 HTTP를 따름.
    - HTTP의 인프라를 그대로 사용하므로 따로 새로운 통신방식을 이용할 필요가 없음
    - HTTP 표쥰 프로토콜은 여러 플랫폼에서 손쉽게 사용이 가능함.
- stateless함
    - 클라이언트-서버 간의 통신에 대한 정보가 저장되지 않고, 각 요청이 분리되어 있어 서로 영향을 주지 않음.
    - 이는 TCP 방식의 3-handshake의 '전에 이뤄졌던 통신'이 영향을 주는 것을 생각하면 이해하기 쉬움.
- cacheable함
    - 이는 HTTP 방식을 따르는 것에 딸려오는 이점이라 볼 수 있는데, HTTP가 가진 캐싱 기능을 사용할 수 있음.
- self-description
    - REST API 메세지는 스스로를 표현할 수 있어야 함.
    - 예를 들어 /api/user/:id 이런 식의 GET METHOD가 있다면, 이는 유저의 정보를 요구하는 메소드일 것임.
- Client-Server 구조
    - Rest 서버는 API를 제공하고, 클라이언트는 사용자 인증 및 세션, 로그인 정보를 직접 관리하여 그 역할이 구분되어 있음.
    - 통신 구조에는 p2p(Peer To Peer)와 같이 client가 곧 네트워크의 노드가 되는 경우도 있는데, 이런 분산형 네트워크와 다르게 중앙집권형인 서버-클라 모델이라는 것임.
- 계층형 구조(layer) 
    - 클라이언트는 REST API 서버만을 호출하지만, 서버는 다중 계층으로 구성될 수 있음. 

10. 
