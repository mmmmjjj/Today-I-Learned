## REST API

- HTTP URI를 통해 제어할 자원을 명시하고, HTTP Method (GET , POST, PUT, DELETE )을 통해 해당 자원을 제어하는 명령을 내리는 방식의 아키텍처

### REST 구성

- 자원 (Resource)  - URI
- 행위 (Verb)  - HTTP Method
- 표현 (Representations)
- 잘 표현된 HTTP URI로 리소스를 정의하고 HTTP Method로 리소스에 대한 행위를 정의한다.
- 리소스는 JSON, XML과 같은 여러 가지 언어로 표현할 수 있다.

![image](https://user-images.githubusercontent.com/67090601/139593918-1968d219-ef9c-4401-bc7d-81af7c2a55ea.png)



### REST 특징

- 기존의 전송방식과는 달리 서버는 요청으로 받은 리소스에 대해 순수한 데이터를 전송한다.
- 기존의 GET/POST 외에 PUT, DELETE 방식을 사용하여 리소스에 대한 CRUD 처리를 할 수 있다.
- HTTP URI를 통애 제어할 자원을 명시하고, HTTP METHOD를 통해 해당 자원을 제어하는 명령을 내리는 방식의 Architecture이다
- 가장 큰 단점은 딱 정해진 표준이 없어 '다들 이렇게 쓰더라~~' 정도의 암묵적인 표준만 정해져 있다.

![image](https://user-images.githubusercontent.com/67090601/139594007-fb631321-7d7d-4992-8c8f-5ed3631765b9.png)

| annotation      | Description                                           |
| --------------- | ----------------------------------------------------- |
| @RestController | Controller가 REST 방식을 처리하기 위한 것임을 명시    |
| @ResponseBody   | JSP 같은 뷰로 전달되는 것이 아니라 데이터 자체를 전달 |
| @PathVariable   | URL 경로에 있는 값을 파라미터로 추출                  |
| @CrossOrigin    | Ajax의 크로스 도메인 문제를 해결                      |
| @RequestBody    | JSON 데이터를 원하는 타입으로 바인딩                  |

