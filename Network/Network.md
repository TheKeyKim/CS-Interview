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

5. HTTP와 HTTPS의 차이점

6. HTTP 리퀘스트에는 어떤 메소드들이 존재하는가? 그 특징은?

7. Restful API의 특징

8. 
