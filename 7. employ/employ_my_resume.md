---
title: undefined
type: Resume
director: My
date: 2025-10-20
tags:
  - programing
  - employment
  - resume
---

---

### JWT + Redis 기반 인증 아키텍처 설계
### QueryDSL을 통한 N+1 문제 제거 및 데이터 조회 최적화
### Redis 캐싱 전략 분리 및 세션 일관성 유지 설계
### HikariCP 연결 풀 관리 및 DBCP 튜닝
### Swagger UI(OpenAPI) 기반 협업 자동화 체계 구축
### GlobalExceptionHandler 기반 전역 예외 처리 표준화
### JMeter를 활용한 부하 테스트 및 성능 지표 분석
### Nginx 로드밸런싱 환경 구축 및 트래픽 분산 설계
### EFK 로그 파이프라인 구축 및 자동화 스크립트 구현
### GPT API 연동 및 사용자별 데이터 영속화 설계



---
- JWT + Redis 인증 구조
- AccessToken / RefreshToken 관리
- Redis TTL 캐싱 및 세션 일관성 유지
- UserDetailsServiceCustom 캐시
- QueryDSL 데이터 접근 최적화
- N+1 문제 제거
- PlaylistVideo 그룹 쿼리 최적화
- Redis 캐싱 분리(User: :, refresh:)
- GenericJackson2JsonRedisSerializer 직렬화
- HikariCP 풀 관리 및 모니터링
- GlobalExceptionHandler 전역 예외 처리
- ExceptionType Enum 표준화
- ModelMapper STRICT 매핑
- Swagger UI(OpenAPI) 자동 문서화
- API 스펙 협의(API Specification Alignment)
- JWT Authorize 기능 테스트
- JMeter 부하 테스트
- Nginx 로드밸런싱
- TPS / P95 / 에러율 측정
- EFK 로그 파이프라인 구축 (Filebeat → Elasticsearch → Kibana)
- Ingest Pipeline(grok/date) 정규화
- PowerShell 자동화 스크립트(start-efk.ps1)
- GPT API 연동 (Apache HttpClient5)
- 사용자별 요청/응답 영속화 (Gpt 엔티티)
- DDD 기반 도메인 구조화 (User, Playlist, Video, GPT)
- 비즈니스 규칙 검증 (수정·삭제 동시 불가)
- 실무형 백엔드 설계 역량, 안정성·성능·확장성 고려

---

- **시스템 아키텍처 설계 및 인증 구조 고도화**  
  - JWT + Redis 기반 인증 시스템 설계  
  - AccessToken과 RefreshToken 구조 분리, RefreshToken은 Redis에 TTL 7일 저장  
  - 로그아웃 시 토큰과 사용자 캐시(User: : email)를 동기 삭제하여 세션 일관성 유지  
  - UserDetailsServiceCustom 캐싱을 통해 로그인 시 DB 조회 최소화  
  - 결과 : 인증 속도 및 확장성 향상, Stateless 환경에서도 안정적인 로그인 유지  

- **QueryDSL 기반 데이터 접근 계층 최적화**  
  - PlaylistRepositoryImpl, PlaylistVideoRepositoryImpl을 QueryDSL로 구현  
  - Playlist-Video 관계를 findAllVideosGroupedByPlaylist() 단일 쿼리로 처리  
  - 결과 : N+1 문제 제거 및 쿼리 효율 약 80% 개선, 응답 속도 향상  

- **Redis 캐싱과 HikariCP 튜닝을 통한 성능 안정화**  
  - 사용자 캐시(User: :), 토큰 캐시(refresh:)를 분리하고 TTL 기반 자동 만료 관리  
  - GenericJackson2JsonRedisSerializer 적용으로 직렬화 안정성 확보  
  - HikariCP 풀 상태(active, idle, waiting) 모니터링으로 연결 누수 방지  
  - 결과 : DB 부하 약 35% 감소, 시스템 응답 시간 단축  

- **예외 처리 및 DTO 변환 표준화, Swagger UI를 통한 협업 효율 개선**  
  - GlobalExceptionHandler + ExceptionType Enum으로 에러 응답 일원화  
  - ModelMapperConfig를 STRICT 매칭으로 설정해 DTO 변환 정확성 확보  
  - Swagger UI(OpenAPI) 기반으로 API 명세 자동화 및 협업 체계 확립  
  - 요청과 응답 DTO 구조, 필드명, 타입, 예시(JSON) 자동 표시  
  - API 스펙 협의(API Specification Alignment)를 시각화하고 자동 반영  
  - JWT 인증 흐름을 Swagger Authorize 기능으로 테스트 가능  
  - 결과 : 프론트엔드 및 QA와의 API 소통 정확도 향상, 문서 관리 부담 감소  

- **JMeter + Nginx 기반 부하 테스트 및 트래픽 분산 설계**  
  - 1.2만 동시 접속 시나리오 구성, TPS·에러율·P95 지표 측정  
  - Nginx Reverse Proxy와 로드밸런싱 구조 검증  
  - 결과 : 평균 응답시간 40% 단축, Failover 성공률 100% 확보  

