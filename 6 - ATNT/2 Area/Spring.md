

----
##### 연결 문서

- 
- 
- 
---

##### 제목 : 

스프링
스프링이란?
URL 기반 웹 프로젝트 개발을 위한 프레임워크

프레임워크란?
프로젝트에 기본적인 뼈대를 만들어주는 클래스들의 집합(=라이브러리)

스프링의 주요 개념
1. Ioc
Inversion of Control
제어의 역전
지금까지 객체의 생성과 초기화는 누가?
"내가"
UserController userController = new UserController();
이것이 역전된다면?
스프링 프레임워크가 직접 객체의 생성과 초기화를 담당하게 된다.
우리가 해줄 것은?
해당 객체가 어떤 역할을 해줄지만 "정의"해주면 된다.

어노테이션을 사용한 처리
우리가 롬복에서 체험했던 @Data와 같은 어노테이션을
스프링프레임워크에서도 사용하게 되는데,
각각의 클래스의 종류와 해당객체의 주입등을 어노테이션을 사용하여
처리를 하게 된다.

Dependency Injection
의존성 주입
우리가 해주었던 의존성 주입(생성자를 통한 주입/셋터를 통한 주입)도
이제는 스프링 프레임워크에서 어노테이션을 통하여 의존성 주입을
자동으로 하게 된다.

- Spring IOC
    
    ```java
    - IOC : Inversion of Control | 제어의 역전
    	* "프로그램의 제어를 다른 대상에게 맡긴다."
    	
    	* Spring 컨테이너 :  "Bean을 생성, 의존관계주입과 같은 작업을 담당한다."
    		여기서 Spring 컨테이너는 ApplicationContext이며, Ioc 컨테이너 혹은 DI 컨테이너라고 부른다.
    		주요 기능 : 내가 작성한 코드를 제어하고, 대신 실행한다.
    
    	* DI : Dependency Injection | 의존관계주입 : 
    		여기서 말하는 의존은 객체 간의 의존을 의미한다.
    		"한 클래스(A)가 다른 클래스(B)의 메서드를 실행할 때, A 클래스가 B 클래스에 의존한다."라고 표현한다.
    		
    		1) 예시 : 
    			 회원가입 예시로 MemberService 클래스에서 구현한다고 가정한다.
    			 이때, 기능이 MemberRepository에 있어 회원 가입 MemberRepository의 메서드 save()가 필요하다면, 
    			 MemberService 클래스는 MemberRepository 클래스에 의존한다고 표현할 수 있다. 
    	
    		2) DI는 IOC의 대표적인 기능으로 의존하는 객체를 직접 생성하는 대신, 의존 객체를 전달받는 방식을 사용한다.
    			 의존관계주입을 할 때엔 DIP, OCP 원칙에 위배하지 않도록, 인터페이스(추상 클래스)에 의존하도록 해야 한다.
    			 
    		3) 의존 관계 주입은 @Autowired 어노테이션을 이용하며, 의존관계를 주입하는 방법은 크게 세 가지가 있다.
    			 (1) 생성자 주입 : 
    			 (2) 수정자(Setter) 주입 : 
    			 (3) 필드 주입 : 
    			 // 생성자 주입이 가장 추천되는 방법이다.
    
    - BeanFactory와 ApplicationContext : 
    	* BeanFactory는 스프링 컨테이너와 최상위 인터페이스이며, 스프링 Bean을 관리하고 조회하는 역할을 한다.
    	  .getBean()과 같은 기능은 BeanFactory가 지원하는 기능이다.
    	
    	* ApplicationContext는 BeanFactory 기능을 모두 상속받아서 제공한다.
    		Spring Bean을 관리 & 조회하는 기능 외에도 앱 개발에 필요한 편리한 부가 기능을 제공한다. 
    		BeanFactory는 거의 사용하지 않고, ApplicationContext를 사용하기 때문에 
    		"ApplicationContext를 Spring 컨테이너라고 부른다."
    
    	* Java 설정 클래스를 기반으로 스프링 컨테이너를 만들 수 있다. 
    		new AnotationConfigApplicationContext(AppConfig.class) => ApplicationContext 인터페이스 구현체
    	
    	* SingleTon 패턴이란 클래스의 인스턴스가 딱 1개만 생성되는 것을 보장하는 디자인 패턴이다.
    		Spring 컨테이너는 SingleTon을 적용하지 않아도, 객체 인스턴스를 SingleTon으로 관리한다.
    		Bean(객체)를 Spring 컨테이너에 등록하고, Bean 조회 요청 시 새로 생성하지 않고, 
    		Spring 컨테이너에서 Bean을 찾아서 반환한다.
    
    - Spring 컨테이너의 생성과 Bean 등록 과정 : 
    	1. Spring 컨테이너 생성 : 
    		 // 스프링 컨테이너 생성 - 구성 정보로 AppConfig.class로 설정
    		 ApplicationContext ac = new AnnotationConfigApplicationContext(AppConfig.class);
    		 이 코드를 통해 Spring 컨테이너를 생성할 수 있다. 
    		 이때 매개변수로 구성 정보를 전달해야 한다.
    		 Spring 컨테이너를 생성한 후, 구성 정보(AppConfig.class)를 활용한다.
    	
    	2. Spring Bean 등록 : 
    		 AppConfig.class에서 등록했던 Bean 정보를 참고하여 Spring 컨테이너를 저장한다.
    		 Spring 컨테이너는 <key : Bean 이름, value : Bean 객체> 형태로 Bean을 저장한다.
    		 key(Bean 이름)은 메서드의 이름으로 사용하고, return하는 실제 객체를 value(Bean 객체)에 저장한다.
    
    	3. Spring Bean 의존관계 등록 : 
    		 Spring 컨테이너가 설정 정보 (AppConfig.class)를 참고해서 의존 관계 주입(DI)를 한다.
    
    - Spring 컨테이너는 어떻게 객체들을 SingleTon으로 관리할 수 있는가? : 
    	* "Spring은 @Configuration이 붙은 클래스를 설정 정보로 사용한다." 
    	
    	* AppConfig라는 클래스에 @Configuration을 추가했다고 가정하자
    		Spring은 CGLIB이라는 바이트코드를 조작하는 라이브러리를 사용해서 AppConfig를 상속받은 
    		다른 클래스(AppConfig@CGLIB)를 사용한다.
    		그리고 이 클래스(AppConfig@CGLIB)를 Spring Bean으로 등록한다. 
    		그리고 이 클래스의 Bean들을 SingleTon이 되도록 보장해준다. 
    	
    		Spring 컨테이너에서 AppConfig를 .getBean()을 통해 꺼내보면 
    		class hello.core.AppConfig$$EnhancerBySpringCGLIB$$bd479d70와 같이 CGLIB에 의해 바뀐 것을 볼 수 있다.
    		만일 AppConfig에 @Configuration을 뺀다면 Bean들이 SingleTon으로 관리되지 않는 것을 볼 수 있다.
    ```
    
