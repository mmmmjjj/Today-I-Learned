## SpringFramework 등장 배경

- EJB를 사용하면 애플리케이션 작성을 쉽게 할 수 있다.

- 코드 수정 후 반영하는 과정 자체가 거창해 기능은 좋지만 효율성이 떨어진다.
- 점차 **POJO** + **경량 프레임워크**를 사용하기 시작
  - EJB서버와 같은 거창한 컨테이너가 필요 없다
  - 오픈 소스 프레임워크라서 사용 무료
  - 상당히 많은 라이브러리 지원
  - 모든 플랫폼에서 사용 가능
  - 웹 뿐만이 아니라 어플리케이션 등 모든 분야에 적용이 가능한 다양한 라이브러리 보유

> **POJO** (Plain Old Java Object)
>
> - 특정 프레임워크나 기술에 의존적이지 않은 자바 객체
> - 특정 기술에 종속적이지 않기 때문에 생산성 , 이식성 향상
> - Plain : 특정 프레임워크에 종속되지 않는 특징
> - old : EJB 이전의 java class를 의미

> **경량 프레임워크**
>
> - EJB가 제공하는 서비스를 지원해 줄 수 있는 프레임워크 등장
> - hibernate, JDO, MyBatis, Spring

## SpringFramework

- 엔터프라이즈 급 애플리케이션을 만들기 위한 모든 기능을 종합적으로 제공하는 경량화 솔루션
- 개발자가 복잡하고 실수하기 쉬운 low level에 신경 쓰지 않고 Business Logic 개발에 전념할 수 있도록 해준다.

## SpringFramework 구조

<img width="293" alt="스크린샷 2021-10-26 오후 8 20 01" src="https://user-images.githubusercontent.com/67090601/138876514-fdb702f8-83ca-48a1-bb82-f86526d27186.png">


- POJO (Plain Old Java Object)
  - 특정 프레임워크나 기술에 의존적이지 않은 자바 객체 (일반 자바 객체를 의미)
  - 특정 기술에 종속적이지 않기 때문에 생산성 향상, 테스트하기 용이
- PSA (Portable Service Abstraction)
  - 환경과 세부기술의 변경과 관계없이 일관된 방식으로 기술에 접근 할 수 있게 해주는 설계 원칙
  - 예를 들어 데이터베이스에 관계없이 동일하게 적용할 수 있는 트랜잭션 처리방식
- IoC / DI (Dependency Injection)
  - DI는 유연하게 확장 가능한 객체를 만들어 두고 객체 간의 의존관계는 외부에서 설정
- AOP (Aspect Oriented Programming)
  - 관심사의 분리를 통해서 소프트웨어의 모듈성을 향상
  - 공통 모듈을 여러 코드에 쉽게 적용 가능

<img width="1156" alt="스크린샷 2021-10-26 오후 8 27 37" src="https://user-images.githubusercontent.com/67090601/138876600-6f5adb0d-464c-4293-a6ff-a73498fd3f5d.png">

<img width="1212" alt="스크린샷 2021-10-26 오후 8 28 29" src="https://user-images.githubusercontent.com/67090601/138876621-d2bb84b2-1e77-495b-8f08-f1b8fd22e5aa.png">



## IoC (Inversion of Control)

- 객체 제어 방식
  - 기존 : 필요한 위치에서 개발자가 필요한 객체 생성 로직 구현
  - IoC : 객체 생성을 Container에게 위임하여 처리
- IoC 장점
  - **객체 간의 결합도를 떨어뜨릴 수 있음**
- 객체간 결합도가 높으면?
  - 해당 클래스가 유지보수 될 때 그 클래스의 결합된 다른 클래스도 같이 유지보수 해야 함

---

### 객체간 강한 결합 vs IoC

- **객체간 강한 결합**

  - 클래스 호출 방식
  - 클래스내에 선언과 구현이 모두 되어 있기 때문에 다양한 형태로 변화 불가능

<img width="402" alt="image-20211026204847955" src="https://user-images.githubusercontent.com/67090601/138877030-37b20139-a66d-4de6-97f8-4039c1b30162.png">

<img width="638" alt="스크린샷 2021-10-26 오후 8 46 14" src="https://user-images.githubusercontent.com/67090601/138877111-72ded087-a961-4964-8d76-3d2510b03862.png">


MemberService가 교체되거나 내부 코드가 변경되면 HomeController까지 수정해야 함

- **IoC**

  - 인터페이스 호출 방식
  - 구현 클래스 교체가 용이하여 다양한 형태로 변화 가능
  - 인터페이스 교체 시는 호출 클래스도 수정해야 함
