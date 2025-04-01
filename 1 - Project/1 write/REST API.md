
---
- [[CS]]
---
# REST API란?

REST API(Representational State Transfer API)는 네트워크 아키텍처의 한 형태로, Roy Fielding이 박사 논문에서 제안한 HTTP 프로토콜을 효과적으로 활용하기 위한 규약이다. REST API는 클라이언트와 서버 간의 통신을 효율적으로 수행할 수 있도록 설계되었다.

## 1. REST API의 필요성
### 1.1 웹 발전과 데이터 교환 필요성 증가
초창기 웹은 정적 페이지(HTML) 제공이 주 목적이었지만, 점점 동적 데이터 교환이 필수적으로 요구되었다. 다양한 클라이언트(웹, 모바일, IoT 등)가 서버와 데이터를 주고받아야 하며, 이를 위한 일관된 방식이 필요했다.

- **정적 페이지**: HTML, CSS 기반의 고정된 콘텐츠 제공
- **동적 페이지**: 사용자의 입력 및 실시간 데이터 교환 가능 (예: 게시판, 로그인, 채팅 등)

### 1.2 SOAP의 복잡성과 REST API의 등장
초기에는 SOAP(Simple Object Access Protocol)이 사용되었지만, 복잡한 XML 구조와 무거운 프로토콜로 인해 부담이 컸다.

- **SOAP의 단점**
  - XML 기반의 복잡한 문법 및 데이터 크기 증가
  - XML 파싱 속도 저하 및 개발 복잡성 증가
  - HTTP 외 다양한 프로토콜 지원으로 인한 구조 복잡성
  - 상태 저장 방식(Stateful)으로 인해 서버 부하 증가
  - 네트워크 트래픽 증가 및 성능 저하

이러한 문제를 해결하기 위해 REST API가 등장했다.

### 1.3 HTTP의 특성을 최대한 활용
REST는 HTTP의 기본 원칙(GET, POST, PUT, DELETE 등)을 활용하여 단순하고 직관적인 API 설계를 가능하게 했다. URL을 활용한 리소스 중심 설계로 시스템 간의 데이터 교환이 용이해졌다.

### 1.4 웹 서비스 간의 상호 운용성 향상
REST는 특정 기술이나 플랫폼에 종속되지 않으며, JSON, XML 등의 다양한 데이터 형식을 사용할 수 있어 범용성이 높다.

### 1.5 마이크로서비스 아키텍처와 API 중심 개발
기존의 Monolithic Architecture에서는 서비스들이 강하게 결합되어 유지보수가 어려웠지만, REST API를 활용하면 MicroService Architecture에서 독립적인 서비스들이 서로 쉽게 통신할 수 있다.

## 2. REST API의 장단점
### 2.1 장점
- **간결하고 직관적인 설계**: HTTP 메서드(GET, POST, PUT, DELETE)를 활용한 쉬운 API 설계
- **플랫폼 및 언어 독립적**: 특정 프로그래밍 언어에 종속되지 않고 다양한 환경에서 사용 가능
- **경량 프로토콜**: JSON을 기본적으로 사용하여 데이터 전송량이 적고 속도가 빠름
- **캐싱 지원**: HTTP 캐시 기능을 활용하여 성능 최적화 가능
- **확장성(Scalability)**: 서버 부담을 최소화하며 부하 분산이 용이
- **무상태성(Stateless)**: 각 요청이 독립적으로 처리되어 서버의 상태 유지 부담 감소
- **유연한 확장성**: 서비스 변경 및 확장이 용이하여 마이크로서비스 아키텍처(MSA)에 적합

### 2.2 단점
- **무상태성으로 인해 클라이언트가 상태를 직접 관리해야 함** (예: JWT, OAuth 등의 인증 필요)
- **표준이 강제되지 않아 API 설계 방식이 일관되지 않을 수 있음**
- **대량 데이터 전송 시 비효율적** (헤더와 메타데이터 포함으로 인한 데이터 크기 증가)
- **보안 처리 필요** (OAuth, JWT 등 인증 방식 적용 필요, CSRF 등의 보안 위협 고려 필요)
- **HTTP 프로토콜 의존적** (UDP 기반의 빠른 통신이 필요한 환경에는 적합하지 않음)

## 3. REST API의 원칙 및 규약
### 3.1 클라이언트-서버 구조(Client-Server Architecture)
클라이언트(사용자)와 서버(데이터 제공자)를 분리하여 독립적으로 동작할 수 있도록 한다.

**예시:**
```http
GET /users  # 사용자 목록 조회
Response: 200 OK
```

### 3.2 무상태성(Stateless)
각 HTTP 요청은 독립적으로 처리되며, 서버는 클라이언트의 상태를 저장하지 않는다. 따라서 클라이언트는 요청 시 필요한 모든 정보를 포함해야 한다.

**예시:**
```http
Authorization: Bearer <JWT_TOKEN>  # JWT를 활용한 인증 요청
```

### 3.3 캐시 가능(Cacheable)
클라이언트는 HTTP 캐시를 활용하여 서버 요청을 줄이고 응답 속도를 향상시킬 수 있다.

**예시:**
```http
Cache-Control: max-age=3600  # 1시간 동안 캐시 유지
```

### 3.4 계층화된 시스템(Layered System)
로드 밸런서, 프록시, API 게이트웨이 등을 활용하여 보안 및 성능을 최적화할 수 있다.

### 3.5 통일된 인터페이스(Uniform Interface)
RESTful API는 일관된 리소스 식별 방식(URL)과 표준 메서드(GET, POST, PUT, DELETE)를 사용한다.

```http
GET /users     # 사용자 목록 조회
POST /users    # 사용자 생성
PUT /users/1   # 특정 사용자 정보 수정
DELETE /users/1 # 특정 사용자 삭제
```

### 3.6 자기 서술적 메시지(Self-Descriptive Messages)
API 응답은 클라이언트가 요청한 데이터 형식(JSON, XML 등)으로 반환된다.

```http
Accept: application/json  # JSON 형식으로 응답 요청
Content-Type: application/json  # JSON 형식으로 데이터 전송
```

---

### 6. 참고 문헌

https://thdqudgns.tistory.com/39
https://dev-coco.tistory.com/97
https://hahahoho5915.tistory.com/54
https://jibinary.tistory.com/188#google_vignette
https://apidog.com/kr/blog/restful-api-vs-rest-api-2/
https://www.youtube.com/watch?v=RP_f5dMoHFc&t=372s&pp=ygUm64Sk7J2067KEIO2YhOyngeyekCByZXN0ZnVsIGFwaSDqsJXsl7A%3D