- Spring AOP
    
    ```java
    - AOP : Aspect Oriented Programming | 관점 지향 프로그래밍
    	* "어떤 로직을 기준으로 핵심적인 관점, 부가적인 관점으로 나누어서 보고 그 관점을 기준으로 각각 모듈하는 것."
    
    	* 핵심적인 관점 : 개발자가 적용하고자 하는 핵심 비지니스 로직
    		부과적인 관점 : 핵심 비지니스 로직을 실행하기 위해서 행해지는 DB 연결, 로깅, 파일 입출력 등을 말한다.
    
    	* AOP는 각 관점을 기준으로 모듈화한다는 것은 코드들을 부분적으로 나누어서 모듈화하겠다는 의미
    		이때 코드상에서 다른 부분에 계속 반복해서 쓰는 코드들을 발견할 수 있는데 
    		이것을 "흩어진 관심사(Cross Cutting Concern)"라 부른다.
    
    	* AOP의 주요 개념 : 
    		1) Aspect : 흩어진 관심사를 모듈화 한것, 주로 부가기능을 모듈화함.
    		2) Target : Aspect를 적용하는 곳(Class, Method..)
    		3) Advice : 실질적으로 어떤 일을 해야할 지에 대한것, 실질적인 부가기능을 담은 구현체 .
    		4) JointPoint : Advice가 적용될 위치, 끼어들 수 있는 지점, 메서드 진입 지점, 생성자 호출 지점, 
    										필드에서 값을 가져올 때 등 다양한 시점에 적용가능.
    		5) PointCut : JointPoint의 상세한 스펙을 정의하는 것. 'A란 메서드의 진입 시점에 호출한 것'과 같이 더욱
    									구체적으로 Advice가 실행될 지점을 정할 수 있음.
    
    	* 스프링 AOP의 특징 : 
    		1) 프록시 패턴 기반의 AOP 구현체, 프록시 객체를 쓰는 이유는 접근 제어 및 부가기능을 추가하기 위해서이다.
    		2) 스프링 빈에만 AOP를 적용 가능
    		3) 모든 AOP 기능을 제공하는 것이 아닌 스프링 IOC와 연동하여 엔터프라이즈 어플리케이션에서 
    			 가장 흔한 문제(중복코드, 프록시 클래스 작성의 번거로움, 객체들 간 관계 복잡도 증가..)
    			 에 대한 해결책을 지원하는 것이 목적
    	
    	* 스프링 AOP : @AOP 
    		// 스프링 AOP를 사용하기 위해선 다음과 같은 의존성을 추가해야 한다.
    		<dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-aop</artifactId>
    		</dependency>
    ```
    
    - AOP 그림 예시
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/11b23e09-5eeb-440a-86c3-5fb272d32444/b89a1e1f-076c-446d-951d-1013a8317a84/Untitled.png)
    
