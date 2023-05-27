String 클래스는 final 클래스인가요? 만약 그렇다면, 그 이유는?

- String은 final 클래스로 구현 되어있으며 CharSequence, Comparable, Serializable로 구현되어있다.

- final로 구현되어있는 이유  
  1. String은 기본적으로 불변객체이다. 즉, String 변수에 값을 재 할당 하는 로직은 String 객체를 새로 만들어 String pool에 있는 값을 할당하는 것이다.
    &nbsp;- String pool은 객체를 저장 하는 것이 아닌, 해당 값을 저장한다. ex) String str = "Hello"; -> 일시, "Hello" 라는 문자열이 String pool에 저장 된다.
    &nbsp;![image](https://github.com/devlooks/csStudy/assets/60064392/585da595-12d7-45c5-b0ac-25570611f708)  

  2. 동기화  
    &nbsp;- String은 불변객체이기 때문에 할당된 값이 변경 되지 않는다. 즉, Thread-safe하다.
    
  3. 해시코드 캐싱  
    &nbsp;- hashCode 계산시, 할당된 값을 계산후 String 으로 메모리에 저장 한다. 
    &nbsp;- String은 불변 객체이므로 해시코드가 변경불가능
    &nbsp;- 해시코드 사용시, String pool에 있는 해시코드 값을 공유만 하면된다. 즉, 캐싱 기능 제공한다.

  4. 보안  
    &nbsp;- Java 애플리케이션에서 String으로  사용자 이름, 암호, 연결 URL, 네트워크 연결 등과 같은 중요한 정보를 저장
    &nbsp;- 클래스를 로드하는 동안 JVM 클래스 로더에서도 광범위하게 사용
    &nbsp;- 임의의 공격자가 String에 접근하여 할당 된값을 바꿀수 있는것을 방지 하기 위해서
   
   5. 성능  
    &nbsp;- Heap에 있는 String 객체가 String pool의 값을 바라 보게 된다.
    &nbsp;- 한개의 값(문자열)을 여러개의 String 객체가 바라보게 됨으로서 중복 문자열 저장을 줄여, 힙 메모리 절약하여 성능 향상 시킨다.

String 클래스가 구현한 인터페이스에는 어떤 것들이 있나?

&nbsp;- CharSequence, Comparable, Serializable

String 클래스의 생성자 중에서 가장 의미 없는 (사용할 필요없는) 생성자는 무엇인가?

&nbsp;- String()

String 문자열을 byte 배열로 만드는 메소드의 이름?

&nbsp;- getByte()

String 문자열의 메소드를 호출하기 전에 반드시 점검해야하는 사항은 무엇인가?

&nbsp;- null Check

String 문자열의 길이를 알아내는 메소드는 무엇인가?

&nbsp;- length() 

String 클래스의 equals() 메소드와 compareTo() 메소드의 공통점과 차이점?

&nbsp;- 공통점 : 상호 값을 비교

&nbsp;- 차이점 : equals() 는 boolean 타입 return, compareTo()는 int 타입 return(앞이면 양수, 뒤면 음수)

문자열이 "서울시"로 시작하는지를 확인하려면 String의 어떤 메소드를 사용?

&nbsp;- startsWith();

문자열에 "한국"이라는 단어의 위치를 찾아내려고 할 때에는 String의 어떤 메소드를 사용해야하나?

&nbsp;- indexOf(), lastIndexOf()

위의 문제의 답에서 "한국"이 문자열에 없을 떄 결과 값은 무엇인가?

&nbsp;- -1

문자열의 1번 부터 10번째 위치까지의 내용을 String으로 추출하려고 합니다  
어떤 메소드를 사용해야 하나요?

&nbsp;- substring()

문자열의 모든 공백을 * 표시로 변환하려고 합니다. 어떤 메소드 사용?

&nbsp;- replace() or replaceAll()

String의 단점을 보완하기 위한 두개의 클래스는 무엇인가?

&nbsp;- StringBuilder, StringBuffer
&nbsp;- 하나의 메소드 내 에선 StringBuilder, 쓰레드 동시 접근성을 가진 변수라면 StringBuffer 

위의 답에서 문자열을 더하기 위한 메소드 이름은 무엇인가?

&nbsp;- StringBuilder (append() 사용)
