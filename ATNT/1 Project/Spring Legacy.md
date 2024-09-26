

----
##### 연결 문서

- 
- 
- 
---

##### Spring Legacy

- 스프링 레거시란?
	- 과거에 개발된 시스템으로 새로운 기술과 새로운 방법론을 도입하지 않고 
	  오래동안 운영되어온 시스템을 의미한다. 
##### Setting
1. 사용 기술 스텍
	- 사용 라이브러리
		- lombok
			- 자바 코드에서 반복적인 코드를 줄이고 간결하게 만들어준다.  
		- thymeleaf
			- 서버 사이드에서 HTML을 만드는데 사용되는 템플릿 엔진이다.
				- 템플릿 엔진 : 동적으로 HTML을 생성할 수 있게 해주는 도구
			- 타임리프는 자연스러운 HTML 문법을 제공
				- HTML 문법 그대로 사용하기 때문에 HTML 파일을 직접 작성할때와 크게 다르지 않다. 
			- 서버 사이드 렌더링
				- 타임리프는 서버 측에서 HTML을 생성한다. 즉 서버에서
				  데이터를 받아와서 HTML을 동적으로 생성한 후 클라이언트에 전달
				  하는 방식이다. 이는 DB에서 가져온 정보나 사용자의 입력에 따라
				  다른 내용을 보여줄 때 유용하다.
			- 스프링과 통합 
				- 타임리프는 스프링과 잘 통합되어 있어서 스프링 웹 MVC와 함께
				  사용하면 컨트롤러에서 전달한 데이터를 타임리프 템플릿에서
				  쉽게 사용할 수 있다.
			- 편리한 동적 데이터 바인딩
				- 타임리프는 변수나 반복문, 조건문 등을 템플릿 내에서 자연스럽게
				  사용 할 수 있다.
			- 다양한 기능 지원
				- 폼 데이터 처리, 국제화(i18n), 자바스크립트 인라인 처리 등
				  다양한 기능을 제공하여 웹 어플리케이션 개발을 편리하게 해준다.
		- thymeleaf-spring6
			- 타임리프와 스프링 프레임워크의 최신 버전을 지원하는 모듈
			- 주요 특징
				- 스프링 MVC와의 통합
				- 폼 처리
				- 국제화(i18n) 지원
				- 스프링 시큐리티와의 통합
					- 스프링 시큐리티와 함꼐 사용하여 인증과 권한 부여를
					  템플릿 레벨에서 처리할 수 있다.
		- spring-webmvc
			- 스프링에서 웹 어플리케이션을 개발할 때 필요한 MVC 아키텍처를 제공
		- spring-jdbc
			- 스프링에서 제공하는 JDBC 추상화 레이어로 
			  데이터베이스와의 간편한 상호작용을 지원
		- spring-security-web
			- 웹 보안을 처리하는 스프링 모듈로
			  인증, 인가를 담당
		- spring-security-config
			- 스프링 시큐리티 설정을 구성하는데 필요한 도구
		- spring-security-taglibs
			- 스프링 시큐리티와 연동하여 보안 관련 태그를 제공
		- mysql-connector-j
			- MySQL 데이터베이스와의 연결을 위한 JDBC 드라이버
		- mybatis
			- 데이터베이스 연동을 담당하는 ORM 프레임워크로 SQL 매핑을 간소화한다.
		- mybatis-spring
			- 마이바티스와 스프링프레임워크의 통합을 지원한다.
		- jakarta.servlet-api
			- 자카르타 서블릿 API는 웹 애플리케이션 개발을 위한 Java 표준 API로, 
			  HTTP 요청을 처리하고 클라이언트에게 응답을 보내는 역할을 한다. HttpServlet을 상속받아 서블릿 클래스를 구현하여 사용하며, 
			  웹 애플리케이션의 핵심 기능을 구현하는 데 중요한 역할을 합니다.
		- jackson-databind
			- JSON 데이터를 자바 객체로 바인딩하는데 사용된다.
		- jackson-core
			- 잭슨 라이브러리의 핵심 모듈, JSON 데이터 처리를 담당한다.
		
	- 사용 기술 스텍
		- Inteli J
			IDE로서 프로젝트 개발 및 디버깅, 빌드 등을 효율적으로 관리한다.
		- Java
			주요 프로그래밍 언어로써 전체 프로젝트를 개발한다.
		- Tomcat
			서블릿 컨테이너로서 웹 어플리케이션을 실행할 수 있게 해준다.
		- mysql
			관계형 데이터베이스로 데이터 저장 및 관리를 담당한다.
	
