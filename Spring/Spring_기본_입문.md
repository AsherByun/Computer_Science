# 스프링 기본 입문

## 프레임워크 개념

사전적의미 : 뼈대, 틀 , 아키택쳐

이미 만들어진 틀을 사용하여 개발→ 일관성이 잘유지 되기때문에 유지보수에 좋음

### 장점

1. 빠른 구현시간

    코드 골격을 주기 때문에 개발자는 비즈니스 로직만 구현하면 된다

2. 쉬운 관리
3. 개발자들의 역량 획일화

    초보와 고수의 코드가 비슷해진다

4. 검증된 아키텍처의 재사용과 일관성 유지

### POJO (plain old java object)

평범한 자바객체 → servlet class와 같이 규칙에 맞게 만들어야 하는 클래스가 아닌 객체

→규칙에 맞춘 객체가아님 

### 스프링 프레임워크 장점

1. 경량

    → 여러개의 모듈로 구성되어 있으며, 하나 이상의 jar 파일로 구성되어 있다

    → POJO 형태의 객체를 관리하기 때문에 가볍다

2. 제어의 역행(IOC : Inversion of Control)

    → 비즈니스 컴포넌트를 개발할 때 신경써야 하는 것은 낮은 결합도와 높은 응집도

    → 스프링에서는 제어의 역행을 통해 객체간 느슨한 결합을 유지한다.

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ed8b5fdb-bd05-411c-8c51-4162ca9691fa/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ed8b5fdb-bd05-411c-8c51-4162ca9691fa/Untitled.png)

    객체생성을 자바코드로 직접 처리하는 것이 아닌 컨테이너가 대신 처리한다.

    객체와 객체 사이의 의존관계 역시 컨테이너가 처리한다→ 소스에 의존관계가 명시되지 않으므로 결합도가 떨어져 유지보수가 편해진다.

    3. 관점지향 프로그래밍(AOP: Aspect Oriented Programming)

    → 핵심 비즈니스 로직과 각 비즈니스 메소드마다 반복해서 등장하는 공통 로직을 분리함으로써 응집도가 높게 개발할 수 있다. (응집도 : 모듈 내부의 기능적인 집중도 높을수록 하나의 일을 수행?)

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2f90c19c-9636-47eb-8471-35b6007bca6a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2f90c19c-9636-47eb-8471-35b6007bca6a/Untitled.png)

    유지보수 측면에서 매우좋다.

    4. 컨테이너

    → 특정 객체의 생성과 관리(수명주기 등등)를 담당.

    → 일반적으로 서버 안에 포함되어 배포 및 구동된다

    (대표적인 컨테이너: servlet 컨테이너, EJB 컨테이너)

    ### IoC(Inversion of Control) 컨테이너

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6095af15-3578-4cbc-ba82-10696cee9785/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6095af15-3578-4cbc-ba82-10696cee9785/Untitled.png)

    ### 결합도 낮추기

    1. 다형성을 이용하자 → 모든 클래스가 같은 클래스를 갖도록 강제할 수 있다.
    2. 디자인 패턴 이용하기 ⇒ Factory 패턴

        Factory 패턴 : 객체 생성을 캡슐화 하여 서브 클래스에서 객체를 생성함.

        입력 값만 변경해주면된다 → 소스를 바꿀 필요가없어진다.

    ### 스프링 컨테이너 종류

    1. BeanFactory → <bean>객체를 생성하고 관리하는 가장 기본적인 컨테이너, 클라이언트의 요청에만 객체가 생성되는 지연로딩(Lazy loading) 방식을 사용하기 때문에 사용하지 않는다
    2. ApplicationContext→ 기본 객체관리 기능 이외에도 트랜잭션 관리, 메시지 기반의 다국어 처리등 다양한 기능을 지원한다. 또한 컨테이너 구동시점에 <bean>에 등록된 클래스들을 객체 생성하는 즉시 로딩(pre-loading) 방식으로 동작한다. (대부분사용)

    ApplicationContext 구현 클래스

    1. GenericXmlApllicationContext : 파일 시스템이나 클래스 경로에 있는 xml 설정파일을 로딩하여 구동하는 방식
    2. XmlWebApplicationContext : 웹기반의 스프링 애플리케이션을 개발할 때 사용하는 컨테이너

    ### <bean> 엘리먼트 속성

    객체생성시 컨테이너는 기본적으로 디폴트 생성자만 인식하기 때문에 초기화는 init-method를 사용한다.

    객체삭제전 호출되는 메소드 → destroy-method로 등록

    기본적으로 즉시 로딩방식이다 → 자주등장하지 않는 객체를 즉시로딩하면 메모리 낭비→ lazy-init 속성을 사용하여 요청시에만 객체를 생성한다.

    scope ="singleton" default가 싱글톤

    scope ="prototype" 은 매번 요청시마다 새로운 객체를 생성 반환한다

    ### 의존성 관리

    - Dependency Lookup → 컨테이너가 애플리케이션 운용에 필요한 객체를 생성하고 클라이언트는 컨테이너가 생성한 객체를 검색 하는 방법. →실제로 사용 x
    - Dependency Injection → 객체 사이의 의존관계를 스프링 설정 파일에 등록된 정보를 바탕으로 컨테이너가 자동으로 처리. 의존성 설정→스프링 설정파일만 수정→ 유지보수가 향상 → 직접 객체들 사이의 의존관계를 처리 → setter Injection & Constructor Injection

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4f3ffbe4-8402-42fc-b28f-bafffb931feb/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4f3ffbe4-8402-42fc-b28f-bafffb931feb/Untitled.png)

    ### 생성자 인젝션 사용

    ref에 객체의 id를 넣어준다.

    index="순서" 로 매개변수 순서를 지정해줄수있다.

    <bean id ="" class="">

    <constructor-arg ref = "매개변수 객체 id">

    ... 개수만큼 넣어준다.

    객체가아닌 고정된(int,String....)의 경우 ref 대신 value를 사용

    </bean>

    ### Setter 인젝션 사용

    constructor-arg대신 property사용

    name ⇒ 호출하고자하는 매소드의 이름

    ex) setSpeaker → name = "speaker
    ```
    <bean id ="" class="">

    <property name="" ref = "매개변수 객체 id">

    ... 개수만큼 넣어준다.

    객체가아닌 고정된(int,String....)의 경우 ref 대신 value를 사용

    </bean>
```
    ### p 네임스페이스 사용하기

    xmlns:p="http://www.springframework.org/schema/p" 추가

    p:변수명-ref="참조할 객체의 이름이나 아이디"

    p:변수명="설정할 값"

    ### 컬렉션(Collection) 객체 설정
```
    list → <list>, set →<set>, map → <map>, properties → <props>

    ex)

    <property name-"addressList">

    <list>

    <value>"asdfad"</value>

    <value>"asdfad"</value>

    </list>

    </property>
```