- Spring PSA
    
    ```java
    - PSA : Portable Service Abstraction. | 휴대용 서비스 추상화
    	* "서비스의 내용을 몰라도 서비스를 사용할 수 있다."
    
    	* 추상화란 하위 시스템의 공통점을 뽑아내서 잘 분리시키는 것을 말하고, 
    		이를 통해 하위 시스템을 알지 못하거나 변경이 있더라도 일관된 방식으로 접근할 수 있게 한다.
    		뿐만 아니라 서비스 추상화를 함으로써 '단일 책임 원칙'을 준수하며 코드가 간결해지고
    		작업 목적이 분명하게 드러나 객체 지향적인 코드를 작성할 수 있다.
    
    	* PSA의 예시 : 
    		Spring Web MVC를 예시로 개발자가 Class를 만들고 해당 클래스에 @Controller 어노테이션을 작성하여
    		컨트롤러 역할을 하는 클래스를 만든다. 
    		그래서 @GetMapping이나 @PostMapping으로 요청을 매핑하여 사용한다.
    		그러데 원래 Servlet을 사용하기 위해선 HttpServlet을 상속받고 
    		doGet()이나 doPost()를 구현하는 작업이 필요하다.
    		하지만 우리는 별도의 작업 없이 간편하게 서비스를 이용하고 있다.
    		즉, "Servlet에 대해 잘 몰라도 @Controller 어노테이션을 사용해서 Servlet을 만들어서 이용"하고있다.
    		이처럼 Service Abstraction의 목적 중 하나가 이러한 편의성을 제공하는 것이다.
    
    	* 정리 : 
    		서비스 추상화는 추상화 계층을 활용하여 어떤 기술을 내부에 숨기고 개발자에게 편의성을 제공하는 것.
    		서비스 추상화로 제공되는 기술을 다른 기술 스택으로 간편하게 바꿀 수 있는 
    		확장성을 갖고 있는 것을 PSA라고 한다.
    ```
    
- Spring이란?
    
    ```java
    1. 스프링은 자바 언어의 기반 프레임워크
    
    2. 자바 언어의 가장 큰 특징 : 객체지향언어 
    
    3. 스프링은 자바 언어가 가진 강력한 특징을 살려내는 프레임워크
    
    4. 스프링은 좋은 객체지향 어플리케이션을 개발할 수 있게 도와주는 프레임워크
    
    - 좋은 객체 지향이란? : 
    	* 추상화
    	* 캡슐화 
    	* 상속
    	* 다형성
      * 높은 응집도, 낮은 결합
    
    5. 스프링은 의존성 주입을 통해 객체간의 의존성을 느슨하게 해준다. 
    	 이는 객체간의 결합도를 감소시켜주고 유연성과 재사용성이 용이해지며
    	 테스트에도 모의 객체나 테스트 의존성을 주입함으로써 
    	 유닛 테스트와 통합테스트가 수행하기 쉬워진다.
    
    ```
    
