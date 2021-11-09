## Vue.js

- 사용자 인터페이스를 만들기 위해 사용하는 오픈 소스 Progessive Framework
- 특징
  - Approachable (접근성)
  - Versatile (유연성)
  - Performant (고성능)

## MVVM Pattern

- **Model + View + ViewModel**
- Model : 순수 자바스크립트 객체
- View : 웹페이지의 DOM
- ViewModel : Vue의 역할
- 기존에는 자바스크립트로 view에 해당하는 DOM에 접근하거나 수정하기 위해 jQuery와 같은 라이브러리를 이용했지만, Vue는 view와 Model을 연결하고 자동으로 바인딩하므로 **양방향 통신**을 가능하게 한다.

![image](https://user-images.githubusercontent.com/67090601/140871313-a2c179b0-f510-44c6-908c-03394f605c45.png)

![image](https://user-images.githubusercontent.com/67090601/140871357-7b8186b1-7176-4385-a10d-a829b818e549.png)

## Vue 인스턴스

![image](https://user-images.githubusercontent.com/67090601/140871422-3504ec42-6feb-4dc5-adc9-3b6910504e9d.png)

| 속성     | 설명                                                         |
| -------- | ------------------------------------------------------------ |
| el       | Vue가 적용될 요소 지정                                       |
| data     | Vue에서 사용되는 정보 저장. 객체 또는 함수의 형태            |
| template | 화면에 표시할 HTML, CSS 등의 마크업 요소를 정의하는 속성<br />뷰의 데이터 및 기타 속성들도 함께 화면에 그릴 수 있다. |
| methods  | 화면 로직 제어와 관계된 메서드를 정의하는 속성.<br />마우스 클릭 이벤트 처리와 같이 화면의 전반적인 이벤트와 화면 동작과 관련된 로직 추가 |
| created  | 뷰 인스턴스가 생성되자마자 실행할 로직 정의                  |

### Vue 인스턴스의 유효범위

- HTML의 특정 범위 안에서만 옵션 속성들이 적용된다.
- el 속성과 밀접한 관계가 있다.

![image](https://user-images.githubusercontent.com/67090601/140871783-3df0393e-8b56-4d48-86f6-be6ecb2787c7.png)

![image](https://user-images.githubusercontent.com/67090601/140871943-89dc1292-3ce5-4b81-bcf0-9dbc58820273.png)

## Vue 인스턴스 Life Cycle

**생성** - **부착** - **갱신** - **소멸**

(인스턴스 = Vue Instance)

| life cycle 속성 | 설명                                                         |
| --------------- | ------------------------------------------------------------ |
| beforeCreate    | 인스턴스가 생성되고 각 정보의 설정 전에 호출. DOM과 같은 화면요소에 접근 불가 |
| created         | 인스턴스가 생성된 후 데이터들의 설정이 완료된 후 호출<br />인스턴스가 화면에 부착되기 전이기 때문에 template 속성에 정의된 DOM 요소는 접근 불가<br />서버에 데이터를 요청하여 받아오는 로직을 수행하기 좋다. |
| beforeMount     | 마운트가 시작되기 전에 호출                                  |
| mounted         | 지정된 element에 인스턴스 데이터가 마운트 된 후에 호출<br />template 속성에 정의한 화면 요소에 접근 할 수 있어 화면 요소를 제어하는 로직 수행 |
| beforeUpdate    | 데이터가 변경될 때 virtual DOM이 랜더링, 패치 되기 전에 호출 |
| updated         | Vue에서 관리되는 데이터가 변경되서 DOM이 업데이트 된 상태<br />데이터 변경후 화면 요소 제어와 관련된 로직 추가 |
| beforeDestroy   | 인스턴스가 제거되기 전에 호출                                |
| destroyed       | 인스턴스가 제거된 후에 호출                                  |



