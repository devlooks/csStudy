### MVC 패턴

**Model, View, Controller로 구성된 디자인 패턴**
장점 : 재사용성, 확장성 용이
단점 : 애플리케이션 복잡 -> 모델, 뷰 관계 복잡

**Model**
어플리케이션의 데이터인 데이터 베이스, 상수, 변수 등을 뜻함

**View**
사용자 인터페이스 요소 뜻함

**Controller**
하나 이상의 모델과 하나 이상의 뷰를 잇는 다리 역할,

메인 로직 담당
모델과 뷰의 생명 주기 관리
모델, 뷰의 변경 통지 -> 해석 해당 내용 알려줌

데이터 validate, aggregate 한다

 

### MVP 패턴

**model, view, presenter로 된 패턴**

뷰와 프레젠터는 1:1 관계 mvc 패턴보다 강한 결함을 지님

### MVVM 패턴
**mvc와 다르게 커맨드와 데이터 바인딩을 가지는것이 특징**
뷰와 뷰 모델 사이의 양방향 데이터 바인디 지원
UI 별도의 코드 수정 없이 재사용, 단위 테스트 용이

ex) 뷰, 안드로이드
커맨드 : 커맨드 패턴 사용, vm의 명령요청을

객체 형태로 갭슐화, 나중에 이작업을 수행, 트리거 하도록 하는 패턴, command, recevier, invoker, client로 이루어져 있음

### 패턴의 공통 목표

**애플리케이션에 대한 시각화, 데이터 처리등 관리의 책임을 분리하는 것**