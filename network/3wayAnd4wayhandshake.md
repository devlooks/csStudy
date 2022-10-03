# TCP 3way handshake

![image](https://user-images.githubusercontent.com/60064392/193551364-c5ae0d54-e73d-4095-9bd9-bac4f73649c7.png)


- TCP는 신뢰성을 확보시, 3-way handshake 진행

  1. SYN 단계 :

  클라이언트는 서버에 클라이언트의 ISN을 담아 SYN을 보낸다. ISN은 패킷에 할당된 임의의

  시퀀스 번호, 장치마다 다를수 있음

  2. SYN + ACK :

  서버는 클라이언트의 SYN을 수신, 서버의 ISN을

  보내며 승인 번호로 클라이언트의 ISN + 1을 보낸다

  3.ACK :

  클라이언트는 서버의 ISN + 1한 값인 승인 번호를

  담아 ACK를 서버에 보낸다.

- 위의 3가지 과정을 통해서, 클라와 서버간 신뢰 구축 UDP는 위 과정이 없다 - 신뢰성이 없음


# TCP 4way handshake

![image](https://user-images.githubusercontent.com/60064392/193551016-21cd5e94-46d0-4647-992f-623d5be706ac.png)

## FIN -> ACK, FIN -> ACK

1. 클라가 연결 닫을떄, FIN 세그먼트 보냄

  그리고 클라가 FIN_WAIT_1 상태로 들어감

  응답 기다림

2. 서버는 클라로 ACK라는 승인 세그먼트 보냄

  서버는 CLOSE_WAIT상태에 들어감

  클라는 FIN_WAIT_2 상태에 들어감

3. 서버는 ACK을 보내고 일정 시간 후에 클라 FIN

  이라는 세그먼트를 보냄

4. 클라는 TIME_WAIT 상태가 되고, 다시 서버로 ACK를 보내서 서버를 CLOSED한다.

  그리고 클라는 어느정도 대기후, 연결이 닫힘,

  서버 모든 자원 연결 해제

- TIME_WAIT : 첫번째 지연 패킷이 발생 할 경우,

패킷이 뒤늦게 도달하는 경우, 데이터 무결성 문제 발생 예방