<img width="398" alt="스크린샷 2021-10-26 오후 8 51 07" src="https://user-images.githubusercontent.com/67090601/138877213-7f8c9eed-883f-4cc9-9b9f-25285ac7e12b.png">
<img width="1177" alt="스크린샷 2021-10-26 오후 8 52 11" src="https://user-images.githubusercontent.com/67090601/138877243-33bf0d38-c478-4bcf-ac0e-788ecde7affd.png">


- **Spring**

  - 객체 간의 강한 결합을 assembler를 통해 결합도를 낮춤
  - IoC 호출 방식
  - 팩토리 패턴의 장점을 더하여 어떠한 것에도 의존하지 않는 형태가 됨
  - 실행시점에 클래스 간의 관계가 형성
  - Spring container가 외부조립기 (assembler) 역할을 함

<img width="735" alt="스크린샷 2021-10-26 오후 9 00 03" src="https://user-images.githubusercontent.com/67090601/138877281-28b63bfb-995d-49d5-b981-7d706bb08cae.png">

<img width="1208" alt="스크린샷 2021-10-26 오후 9 02 09" src="https://user-images.githubusercontent.com/67090601/138877327-96c9ccce-b785-4a2e-84c4-732a4bd3738d.png">

---

<img width="598" alt="스크린샷 2021-10-26 오후 8 31 37" src="https://user-images.githubusercontent.com/67090601/138877374-64fab9fb-ffcd-4f56-9eb0-1f81844c0d9a.png">

### IoC 종류

#### dependency lookup

- 컨테이너가 lookup context를 통해서 필요한 resource를 얻는 방식
- Lookup 한 object를 필요한 타입으로 casting 해 주어야 함

#### dependency injection

- 컨테이너가 직접 의존 구조를 object에 설정 할 수 있도록 지정해주는 방식
- object가 컨테이너의 존재 여부를 알 필요가 없음
- Lookup 관련 코드들이 object내에서 사라짐
- setter , constructor 사용

## container

- 객체의 생성, 사용, 소멸에 해당하는 라이프사이클 담당
- 라이프사이클을 기본으로 애플리케이션 사용에 필요한 주요 기능 제공
- Ex) 톰캣 (servlet-container, spring container)

##### 기능

- 라이프사이클 관리
- Dependency 객체 제공
- thread 관리

##### 필요성

- 비즈니스 로직 외에 부가적인 기능들에 대해서는 독립적으로 관리되도록 하기 위함
- 서비스 look up이나 configuration에 대한 일관성을 갖기 위함
- 서비스 객체를 사용하기 위해 각각 factory나 singleton 패턴을 직접 구현하지 않아도 됨

#### Spring DI Container

- spring DI container가 관리하는 객체 : Bean
- 이 빈들의 생명주기를 관리하는 의미로 빈팩토리라고 한다. (BeanFactory)

<img width="1136" alt="스크린샷 2021-10-26 오후 8 39 41" src="https://user-images.githubusercontent.com/67090601/138877427-a447e3f4-3915-42a8-b516-9290a9c93de4.png">

## Spring DI 용어 정리

- 빈 (bean)

  - 스프링이 IoC 방식으로 관리하는 오브젝트
  - 스프링이 직접 그 생성과 제어를 담당하는 오브젝트만을 bean이라 한다.
- 빈 팩토리 (BeanFactory)
  - 스프링이 IoC를 담당하는 핵심 컨테이너
  - Bean을 등록, 생성, 조회, 반환하는 기능을 담당
  - 일반적으로 beanfactory를 바로 사용하지 않고 이를 확장한 applicationContext 이용
- 애플리케이션 컨텍스트 (ApplicationContext)
  - beanfactory를 확장한 IoC 컨테이너이다.
  - xml파일에 <bean>을 추가해서 관리, annotation도 사용
  - bean을 등록하고 관리하는 기본적인 기능은 beanfactory와 동일
  - 스프링이 제공하는 각종 부가 서비스를 추가로 제공
  - 빈팩토리라고 부를 때는 주로 빈의 생성과 제어의 관점에서 이야기 할 경우,
  - 애플리케이션 컨텍스트라고 할 때는 스프링이 제공하는 애플리케이션 지원 기능을 모두 포함해서 이야기 하는 것
- 설정정보 / 설정 메타 정보 (configuration metadata)
  - applicaionContext 또는 BeanFactory가 IoC를 적용하기 위해 사용하는 메타정보

 <img width="1092" alt="스크린샷 2021-10-26 오후 9 09 19" src="https://user-images.githubusercontent.com/67090601/138877472-97d2083d-e457-4f1a-9234-ff0b6c6af1b6.png">
