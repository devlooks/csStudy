## 1. 프로토콜 간략한 소개

  - 웹 서비스는 HTTP 프로토콜로 메시지를 전성하는 시스템  
    클라이언트가 보낸메세지는 HTTP프로콜에 실려 서블릿 컨테이너에 전송된다.

  - 전송된 메세지를 서버측에서 재구성하려면,   
    서블릿 컨테이너는 반드시 HTTP프로토콜 해석 기계를 구현해야함

## 2. 하나의 HTTP 메시지를 특정 하는 방법

  - 메세지 전송 프로토콜에서 반드시 필요한 것은 메시지 끝을 결정 하는것.  
    종료메세지 특정 할 필요 있음
  - HTTP 요청을 보내는 클라이언트는 요청에 필요한 문자열 뒤에 행구분자를 붙여  
    하나의 HTTP 메세지를 완성후 전송
    
## 3. 부가 정보(메시지 헤더와 메시지 바디)
  
  - HTTP/1.0에선 문자열 전송 이상의 기능 요구  
    단일 행 요청 문자열을 시작행으로 재정의  
    부가 정보를 전송하는 메시지 헤더, 메시지 바디를 선택적으로 추가 기능 생성  
  - Content-Length : 헤더 모두 전송후, 해당 길이만큼 메시지 바디가 따라온다는 의미  
  - 서버는 Content-Length 헤더 존재시, 만큼 더 읽은 후, 메시지 완성  
    없다면, 메시지 헤더가 종료된 시점, http 요청 자체 종료로 간주  
 
## 4. HTTP 메시지의 크기를 미리 알수 없는 경우
    
  - 미리 Content-Length를 만드는 건 서버리소스 낭비
  - 차라리, 바디 생성중 버퍼 사용해서 재활용하는것이 나음
  - 이를 위해서 **HTTP/1.1부터는 메세지 바디를 점진적 전송 방법 청크 인코딩 방식 사용**
  - **청크인코딩** 메세지 헤더에 transfer-conding의 값으로 chunked를 지정
  - chunk데이터 단위로 데이터 나열, **데이터 크기 전송(Content-Length)** -> **데이터 보내는 전략**을 반복하는 것.

## 5. 청크 인코딩 

  **HTTP 메시지의 각행은 CRLF으로 끝난다는것(생략 됨)을 기억(\r\n)**
  
  - Transfer-Encoded : chunked 헤더 존재  
  - 청크의 크기, 메시지 바디에 나타날수 있는 횟수 제한은 없음. 단, **메세지 끝에 0과 빈행이 있다는 점을 확인**

  - **청크의 크기가 0일 경우**, 더이상 청크가 없다는 것을 의미

  - Accept-Encoding: gzip, deflate : 메세지 바디를 gzip 또는 deflate로 압축한 것도 받을수 있다는 것을 의미

  - 해당 압축된 메세지 바디를 웹브라우저에서 압축 해제하여, 화면을 그린다.

## 6. HTML 에 존재하는 url 호출(GET)
  
  1. 서버에 get요청 
  2. HTML 반환
  3. 브라우저 응답 해석
  4. link 태그 발견
  5. /css/ 요청 자동으로 서버 전송

## 7. 서버 리소스에 대해 Content-Length 지정 및 브라우저 전송 과정 
   
  1. 서버상에서 파일 접근 가능
  2. Content-Encoding의 헤더 값이 gzip -> 서버리소스를 gzip으로 압축
  3. Content-Length를 헤더 값으로 지정,
  4. 압축 내용을 메세지 바디로 전송

## 8. Connection 헤더
  
  1. 소켓 연결을 요청/응답 완료후 끊을 것인지(close), 유지하여 다음 전송 대비(keep-alive)할건지, 여부 결정
  2. 일반적으로 tcp는 비싼 자원이므로 keep-alive가 유용

## 9. 매개 변수를 이용한 GET요청
  
  - 쿼리 스트링형식으로 붙여서 서버에 전송

## 10. 매개 변수를 이용한 POST 요청
  
    - Content-Type : application/x-www-form-urlencoded로 지정 
    - 메세지 바디에 쿼리스트링 형식으로 전달

**get과 post 둘다 form 으로 전송 가능**

## 11. GET과 POST의 차이점

  GET
  
    - GET 방식의 요청일 경우 쿼리스트링을 구분자로 잘라내여, 매개변수 할당, API 접근
    - 메모리상 적대 가능  

  POST

    - HTTP 바디 파싱 데이터 획득 과정 필요
    - 바디 파싱 하면서 메모리에 적재 (메시지 바디 크기 제한 없음)
    - 서블릿 동작적 매개 변수 준비 필요
    - 파싱 과정을 통해서 매개변수 준비
    - 의미없는 대기 상태 피함
    - 이런 상황을 피하기 위해, 메세지 바디에 대한 파싱을 시작하는 전략을 취함

## 12. 바이너리 데이터 전송 - multipart/form-data
  
  - Content-Type : multipart/form-data: boundary=----....
  
      1. POST 방식, HTTP 바디에 데이터 존재 인지 및 예상
      2. Content-Length 파악
      3. boundary 문자열을 구분자로 사용, 매개변수 단위로 재구성
  
  - **메세지 바디 읽는 세부 내용**
  
      1. Content-Type : multipart/form-data인 것 파악
      2. ServletInputStream 으로 HTTP바디 읽음
      3. name/value 쌍으로 익음, 메모리 적재
      4. 라이브러리 API 사용 접근 파일 업로드
