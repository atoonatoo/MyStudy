

---
- [[0 Home]]
---

- 문제 요약
	- 비교적 작은 부하에도 로그인 응답시간에 지연이 발생한다.

---
- 환경 정보
  - `운영체제`: `Windows 11 Home 24H2 (OS 빌드 26100.4484)`
  - `시스템`: `64비트 운영 체제, x64 기반 프로세서`
  - `프로세서`: `Intel(R) Core(TM) Ultra 5 125H (3.60GHz)`
  - `RAM` : `16.0 GB`
  - `Java`: `17.0.12 (LTS, build 17.0.12+8-LTS-286)`
  - `Spring Boot` : `3.3.4`
  - `Gradle Java Toolchain` : `Java 17`
  - `Spring`
    - `spring-boot-starter-web`
    - `spring-boot-starter-security`
    - `spring-boot-starter-data-jpa`
    - `springdoc-openapi 2.0.2`
    - `QueryDSL 5.0.0 (jakarta)`
    - `Spring Actuator, Validation`
  - `JMeter` : `Apache JMeter 5.6.3`
---

- 시도한 방법
	- 서버가 받은 요청수와 클라이언트가 요청한 수 같은 지를 비교한다.
	- `attemptAuthentication(로그인 요청 시 인증을 시도하는 메서드)`에 요청 수를 console로 찍는다.

- `- 2025-06-28T21:31:02.065+09:00 WARN 65480 --- [l-1 housekeeper] com.zaxxer.hikari.pool.HikariPool : HikariPool-1 - Thread starvation or clock leap detected (housekeeper delta=7m29s917ms877µs).`

| 포트   | 로그인 수 | 포트   | 로그인 수 |
| ---- | ----- | ---- | ----- |
| 8080 | 1157  | 8081 | 1631  |
| 8082 | 1245  | 8083 | 1180  |
| 8084 | 1587  | 8085 | 1081  |
| 8086 | 1192  | 8087 | 1302  |

- 클라이언트
	- 클라이언트가 보낸 요청 수 : 12,000건
	- 성공 요청수 : xxx건
	- 에러율 : xxx%
	- 누락된 요청 수 : xxx건
- 서버
	- 서버가 실제로 받은 요청 수 : 10,375건
	- 서버 누락된 요청 수 : 1,625건
- 결과
	- 클라이언트 에러율로 인한 누락 요청 수가 일치하는 것을 확인



- 원인 분석

- 해결 과정

- 결과 확인

- 향후 조치 및 제안

---