- Spring이 만들어진 이유
    
    ```java
    - Spring은 왜 만들어졌을까…?
    
    1. EJB 프레임워크
       2000년대 초반, EJB라는 기술이 있었고 당시에 설정에 의한 트렌젝션 관리, 
    	 분산기술 (서비스, dao같은)을 사용하느게 장점이었다, orm 기술은 자바 객체를 
    	 디비에 저장하기 편하게 만들었다.
     
    2. 단점
     - 복잡하고 어렵고 느리다
     - 컨테이너 한번 돌리는데 오래 걸림
     - 오죽 힘들었으면 (POJO) plan old java object라는 말이 나옴
    
    3. EJB에 빡친 개발자들
      - 2002년에 로드 존슨이 책을 출간
      - EJB 없이도 충분히 고품질의 확장 가능한 어플리케이션을 개발할 수 있음을 
    		보여주었다. (예제를 30,000라인)이상으로 작업
      - 그러자 다른 개발자들도 예제를 실제 자기 서비스에 도입
      - 그래서 이 상황을 봤던 유겐 휠러, 얀 카로프 라는 사람이 존슨에게 오픈 소스 
    		프로젝트를 제안
      - 겨울을 넘어 새로운 시작이라는 뜻으로 SPRING이라 작명
     
    4. 하이버네이트 개발 
      - EJB 엔티티빈 기술을 대체, JPA의 새로운 표준 정의
    
    5. 그 이후에 EJB회사에 자신들의 기술보다 하이버 네이트가 더 많이 사용됨을 
       인정하여 하이버 네이트를 만든 개발자들을 데려와서 거의 하이버 네이트를 
    	 복붙하듯 만든 기술이 바로 JPA	
    
    6. SPRING의 강점
      
    	- POJO : 라이브러리나 프레임워크의 영향을 안받는 종속성이 없는 순수 자바 객체
      
    	- AOP : (관점지향프로그래밍) 개발자들이 코드를 작성, 관리하는데 반복적으로 
    		발생하는 공통의 관심사인 횡단관심사(트랜잭션, 보안, 캐싱, 예외처리, 
    		로깅 등)를 관리하는데 도움을 주며 개발자가 비지니스 로직에만 집중할 수 
    		있도록 해준다.
      
    	- 편리한 MVC 구조 
    		* Model : 
    			- 어플리케이샨의 데이터이며, 모든 데이터의 정보를 가공하여 가지고있는 
    			  컴포넌트이다.
    			- 사용자가 이용하려는 모든 데이터를 가지고 있어야한다.
    			- View 또는 Controller에 대해 어떤 정보도 알 수 없어야 한다.
    		* View : 
    			- 시각적인 UI 요소를 지칭하는 용어이다.
    			- 모델이 가지고 있는 데이터를 저장하면 안된다.
    			- 모델이나 컨트롤러에 대한 정보를 알면 안되며, 단순 표시의 역할만 
    				가지고있다.
    		* Controller :
    			- 모과 뷰를 연결해주는 역할
    			- 모델과 뷰에 대한 정보를 알아야 한다.
    			- 모델과 뷰 변경을 인지하여 대처해야 한다.
    		* MVC 아키텍처는 각 구성 요소(모델, 뷰, 컨트롤러)가 독립적으로 동하도록 
    			설계되어 어플리케이션을 효율적으로 구축하고 유지보수하는데 도움을 준다.
    
    	- WAS에 독립적인 개발 환경 : 
    		* 웹서버는 정적인 데이터를 처리하 서버로 단순 이미 HTML을 처리하는 서버이며, 
    		  WAS(Web Application Server)는 동적인 데이터를 처리하는 서버로 
    		  DB 연동 데이터 조작등과 같은 처리를 WAS에서 한다.
    		* 스프링 Boot 기본 내장 WAS는 Apache Tomcat이다.
    		* @SpringBootApplication을 실행하면 자동으로 웹 서버가 실행된다.
    		  주의할 점은 스프링부트가 웹 서버 그 자체가 아니다. 스프링부트는 
    			스프링을 편하게 사용하기 위한 툴에 불과, 웹 서버가 실행된다 함은 
    			스프링부트가 내장된 웹서버를 자동으로 구동한다는 의미이다.
    		* 스프링부트의 내장 WAS를 꼭 사용해야하는 것은 아니고 자유롭게 변경이 
    			가능하다.
    		* 정리 SPRING이 제공하는 기능이 프로그래로 하여금 편리하게 개발 할 수 
    			있도록 한다. 비지니스 로직에만 집중할 수 있게 해주는 것이다.
    ```
    
