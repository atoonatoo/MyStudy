# 1. Spring Security?

Spring Security란 **Spring에서 제공해주는 인증 (Authentication)과 인가(Authorization)에 대한 처리를 위임하는 별도의 프레임워크이다.**

**Spring Security는 `인증`과 `인가`에 대한 부분을 `Fiter` 흐름에 따라 처리한다.**

`Filter`는 `Dispatcher Servlet` 으로 가기 전에 적용되므로 가장 먼저 URL 요청을 받는다.

Spring Security는 보안과 관련해서 쳬게적으로 많은 옵션을 제공해주기 때문에 개발자 입장에서는 일일이 보안관련 로직을 작성하지 않아도 된다는 장점이 존재한다.

---

# 2. Spring Security 동작 과정

- 아래의 그림은 스프링 시큐리티 프레임워크가 `인증`, `인가`를 어떻게 처리해주는지 흐름을 이해하고 만든 간단한 구조 그림이다.

앞서 이야기하였지만, Spring Security는 요청이 Dispatcher Servlet 으로 가기 전에 Filter 단에서 요청을 가로채 `인증`과 `인가`에 대한 처리를 해준다.

## 2.2 Http Request 가 Spring Controller 로 가는 과정

![](https://velog.velcdn.com/images/atoonatoo/post/a87477f8-9bb9-42e6-b1bb-fa28cc08c582/image.png)


![](https://velog.velcdn.com/images/atoonatoo/post/a8e59b6b-9260-4ac0-8676-2632d2dbe666/image.png)

---

## 2.1 Client Http Request와 Spring Security 간의 흐름

### 2.1 Spring Security Componant

1. AuthenticationFilter

2. UsernamePasswordAuthenticationToken

3. AuthenticationManager

4. AuthenticationProvider

5. ProviderManager

6. UserDetailsService

7. UserDetails

8. User

9. SecurityContextHolder

10. SecurityContextHolder

11. SecurityContext

12. Authentication

---

### 2.1.2 Spring Security Architecture

![](https://velog.velcdn.com/images/atoonatoo/post/06264ca8-f5ce-4c71-9628-bb50f05a8149/image.png)

1. 사용자가 로그인 정보(id, password) 로 로그인(인증)을 요청

2. AuthenticatinFliter가 (1) 의 정보를 가로채서 UsernamePasswordAuthentication Token(Authentication 객체)을 생성하여 AuthenticationManager에게 Authentication 객체를 
전달
3. AuthenticationManger 인터페이스를 거쳐 AuthenticationProvider에게 (2) 의 정보 전달(Authentication 형태), 등록된 AuthenticationProvider(들)을 조회하여 인증을 요구

4. AuthenticationProvider는 UserDetailService를 통해 입력받은 (3)의 사용자 정보를 DB에서 조회
	- supports() 메소드를 통해 실행 가능한지 체크
    - authentication() 메소드를 통해 DB에 저장된 이용자 정보와 입력된 로그인 정보 비교
    	- DB 이용자 정보 : UserDetailsService의 loadUserByUsername() 메소드를 통해 불러온다.
        - 입력 로그인 정보 : (3) 에서 받았던 Authentication 객체 (UsernameAuthentication Token)
	- 일치하는 경우 Authentication 반환        

5. QuthenticationManager 는 Authentication 객체를 AuthenticationFilter로 전달 

6. AuthenticationFilter는 전달받은 Authentication 객체를 LoginSuccessHandler로 전송하고, SecurityContextHolder에 담는다.

7. 결과
	- 성공시 AuthenticationSuccessHandle 실행
	- 실패시 AuthenticationFailureHandle 실행

---

# 3. Spring Security 적용 및 사용법



---


# 출처

1. https://thalals.tistory.com/436
2. https://wikidocs.net/162150
3. https://www.elancer.co.kr/blog/detail/235
4. https://velog.io/@hope0206/Spring-Security-%EA%B5%AC%EC%A1%B0-%ED%9D%90%EB%A6%84-%EA%B7%B8%EB%A6%AC%EA%B3%A0-%EC%97%AD%ED%95%A0-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0
5. https://www.youtube.com/watch?v=y0PXQgrkb90&list=PLJkjrxxiBSFCKD9TRKDYn7IE96K2u3C3U