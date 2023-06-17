Java 7에서 새로 추가된 Fork/Join은 어떤 것을 의미?

- 여러 계산 작업을 나누어 처리하고 다시 모으는 것을 의미한다.

Fork/Join에 있는 Work steal이라는 개념은 무엇인가?

- 한 Queue에서 대용량 작업 할시 다른 Queue에서 내용을 가져와 부담 한다.

Path 라는 인터페이스에는 어떤 기능 제공?

- 파일과 경로에 대한 정보 

Files 클래스는 어떤 기능을 제공하나?

- Path객체를 사용하여 파일을 통제하는데 사용된다.

WatchService라는 클래스는 어떤 기능을 제공하나?

- 파일이 변경되었는지 확인하는 기능 제공 (lastModified())

NIO에서 이야기하는 채널(Chennel)은 무슨 역할을 하나요?

- 데이터를 읽고, 다시 처리하는 역할

java.util 패키지에 추가된 Objects라는 클래스는 어떤 메소드들을 제공하나?

- equals, haschCode, compare, hash, toString등 static한 메소드 제공, 단 null도 처리한다(NPE발생X)
