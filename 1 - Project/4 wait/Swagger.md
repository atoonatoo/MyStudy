---
created: 2024-01-04
updated: 2024-09-19
---
----
##### 연결 문서

- 
- 
- 
---

# **README**

- RestFul API를 설계하고 문서화하는 **오픈 소스 프레임워크**이다.
- Swagger는 API의 구조를 명확하게 정의하고, API 사용 방법을 문서로 자동 생성할 수 있게 도와준다.
- 이를 통해 개발자나 클라이언트가 API를 쉽게 이해하고 사용할 수 있다.

### 주요 기능

- **API 문서 자동 생성
	- Swagger는 API 코드에 주석을 달거나 OpenAPI 스펙을 작성하면 **자동으로 API 문서를 생성**한다. 
	- 이를 통해 사용자는 웹 브라우저에서 API의 각 엔드포인트, 요청 방법(GET, POST 등), 파라미터, 응답 등을 한눈에 볼 수 있다.
	  
- **인터프렉티브 API 테스트
	- Swagger UI 라는 도구를 통해, API 문서를 웹 인터페이스로 제공하고, **API를 바로 테스트**할 수 있는 기능을 제공한다.
	- 브라우저에서 직접 API 요청을 보내고 응답을 확인할 수 있어, 테스트와 디버깅이 간편하다.
	  
- **API 정의 표준화
	- Swagger는 API를 정의하는 표준인 **OpenAPI 스펙**을 따른다.
	- 이 스펙을 통해 API를 문서화하고, 클라이언트와 서버 간의 의사소통을 쉽게 할 수 있다.

### Swagger 사용 흐름
- **Swagger 설정
	Spring Boot 프로젝트에서 Swagger를 사용하려면, 
	주로 `springdoc-openapi` 라이브러리를 사용하여 Swagger 설정을 추가한다.
- **Swagger 주석 추가**
	API 코드에 주석을 추가하여 각 엔드포인트의 설명, 요청 파라미터, 응답 상태 코드 등을 정의한다.
- **Swagger UI 사용**:
	Swagger UI는 `/swagger-ui.html` 경로에서 웹 인터페이스를 제공하며, 
	이곳에서 문서화된 API를 보고 테스트할 수 있습니다.

- **의존성 추가 (Maven)
```xml
<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-ui</artifactId>
    <version>1.5.9</version>
</dependency>

```

- **API 컨트롤러 주석
```java
import io.swagger.v3.oas.annotations.Operation;
import io.swagger.v3.oas.annotations.responses.ApiResponse;
import io.swagger.v3.oas.annotations.responses.ApiResponses;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api")
public class UserController {

    @Operation(summary = "회원 가입")
    @ApiResponses(value = {
        @ApiResponse(responseCode = "200", description = "회원 가입 성공"),
        @ApiResponse(responseCode = "400", description = "잘못된 요청")
    })
    @PostMapping("/users")
    public ResponseEntity<String> createUser(@RequestBody UserModel userModel) {
        // 로직
        return ResponseEntity.ok("User created");
    }
}

```
### 참고 문서

- 스웨거 사용법 및 설치법 
	- https://jforj.tistory.com/394