2. setting.xml
	- web.xml
		- 정의
			- 웹 애플리케이션에서 사용되는 배포 설명자 파일이다.
			- XML 형식으로 사용되며, 웹 에플리케이션의 설정과 구성을 정의하는데 사용
			- 어플리케이션 서버에 의해 읽혀지고, 웹 애플리케이션의 동작 방식과 다양한 설정들을 지정하는 역할
			  
		- 제공할 수 있는 구성 정보들
			- 서블릿 메핑
				- 요청 URL을 보고 어떠한 서블릿이 해당 요청을 처리할지 설정
				- 이 정보를 통해 웹 애플리케이션은 특정한 URL 을 처리할 수 있다.
				- 예제 코드
			- 보안 제약
				- 특정한 리소스에 접근할 때 인증 혹은 인가를 요구하도록 설정
				- 사용자에 대한 역할 및 어떤 사용자를 허가할 것인지도 포함할 수 있다.
			- 에러 페이지
				- 404나 500 응답 시 노출되는 에러 페이지를 설정
			- 초기화 파라미터
				- 자바 웹 앱이 초기화 될 때 전달할 정보를 정의한다.
			- 필터
				- 요청과 응답을 가로채 공통 로직을 적용하는 필터를 정의한다.
				- 인증, 로깅, 입력값 검증 등에 사용된다.
			- 세션 구성
				- HTTP 세션에 대한 옵션을 구성한다.
				- 세션 타임아웃이나 쿠키 타임아웃 같은 것을 설정한다.
			- 마임 타입 매핑
				- 파일 확장자와 마임 타입 사이 매핑을 구성한다.
			
		- web-app
			- web.xml 가장 상위 수준의 루트 요소
			- 배포 설명자를 정의하는 역할
			- 이 요소내에 서블릿, 필터, 리스너, 초기화 파라미터, 보안 제약 등
			  웹 애플리케이션의 모든 정보를 포함한다.
			  
		- context-param
			- 애플리케이션 전역 설정
				- web.xml 파일에서 웹 어플리케이션 전역에서 사용할 수있는 초기화 파라미터를 정의 하는데 사용
			- 초기화 파라미터
				- 이러한 파라미터는 웹 어플리케이션의 모든 서블릿과 JSP페이지에서 접근할 수 있으며, 애플리케이션 전체에 걸쳐 공통적으로 사용되는 설정 값을 제공하는데 유용하다.
				  
			- pram-name
				- 초기화 파라미터의 이름을 지정
				- 이 이름은 고유해야 한다.
				- 애플리케이션의 다른 부분에서 해당 초기화 파라미터를 참조할 때 사용된다.
				- 예시
					- 데이터베이스 연결 문자열, 파일 경로, 최대 업로드 크기 등의 설정 이름으로 사용된다.
					  
			- pram-value
				- 초기화 파라미터의 값을 지정한다.
				- 이 값은 pram-name과 쌍을 이루어 설정 값을 제공한다.
				- 예시
					- 데이터베이스 URL, 파일 경로 문자열, 정수값 등 실제 설정 값을 포함한다.
			  
		- listener
			- Java EE 웹 애플리케이션에서 특정 이벤트가 발생할 때 
			  자동으로 실행되는 클래스를 정의하는 데 사용
			  
			- 주요 역할
				- 애플리케이션 라이프사이클 관리
				- 세션 관리
				- 요청 처리
			  
			- 주요 리스너 인터페이스
				- **ServletContextListener**: 애플리케이션 시작과 종료 시 이벤트를 처리.
				- **HttpSessionListener**: 세션 생성과 소멸 시 이벤트를 처리.
				- **HttpSessionAttributeListener**: 세션 속성의 변경 시 이벤트를 처리.
				- **ServletRequestListener**: 요청 생성과 소멸 시 이벤트를 처리.
				- **ServletRequestAttributeListener**: 요청 속성의 변경 시 이벤트를 처리.
			  
			- listener-class
				- 역할
					- **리스너 지정**: 특정 이벤트를 처리하기 위해 사용되는 리스너 클래스를 지정
					- **이벤트 처리**: 지정된 리스너 클래스는 애플리케이션의 시작, 종료, 세션 생성, 세션 소멸, 요청 생성 등 다양한 이벤트를 처리
			
		- servlet
			- servlet-name
			- servlet-class
			- init-param
			- param-name
			- param-value
		- servlet-mapping
			- servlet-name
			- url-pattern
		- filter
			- filter-name
			- filter-class
		- filter-mapping
			- filter-name
			- url-pattern
	- apllication-context.xml
		- beans
		- context:property-placeholder
			- location
		- bean
			- property
		- driverClassName
			- property name="driverClassName" value="${datasource.driver}"
			- property name="url" value="${datasource.url}"
			- property name="username" value="${datasource.username}"
			- property name="password" value="${datasource.password}"
		- dataSource
			- property name="dataSource" ref="dataSource"
			- property name="configLocation" value="classpath:mybatis/config/mybatis-config.xml"
			- property name="mapperLocations" value="classpath:mybatis/mappers/*Mapper.xml"
		- sqlSessionFactory
			- constructor-arg name="sqlSessionFactory" ref="sqlSessionFactoryBean"
		- webexpressionHandler
		- mvc:resources
			- mapping="/resources/**" location="classpath:/static/css/
	- dispatcher-servlet.xml
		- mvc:annotation-driven
		- templateResolver
			- property name="prefix" value="/WEB-INF/templates/"
			- property name="suffix" value=".html"
		- templateEngine
			- property name="templateResolver" ref="templateResolver"
		- org.thymeleaf.spring6.view.ThymeleafViewResolver
			- id는 따로없기에 class로 명명하겠다.
			- property name="templateEngine" ref="templateEngine"
			- property name="contentType" value="text/html"
			- property name="characterEncoding" value="UTF-8"
		- context:component-scan base-package="com.nc13.spring_legacy"
	- security-context.xml
		- mvc:annotation-driven
		- context:component-scan base-package="com.nc13.spring_legacy.service"
		- authHandler
		- passwordEncoder
		- security:http auto-config="true" use-expressions="true" pattern="/**"
			- security:intercept-url pattern="/" access="permitAll()"
			- security:intercept-url pattern="/user/**" access="permitAll()"
			- security:intercept-url pattern="/favicon.ico" access="hasRole('ROLE_ANONYMOUS')"
			- security:intercept-url pattern="/resources/**" access="permitAll()"
			- security:intercept-url pattern="/board/**" access="isAuthenticated()"
			- security:form-login  
		        login-page="/"  
		        login-processing-url="/logIn"  
		        username-parameter="username"  
		        password-parameter="password"  
		        default-target-url="/board/showAll"
		    - security:logout  
		        logout-url="/logOut"  
		        logout-success-url="/"  
		        delete-cookies="JSESSIONID"
		    - security:remember-me  
		        token-validity-seconds="604800"  
		        data-source-ref="dataSource"
		- security:authentication-manager
			- security:authentication-provider user-service-ref="customDetailService"
				- security:password-encoder ref="passwordEncoder"
	
3. 코드 설계 과정
	- 
