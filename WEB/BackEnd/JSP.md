

## 📌 JSP

![image](https://user-images.githubusercontent.com/67090601/136660959-2db8a9cf-4b3e-46eb-83d8-0b6063201247.png)

- HTML내에 자바 코드를 삽입하여 웹 서버에서 동적으로 웹페이지를 생성하여 웹 브라우저에 돌려주는 언어.
- 웹 애플리케이션 서버에서 동작한다.
- 실행 시 자바 서블릿으로 변환된 후 실행된다. (초기에 단 한번만 변환)

### 💡 JSP 스크립팅 요소

1. 선언 (Declaration)
> 멤버변수 선언이나 메소드를 선언하는 영역

`<%! 멤버변수와 method작성 %>`

```jsp
<%!
String name;

public void init(){
    name = "홍길동";
}
%>
```
2. 스크립트릿 (Scriptlet)
> Client 요청 시 매번 호출 영역, Servlet으로 변환 시 service()에 해당하는 영역 <br> request, response에 관련된 코드 구현

`<% java code %>`

3. 표현식 (Expression)
> 데이터를 브라우저에 출력할 때 사용

`<%= 문자열%>`

- 문자열 뒤 세미콜론은 작성하지 않는다.
- `<%=문자열%>` == `<% out.print(문자열); %>`

4. 주석 (Comment)
> 코드 상에서 부가 설명을 작성

`<%-- 주석할코드 --%>`

> 자바 주석과 HTML주석을 섞어서 사용하면 안된다!<br> 자바코드와 HTML코드를 분리해서 코딩해야 한다는 의미<br>자바가 먼저 돈다.

### 💡 JSP 지시자 (Directive)

![image](https://user-images.githubusercontent.com/67090601/136661754-8a446179-a627-43f8-b369-742d2ece543f.png)

### 💡 Web Page 이동방법

![image](https://user-images.githubusercontent.com/67090601/136661706-070ae045-c72b-4f15-9872-86e31cd7f44a.png)

1. forward(request, response)
- 내용 그대로 전달
- path로 이동
- 내 프로젝트 안에서만 이동 가능.
> contextroot 붙이면 X 

2. sendRedirect(URL)
- 동일 서버 포함 타 URL 가능
> contextroot까지 써야한다.


> JSP에선 doget, dopost 구분할 필요가 없다.
> request, response, out 이런걸 선언하지 않도고 사용가능. 자동으로 생성되는 기본객체다. (내장객체)
>session 의 기본값 : true