- **EFK 로그 수집 파이프라인 구축 및 자동화**  
  - Filebeat → Elasticsearch → Kibana 로그 중앙화 구성  
  - Grok, Date 기반 Ingest Pipeline으로 timestamp, traceId 정규화  
  - PowerShell 스크립트(start-efk.ps1)로 EFK 스택 원클릭 자동 기동  
  - 결과 : 실시간 로그 시각화 및 운영 비용 절감, ILM Hot/Warm/Delete 정책으로 저장 효율화  

- **GPT API 연동 및 사용자별 요청·응답 영속화**  
  - Apache HttpClient5로 OpenAI API 직접 호출 및 응답 파싱  
  - 사용자별 요청과 응답 데이터를 DB에 영속화(Gpt 엔티티)  
  - GptRequestException, InvalidGptRequestException으로 예외 세분화  
  - 결과 : 외부 AI 서비스 안정적 연동 및 대화형 Q&A 시스템 완성  

- **도메인 주도 설계(DDD) 기반 구조화**  
  - User, Playlist, Video, GPT 등 도메인별 패키지 구조와 책임 명확히 분리  
  - 서비스 레벨에서 비즈니스 규칙(예 : 수정과 삭제 동시 불가) 검증  
  - 결과 : 응집도 높은 구조로 유지보수성, 확장성, 가독성 강화  

- **요약**  
  - JWT + Redis 인증, QueryDSL 최적화, 캐싱·DBCP 튜닝, Swagger 협업 자동화, EFK 로깅, JMeter 부하 검증까지 구현  
  - 기능 구현을 넘어 API 스펙 협의(API Specification Alignment)와 시스템 안정성, 성능, 확장성을 모두 고려한 실무형 설계 역량 보유  

---

### **인증 및 사용자 정보 관리 기능 구현**

- MySQL 초기 세팅 및 DB 스키마 정의 및 관계 설정
- Spring Boot로 RESTful API 설계 및 구현하여 클라이언트 ↔ 서버 간 통신 구축
- Spring Security를 이용하여 로그인 기능 구현
    - JWT Token과 Refresh Token을 활용하여 짧은 인증 토큰 만료를 보완하고 자동 재발급 구조를 통해 보안성과 사용자 편의성 확보

### **플레이리스트 관리 기능 구현 및 설계**

- QueryDSL로 N+1 문제를 제거한 플레이리스트 ↔ 영상 일괄 조회 및 YouTube API 연동, 중복 검증, 트랜잭션 처리로 안정적인 CRUD 구현
- 성능 최적화(QueryDSL), 무결성 검증, 권한 검증, 페이징 및 DTO 분리 등 플레이리스트 전반 백엔드 로직 구축

### **OpenAI ChatGPT API 연동**

- 보안 컨텍스트 기반의 보호된 GPT Q&A API 설계
- OpenAI 호출, JSON 파싱, 예외 처리 흐름 표준화
- 유저별 이력 영속화로 운영 안정성 확보

### **부하 테스트 시나리오 설계 및 실행**

- Apache JMeter로 Thread Group, CSV Data Set, HTTP Sampler 구성 및 Aggregate/Graph 리스너 시각화
- TPS, P95/99, 에러율 중심으로 병목 구간 분석
- 로그인 요청 튜닝 후 에러율 **37.97% → 15.75%**, TPS **398,305ms → 7,988ms** 개선

### **로드 밸런싱 구축**

- Nginx 로드밸런서로 8개 인스턴스 트래픽 분산
- upstream 기반 재시도·타임아웃 설정으로 장애 전파 최소화

### **로그 수집 파이프라인 구축**

- Filebeat → Elasticsearch → Kibana 구성으로 애플리케이션/액세스 로그 중앙화
- JSON 파싱 + Ingest Pipeline(grok/date)으로 `timestamp`, `level`, `traceId` 정규화 및 서비스 단위 대시보드 구축

### **Database Connection Pool 튜닝**

- HikariCP의 `maximumPoolSize`, `connectionTimeout`, `idleTimeout`, `minimumIdle` 조정으로 풀 고갈·대기 시간 완화
- `leakDetectionThreshold` 활성화 및 `try-with-resources` 패턴 정착으로 커넥션 누수 제거

### **캐싱 도입**

- Redis 기반 읽기 캐시로 빈번 조회 엔드포인트 응답 속도 향상 및 DB 부하 감소
- TTL 전략(핵심 키 단기 TTL, 변경 시 캐시 무효화)으로 정합성 유지
- RedisTemplate 수동 캐시로 `UserDetailsServiceCustom#loadUserByUsername`의 `findByEmail` 결과를 `User::<email>`(TTL 120분)에 캐싱하여 인증 경로 변경 없이 조회 성능 향상


---

1. 부하테스트 툴
    - Jmeter
        - java 기반 언어로 스크립트를 짜는 툴
        - GUI, CLI 모두 지원
        - 메모리를 크게 잡아먹는 단점
    - k6
        - javascript 기반 테스트 스크립트 작성
        - CI/CD 통합으로 자동화된 성능 테스팅 파이프라인 지원
        - 테스트 엔진 : Go
        - 낮은 메모리 사용량과 높은 처리량
        - 