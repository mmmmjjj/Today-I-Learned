## 📌 Web Architecture

![image](https://user-images.githubusercontent.com/67090601/136659338-f4a481db-dde1-4467-8cef-cfa1c70600d1.png)

>1. 서버에서 클라이언트가 접속 할 수 있도록 서버를 킨다.
>2. 웹브라우저에서 데이터를 발생시킨다.
>3. 그 데이터를 가지고 웹서버에 `request` 요청한다.
>4. 웹서버는 http server이기 때문에 직접 DB 작업을 할 수 없다. 그래서 웹 서버와 DB 사이에 어플리케이션 서버가 존재한다.<br>
어플리케이션 서버에서 그 데이터를 이용해 DB를 연결(Persistence Logic) 하고 로직을 처리(Business Logic)한다.
>5. 다시 웹 브라우저에 `response`를 보내 결과를 출력한다. 결과는 마크업언어로 표시.(Presentation) ex) html, xml, json ...

> 원래는 웹 서버, 어플리케이션 서버가 따로 존재하는데 WAS는 두개를 합쳐놈 ex) Tomcat, JBoss, Weblogic...
> <br> 역할 : 클라이언트에 접속 처리, 데이터 처리

- Context-root
    - http://edu.ssafy.com/**여기부분**
    - 위의 링크로 들어가면 WebContent에 있는 컨텐츠가 보인다.

### 💡 Dynamic Web Project 구조
![image](https://user-images.githubusercontent.com/67090601/136660020-244efd07-47a0-4f4a-b5a1-85a473bb7cfd.png)

- `src` : 자바 파일
- `WebContent` : html, css, js, jsp, img ... 자바를 제외한 모든 파일

## 📌 Servlet
- 자바를 사용하여 웹페이지를 동적으로 생성하는 서버측 프로그램, 혹은 그 사양
- 웹서버의 성능을 향상하기 위해 사용되는 자바 클래스의 일종

### Servlet의 동작흐름
![image](https://user-images.githubusercontent.com/67090601/136660147-806bc628-9de9-42ed-8b19-d32c3013a937.png)

![image](https://user-images.githubusercontent.com/67090601/136660179-d9f516a0-286a-4cde-82f3-884ba37f636e.png)

### Servlet Life-Cycle

- Servlet은 javaSE의 클래스와 다르게 main 메소드가 없다. 즉 객체의 생성부터 사용의 주체가 사용자가 아닌 Servlet Container에게 있다.

- Client가 요청(Request)을 하게 되면 Servlet Container는 Servlet객체를 한번만 생성하고, 한번만 초기화 하며 요청에 대한 처리를 요청시마다 반복하게 된다. 또한 Servlet객체가 필요 없게 되면 destroy 제거한다.

### 주요 method

![image](https://user-images.githubusercontent.com/67090601/136660256-4f6ab85a-3ddc-4219-be1d-08e3efbeda8d.png)

- init()
    - 초기화
    - 최초 한번만 초기화 작업 수행. db 드라이버 로딩을 한번만 하듯이!
 
- service(request, response)
    - 모든 로직 처리

> service() 를 제외한 네가지는 안 만들어도 된다. 필요할 때도 있고 없을 때도 있다.

- GenericServlet
    - service만 오버라이드 된다.
    - 근데 얘는 get을 할지 post를 할지 if문으로 설정해줘야 해서 계속 if문이 호출되는 단점
- HttpServlet
    - 가지고 있는 메서드 중에 원하는 메서드만 오버라이딩하면 된다.

    ### Parameter 전송 방식

![image](https://user-images.githubusercontent.com/67090601/136660292-83f03741-0020-4a04-96f0-b677289affd1.png)

- 쉽게 보자면 POST라 명시되어 있는 경우 빼고 다 GET이다.
