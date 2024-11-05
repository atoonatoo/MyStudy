---
created:
---
---
# **README**

- 참고 자료 - 개발자 유미 Security 강의
	- https://www.youtube.com/playlist?list=PLJkjrxxiBSFCcOjy0AAVGNtIa08VLk1EJ
### Intro
- 시작하기 전..
  
	팀프로젝트를 진행하며 회원을 담당하게 되었다.
	MSA 프로젝트를 진행하기 때문에 CORS 에러를 해결하는 과정해서 더 중요한 사실을 놓쳤다는걸 꺠달았다. 로그인 후 응답 값을 JSON으로 반드시 변환해야 하는데, 시큐리티의 formlogin 방식은  html로 반환 된다. 여러 가지 시행 착오를 겪었고, 다음과 같은 사실을 인지했다.
	1. JSON 객체로 반환하기 위해선 formlogin을 비활성화 해야한다.
	2. formlogin을 대처하기위해 기존의 시큐리티 메서드를 커스터마이징을 해야한다.
	3. JWT을 반드시 사용해야 한다.
	4. 내가 위의 과정을 해결하기 위해서는 반드시 Security의 충분히 깊은 이해가 필요하다.
	
	그렇게 다음과 같은 글 작성은 내가 시큐리티를 공부하기 위해 유튜브, 인강을 보여 학습하고 올바르게 이해를 돕기 위해 기록하는 과정이다.

# Spring Security 

1. **실습 목표 
	- Spring Security를 활용하여 
1. 
### Spring Security

- **1. 실습 목표**
	- 스프링 시큐리티 프레임워크를 활용하여 인증/인가를 구현하고 회원 정보 저장(영속성)은 MYSQL DB를 활용하여 구현한다.
		
	- 구현
		- 인증 : 로그인
		- 인가 : 경로별 접근 권한
		- 회원가입
		
	- 시큐리티 동작 원리
		- 스프링부트 어플리케이션은 Servelt Container 위에 존재하게 된다.
		1. Clinet 요청 
		2. Servelt Container의 Filter를 거친다. 
		3. Filter를 거친 후 스프링부트 컨트롤러에 요청에 도달하게 된다.
		4. SecurityConifg라는 파일을 만들고 설정을 한다.
		5. Config는 특정한 Filter를 만들고 Client의 요청을 가로챈다. 
		6. 가로챈 후에 이 Client의 가고 싶어하는 목적지에 가기전에 목적지로 가기위해 필요한 특정한 권한이 있는지 검증한다.
	- 예시
		- ex) ADMIN으로 가고자 할 때 ADMIN의 권한이 없다면 그 Filter에서 막힌다.
		
		- ex) 로그인을 진행해야 한다. Filter에서 모든 유저의 접근 권한을 해제하고, 로그인 Controller에 간 뒤에, 로그인을 진행하고 그 Session에 로그인에 성공한 유저의 정보가 등록되게 된다. 그후, 메인 Controller, Mypage Controller 등 특정 유저의 권한이 필요한 페이지에 접근할 때 SecurityConfig가 Session에 유저가 등록 되었기 때문에 Filter에서 통과를 허용시켜서 Mypage의 Controller로 접근할 수 있게 된다.
		
	- JWT 로그인 방식
		1. from 로그인 방식을 사용하지 않고 커스터마이징하여 직접 작업을 해야한다.
		2. Authentication filter
		3. Authentication Manager 회원 검증
		4. Authentication Manager는 UserDetailsService로 DB에 저장된 회원을 가져와 검증 
		5. UserDetailsService는 DB에 정보를 가져와 UserDetailes에 담아 Authentication Manager로 보낸다.
		6. 회원 검증에 성공할 경우 SuccessFullAuthentication를 통해서
		7. JWTUtil에서 토큰을 만들고 Response로 응답을 보낸다.
		
		- 로그인 동작 원리![[Pasted image 20241104140847.png]]
		
	- 경로 접근 인가
		- ADMIN, MyPage 등 특정한 경로를 접근 하기 위해 Header에 넣고 요청을 진행해야한다.
		  
		- 검증 방식
			1. security filter에 검증 진행
			2. 우리가 직접 커스터마이징한 JWT filter 검증을 진행
			3. token이 알맞게 존재하고, token 내부의 정보가 정확히 일치한다면, SecurityContextHolder를 통해 일시적인 Session을 만든다.
			4.  token을 통해서 특정한 경로로 요청이 들어가면 session이 있기 때문에 접근이 가능해진다.
				- 단, 생성된 세션은 요청이 끝나면 소멸된다.
			  
			- 인가 동작 원리![[Pasted image 20241104140921.png]]
		
	- 기타
		- 스프링 시큐리티 JWT 구현 방법이 아주 많다. 개발자마다 구현 방식이 매우 많이 다를 수 있다. 최대한 공식 문서에 구현된 형태로 코드를 작성하지만, 구현은 다를 수 있다.
	
-  **2. 프로젝트 생성**
	-  강의 버전 
		- Spring Boot 3.2.1
		- Scurity 6.2.1
		- Lombok
		- Spring Data JPA - MySQL
		- Gradle - Groovy
		- inteliJ Ulitmate
		  
	- JWT 필수 의존성 
			- 대부분 JWT 0.11.5 버전을 통해 구현하지만, 최신 버전은 0.12.3이다.
			- 둘의 방식은 매우 다르다.
			  
		- 신버전 - 0.12.3
			- implementation 'io.jsonwebtoken:jjwt-api:0.12.3'  
			- implementation 'io.jsonwebtoken:jjwt-impl:0.12.3'  
			- implementation 'io.jsonwebtoken:jjwt-jackson:0.12.3'
			  
		- 구버전  - 0.11.5
			- implementation 'io.jsonwebtoken:jjwt-api:0.11.5'
			- implementation 'io.jsonwebtoken:jjwt-impl:0.11.5'
			- implementation 'io.jsonwebtoken:jjwt-jackson:0.11.5'
	
- **3.Security Config 설정**
	
	- SecurityConfig 클래스 설명
		- 스프링 시큐리티의 인가 및 설정을 담당하는 클래스이다.
		- Config의 구현은 시큐리티의 버전별로 많이 상이하다.
		- 이번 시리즈는 스프링 시큐리티 6.2.1 버전이다.
		  
	- 버전별 Security Config 구현 방법
		- https://www.youtube.com/watch?v=NdRVhOccuOs
	
- **4. POSTMAN **
	
	- API 서버는 웹서버와 달리 서버측으로 요청을 보낼 수 있는 페이지가 존재하지 않기 때문에 요청을 보낼 API 클라이언트가 필요하다.
	
- **5. DB 설정**
	
- **6. 회원가입 로직 구현**
	
	- lifeCycle
		- POST : join > (dto) > joinController > (dto) > joinService > User > UserRepository > DB(User)
		  
	- JoinDTO
		- 
	
- **7. 로그인 필터 구현**
	
	- UsernamePasswordAuthenticationFilter
	- AuthenticationMananger
	
	- 로그인 로직 구현 목표
		- 아이디, 비밀번호 검증을 위한 커스텀 필터 작성
		- DB에 저장되어 있는 회원 정보를 기반으로 검증할 로직 작성
		- 로그인 성공시 JWT를 반환할 success 핸들러 생성
		- 커스텀 필터 SecurityConfig
		  
	- 로그인 모식도![[Pasted image 20241104163108.png]]
	
- **3.**
	
- **3.**
	
- **3.**
	
- **3.**
	
- **3.**
