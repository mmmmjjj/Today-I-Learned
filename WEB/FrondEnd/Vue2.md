## Vue의 문법

#### - 보간법 (Interpolation)

- 데이터 바인딩의 가장 기본 형태는 "mustache"구문을 사용한 텍스트 보간
  - {{ 속성명 }}

#### - 원시 HTML로 출력하기

- mustache는 HTML이 아닌 일반 텍스트로 데이터를 해석한다.
- 실제 HTML을 출력하려면 v-html 디렉티브를 사용해야 한다!

![image](https://user-images.githubusercontent.com/67090601/140873238-9ee319d6-f4f3-4b6e-8bf9-3ff010aeeda9.png)

#### - JavaScript 표현식을 사용한다.

- 모든 데이터 바인딩 내에서 javascript 표현식의 모든 기능을 지원한다.
- 단, 각 바인딩에 하나의 단일 표현식만 포함 될 수 있으므로 아래처럼 작성하면 안된다.

![image](https://user-images.githubusercontent.com/67090601/140873422-087cf124-615f-4506-8909-44257134d11d.png)

## 디렉티브 (Directives)

- **v-**접두사가 있는 특수 속성

- 디렉티브 속성 값은 단일 javascript 표현식이 된다. (v-for 예외)
- 표현식의 값이 변경될 때 사이드 이펙트를 반응적으로 DOM에 적용시킨다.

| 속성                    | 설명                                                         |
| ----------------------- | ------------------------------------------------------------ |
| v-model                 | 양방향 바인딩 처리를 위해서 사용 (form의 input이나, textarea) |
| v-bind ( : )            | 엘리먼트의 속성과 비인딩 처리를 위해서 사용<br /> 약어로 **:**로 사용 가능하다. |
| v-show                  | 조건에 따라 엘리먼트를 화면에 렌더링<br />style의 display를 변경한다. |
| v-if, v-else-if, v-else | 조건에 따라 엘리먼트를 화면에 렌더링                         |
| v-for                   | 배열이나 객체의 반복에 사용한다.<br />v-for="요소변수이름 in 배열"<br />v-for="(요소변수이름 , 인덱스 ) in 배열" |
| template                | 여러 개의 태그들을 묶어서 처리해야 할 경우 template를 사용<br />v-if, v-for, component 등과 함께 많이 사용한다. |
| v-cloak                 | 뷰 인스턴스가 준비될 때까지 mustache 바인딩을 숨기는 데 사용 |

