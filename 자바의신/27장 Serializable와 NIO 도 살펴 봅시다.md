java.io.Serializable을 import 하는 이유 

- 객체를 저장하기 위해서

java.io.Serializable의 serialVersionUID를 지정하는 이유는 무엇인가?

- 서버간 통신하는 객체 클래스가 동일한지 판단하기 위한 값

자바에서 객체를 파일로 읽거나 쓸 때 사용하는 Stream 클래스 이름은 무엇인가?

- FileOutputStream, FileInputStream

transient 예약어의 용도

- Serializable 의 대상에서 제외 하기 위해

NIO가 생긴 이유

- 기존의 IO 보다 더 빠른 속도를 위해

NIO 에서 Chennal의 용도

- Stream 데이터의 읽기와 쓰기

NIO 에서 Buffer의 용도

- 읽은 데이터를 메모리에 저장 및 
- 메모리 크기 설정 (capacity)
- 읽을수 없는 첫 위치 획득(limit)
- 현재 버퍼의 위치 (position)
- 현재 position 표시(mark)
- position 을 mark한곳으로 이동(reset)
- position 을 0으로 이동 (rewind)
- remaining (limit - position 값)
- position과 limit 값에 차이가 있는 경우 true 리턴
- clear() 버퍼를 지우고 현재 position을 0으로 이동, limit 값을 버퍼의 크기로 변경
ex) 0 <= mark <= position <= limit <= capacity

NIO에서 Buffer의 상태를 확인 하기 위한 메소드들에는 어떤 것들이 있나?

- mark() : 현재 position 표시
- remaining() : (limit - position 값)
- hasRemaining() : position과 limit 값에 차이가 있는 경우 true 리턴
- clear() 버퍼를 지우고 현재 position을 0으로 이동, limit 값을 버퍼의 크기로 변경

NIO에서 Buffer의 position을 변경하기 위한 메소드들에는 어떤것들이 있나?

- reset() : position 을 mark한곳으로 이동
- rewind() : position 을 0으로 이동
 