- Spring과 SpringBoot의 차이
    
    ```java
    - Spring, Spring Boot의 차이
     
    	* 웹프로그램(component)은 항상 Server의 내부 Container안에 존재하여야 한다.
    		
        1. 스프링
    		  1) 기존 스프링 레거시 프로젝트의 경우 추가적으로 web.xml설정, war구조, 
    				 배포관리 등등 was서버를 설치 및 설정을 해주어야만 하는 번거로움이 
    				 존재함.
    			2) 스스로 특정 기술의 라이브러리를 선택하고, 버전 호환성을 확인하여 
    				 수동으로 추가해야하는 번거로움이 존재.
    			3) 스프링은 더 유연하고, 더 다양한 커스터마이징에 초점
        
        2. 스프링부트
    		  1) 하지만 스프링부트의 경우 내장되어 있는 was와 초기설정들 덕분에
    		     개발자가 was를 학습하여 설치하고, 실행 및 관하는 개발자의 수고를 제거
    			2) 스프링부트는 Web, DB연동, Security, Batch 등 같은 기술에 필요한 여러 
    			   선택자들 중 꼭 필요하고 적합하다고 판단되는 라이브러들을 미리 정해놓고 
    				 상위 호환되는 버전을 결정하여 개발자에게 제공해 준다.
    			3) 스프링부트는 시대에 변화에 맞춰 어플리케이션 개발의 더 빠르고 효율적인 
    				 방법을 제공하는데 초점을 두었다.
    ```
    
    
- 컴포넌트 스캔
    
    ```java
    - 컴포넌트 스캔 : 스프링 IOC 컨테이너에 등록될 컴포넌트(또는 빈)들을 
    	자동으로 검색하고 등록하는 프로세스를 말한다. 
    	이 프로세스를 통해 스프링 애플리케이션은 필요한 컴포넌트를 자동으로 찾아서 
    	관리하며, 각 컴포넌트는 스프링 애플리케이션에서 사용할 수 있는 기능을 
    	제공합니다.
    ```
    
- Spring 컴포넌트 어노테이션
    
    ```java
    - @Controller : 웹어플리케이션의 컨트롤러 역할을 하는 클래스를 표시
    	* RequestMapping
    	* MVC방식 기능(Model, ModelAndview)
    	* HTTP 요청(GET, POST, PUT, DELETE) 
    
    - @Service : 비지니스 로직을 수행하는 서비스 클래스를 표시
    	* 트랜잭션 관리
    	* 예외 처리
    
    - @Repository : 데이터 엑세스와 관리된 클래스를 표시
    	* CURD 작업
    	* 쿼리 작성
    	* 예외 처리
    ```


    
- Spring 핵심 기술
    
    ```java
    # Spring DI 컨테이너 : 
     
    # Spring AOP : 
    
    # Spring Event : 
    ```
    
- Spring 웹 기술
    
    ```java
    1. 
    2. 
    3. 
    4. 
    5. 
    ```
    
- Spring 데이터 접근 기술
    
    ```java
    1. 
    2. 
    3. 
    4. 
    5. 
    ```
    
- Spring 기술 통합
    
    ```java
    1. 
    2. 
    3. 
    4. 
    5. 
    ```
    
- Spring 테스트
    
    ```java
    1. 
    2. 
    3. 
    4. 
    5. 
    ```
    
- Spring 언어
    
    ```java
    1. 
    2. 
    3. 
    4. 
    5. 
    ```
    
- Spring DI 컨테이너 기술
    
    ```java
    1. 
    2. 
    3. 
    4. 
    5. 
    ```
    
- Spring 프레임워크
    
    ```java
    1. 
    2. 
    3. 
    4. 
    5. 
    ```
    
- Spring Boot
    
    ```java
    1. 
    2. 
    3. 
    4. 
    5. 
    ```
    
- Spring Data
    
    ```java
    1. 
    2. 
    3. 
    4. 
    5. 
    ```
    
- Spring Session
    
    ```java
    1. 
    2. 
    3. 
    4. 
    5. 
    ```
    
- Spring Security
    
    ```java
    1. 
    2. 
    3. 
    4. 
    5. 
    ```
    
- Spring Rest Doc
    
    ```java
    1. 
    2. 
    3. 
    4. 
    5. 
    ```
    
- Spring Batch
    
    ```java
    1. 
    2. 
    3. 
    4. 
    5. 
    ```
    
- Spring Cloud
    
    ```java
    1. 
    2. 
    3. 
    4. 
    5. 
    ```
    
- Spring 빌드 도구