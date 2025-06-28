

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
	- 결과
		- 8080
			- 로그인 요청 수: 1157
			- 2025-06-28T21:30:52.487+09:00  WARN 26528 --- [l-1 housekeeper] com.zaxxer.hikari.pool.HikariPool        : HikariPool-1 - Thread starvation or clock leap detected (housekeeper delta=7m29s920ms590µs700ns).
		- 8081
			- 로그인 요청 수: 1631
			- 2025-06-28T21:30:53.965+09:00  WARN 66156 --- [l-1 housekeeper] com.zaxxer.hikari.pool.HikariPool        : HikariPool-1 - Thread starvation or clock leap detected (housekeeper delta=7m29s925ms881µs900ns).
		- 8082
			- 로그인 요청 수: 1245
			- 2025-06-28T21:30:54.890+09:00  WARN 37160 --- [l-1 housekeeper] com.zaxxer.hikari.pool.HikariPool        : HikariPool-1 - Thread starvation or clock leap detected (housekeeper delta=7m29s922ms375µs100ns).
		- 8083
			- 로그인 요청 수: 1180
			- 2025-06-28T21:30:56.129+09:00  WARN 29716 --- [l-1 housekeeper] com.zaxxer.hikari.pool.HikariPool        : HikariPool-1 - Thread starvation or clock leap detected (housekeeper delta=7m29s917ms485µs).
		- 8084
			- 로그인 요청 수: 1587
			- 2025-06-28T21:30:57.859+09:00  WARN 14068 --- [l-1 housekeeper] com.zaxxer.hikari.pool.HikariPool        : HikariPool-1 - Thread starvation or clock leap detected (housekeeper delta=7m29s927ms578µs500ns).
		- 8085
			- 로그인 요청 수: 1081
			- 2025-06-28T21:31:02.065+09:00  WARN 65480 --- [l-1 housekeeper] com.zaxxer.hikari.pool.HikariPool        : HikariPool-1 - Thread starvation or clock leap detected (housekeeper delta=7m29s917ms877µs).
		- 8086
			- 로그인 요청 수: 1192
			- 2025-06-28T21:30:50.788+09:00  WARN 64144 --- [l-1 housekeeper] com.zaxxer.hikari.pool.HikariPool        : HikariPool-1 - Thread starvation or clock leap detected (housekeeper delta=7m29s923ms768µs400ns).
		- 8087
			- 로그인 요청 수: 1302
			- 2025-06-28T21:31:01.345+09:00  WARN 47636 --- [l-1 housekeeper] com.zaxxer.hikari.pool.HikariPool        : HikariPool-1 - Thread starvation or clock leap detected (housekeeper delta=7m29s920ms524µs800ns).
		- 합계 : 10,375 (1,625건 누락 ! )
		- 결론 : 일치 하지 않는다. 



- 원인 분석

- 해결 과정

- 결과 확인

- 향후 조치 및 제안

---
