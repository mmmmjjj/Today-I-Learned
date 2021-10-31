## Spring Web MVC

#### Model

- 클라이언트의 요청에 대해 응답을 하기 위해 로직 수행
- 어플리케이션 상태의 캡슐화
- 상태 쿼리에 대한 응답
- 어플리케이션 기능 표현
- 변경을 view에 통지

#### View

- 모델을 화면에 시각적으로 표현
- 모델에게 업데이트 요청
- 사용자의 입력을 컨트롤러에 전달
- 컨트롤러가 view를 선택하도록 허용

#### Controller

- 요청이 들어 올 때 제어 역할
- 어플리케이션의 행위 정의
- 사용자 액션을 모델 업데이트와 mapping
- 응답에 대한 view 선택

<img width="780" alt="스크린샷 2021-10-31 오후 3 34 00" src="https://user-images.githubusercontent.com/67090601/139571254-2aa8663e-ff13-403a-b411-485ab416f53c.png">

## Spring MVC 구성요소

#### DispatcherServlet (Front Controller)

- 모든 클라이언트의 요청을 전달받음
- Controller에게 클라이언트의 요청을 전달하고 controller가 리턴한 결과값을 view에게 전달

#### HanderMapping

- 클라이언트의 요청 url을 어떤 controller가 처리할지 결정
- url과 요청 정보를 기준으로 어떤 핸들러 객체를 사용할 지 결정하는 객체
- DispatcherServlet은 하나 이상의 핸들러 매핑을 가질 수 있음

#### Controller

- 클라이언트의 요청을 처리 한 뒤, model을 호출하고 그 결과를 dispatcherServlet에 알려준다.

#### ModelAndView

- Controller가 처리한 데이터 및 화면에 대한 정보를 보유한 객체

#### ViewResolver

- Controller가 리턴한 뷰 이름을 기반으로 controller의 처리 결과를 보여줄 view를 결정

#### View

- Controller의 처리결과를 보여줄 응답화면 생성

## Spring MVC 흐름

<img width="783" alt="스크린샷 2021-10-31 오후 3 43 15" src="https://user-images.githubusercontent.com/67090601/139571574-35d9d95e-f286-444a-8490-42e9b2aaaf8e.png">

<img width="761" alt="스크린샷 2021-10-31 오후 3 43 05" src="https://user-images.githubusercontent.com/67090601/139571626-c6b0dc43-eb1d-4167-a2c0-d171eaae6cc6.png">

<img width="789" alt="스크린샷 2021-10-31 오후 3 43 26" src="https://user-images.githubusercontent.com/67090601/139571636-67e08036-027f-4805-9e65-5c18a775292a.png">

## Spring MVC 구현

#### 1. Web.xml 에 DispatcherServlet 등록 및 Spring 설정 파일 등록

<img width="769" alt="스크린샷 2021-10-31 오후 5 06 21" src="https://user-images.githubusercontent.com/67090601/139573943-3b6e5143-1185-4046-a708-c15e982f74c8.png">

<img width="786" alt="스크린샷 2021-10-31 오후 5 08 06" src="https://user-images.githubusercontent.com/67090601/139573978-d9cdbc88-eb80-4def-87a6-1eff2920012a.png">

- Spring Container : 설정파일의 내용을 읽고 ApplicationContext 객체를 생성
- <url-pattern> : DispatcherServlet이 처리하는 URL mapping 패턴 정의
- 1개 이상의 DispatcherServlet 설정 가능

#### 2. 설정 파일에 handlerMapping 설정

#### 3. Controller 구현 및 Context 설정 파일 (servlet - context.xml ) 에 등록

<img width="711" alt="스크린샷 2021-10-31 오후 5 10 33" src="https://user-images.githubusercontent.com/67090601/139574036-a96c621b-93da-4900-86dd-feec265e22fc.png">

<img width="711" alt="스크린샷 2021-10-31 오후 5 21 17" src="https://user-images.githubusercontent.com/67090601/139574344-8e2cc92e-abfe-4273-9894-3522a6e73e98.png">

  
  
- Controller Class 작성
- Context 설정파일에 Controller 등록

#### 4. Controller와 JSP의 연결을 위해 View Resolver 설정

- 위 코드 참고
- 정확한 view를 호출하기 위해 servlet-context에 ViewResolver 설정

#### 5. JSP 코드 작성

