## "11장 HTTP와 REST 컨트롤러 " 

REST API
REST는 HTTP URL로 서버의 자원을 명시하고 HTTP 메서드(GET,POST,PATCH/PUT,DELETE)로 해당 자원에 대해 CRUD하는 것을 말합니다
그리고 API는 클라이언트가 서버의 자원을 요청할 수 있도록 서버 측에서 제공하는 인터페이스입니다.

#### REST Controller
REST API로 설계된 URL 요청을 받아 처리하는 컨트롤러
일반 컨트롤러는 뷰 페이지를 반환하고 REST 컨트롤러는 JSON이나 텍스트 같은 데이터를 반환한다.

#### REST 컨트롤러의 특징
- @RESTCONTROLLER 어노테이션을 붙여 선언한다.
- 클라이언트의 데이터 조회,생성,수정,삭제 요청을 HTTP 메서드에 맞게 @GetMapping, @PostMapping, @PatchMapping, @DeleteMapping 으로 받아 처리한다

#### ResponseENtity
REST 컨트롤러의 반환형, 즉 REST API의 응답을 위해 사용하는 클래스입니다

#### 
