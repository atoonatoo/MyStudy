---
title: portpolio version 1.1
type: resume
director: employ
date: 2025-10-31
tags:
  - programing
  - employment
  - resume
---
[[#1. 기술 후보군 정리]]
[[#2. 도구 별 키워드 정리]]
    [[#2.1 부하 테스트 도구]]
    [[#2.2 로드밸런서]]
    [[#2.3]]
[[#3. 분석]]
    [[#3.1 로드밸런서서]]

# 1. 기술 후보군 정리
- **부하 테스트 도구**  
    JMeter, k6, Locust, nGrinder
    
- **로그 수집기(저장소)**  
    Elasticsearch, OpenSearch, Loki, Graylog, ClickHouse, Splunk, Datadog, New Relic
    
- **로그 수집 에이전트(수집기)**  
    Filebeat, Fluent Bit, Vector, rsyslog, Logstash Forwarder
    
- **시각화 및 모니터링 도구**  
    Kibana, Grafana, OpenSearch Dashboards, Graylog Web UI, Datadog Dashboard
    
- **로드밸런서**  
    Nginx, HAProxy, AWS ALB, Traefik
    
- **데이터 접근 계층**  
    Spring Data JPA, MyBatis, JDBC Template, JOOQ
    
- **쿼리 빌더**  
    QueryDSL, JPQL, Criteria API, JOOQ
    
- **커넥션 풀 관리**  
    HikariCP, Apache DBCP2, Tomcat JDBC Pool, c3p0
    
- **캐싱 및 세션 관리**  
    Redis, Memcached, Caffeine, Hazelcast
    
- **인증 및 인가**  
    Spring Security, Apache Shiro, Keycloak, pac4j
    
- **생성형 AI 모델 API (LLM 서비스)**
    ChatGPT OpenAI API, Claude API, Gemini API
---

# 2. 도구 별 키워드 정리
## 2.1 부하 테스트 도구
### 2.2.1 Jmeter
#### 키워드
- `GUI에 특화된 초심자 친화적 테스트 도구`
- `다양한 프로토콜과 플러그인 지원`
- `GUI (XML)or CLI 기반 실행기`
- `다양한 리스너 기반 리포트 자동 생성 및 시각화`
- `JVM 스레드 기반으로 수천 ~ 수만 단위 동시 사용자까지 현실적 한계`
- `시나리오 단위 스레드 유지, 루프 종료 시 일괄 해제`

### 2.2.2 k6
#### 키워드
- `개발자 친화적 코드 기반 성능 테스트 도구`
- `JavaScript로 테스트 시나리오 작성 및 제어`
- `Go 엔진 + V8 JS 런타임 하이브리드 구조`
- `경량 Goroutine 기반 고성능 동시성 처리`
- `CLI 중심으로 CI/CD 자동화 및 DevOps 연동 용이`
- `멀티 환경 일관 실행 유연성`
- `다양한 성능, 통합 테스트 지원`
- `모니터링, 메시징, 관찰 도구와 폭 넓은 통합`
- `확장 가능한 오픈소스 구조`

### 2.2.3 nGrinder
#### 키워드
- `네이버 개발 오픈소스 부하 및 성능 테스트 도구`
- `조직 기업 단위의 대규모 팀 환경에 특화된 테스트 도구`
- `Java 기반 Controller-Agent 분산 아키텍처`
- `웹 UI로 테스트 관리, 모니터링, 리포트 제공`
- `Agent 확장만으로 대규모 부하 생성`
- `SVN 내장으로 스크립트 버전 관리 및 협업 지원`
- `Jython, Groovy 스크립트 기반 시나리오 구성`
- `실시간 TPS, 응답시간, 에러율 시각화 리포트`
- `테스트 비교, 회귀(Regression) 분석 기능 내장`
- `분산, 확장형 부하 테스트 환경 제공`

### 2.2.4 Locust
#### 키워드
- `Python 기반 코드형 부하 테스트 프레임워크`
- `가상 사용자(User Class)로 실제 사용자 행동 시뮬레이션`
- `@task, TaskSet 등으로 시나리오 가중치 및 흐름 제어`
- `HTTP, FastHTTP 클라이언트 제공 (requests 기반)`
- `Master-Worker 구조로 분산 부하 실행 가능`
- `웹 UI를 통한 실시간 모니터링 및 리포트 시각화`
- `on_start, wait_time 등으로 현실적 사용자 패턴 구현`
- `Python 생태계와 확장성 높은 통합 지원`
- `단순하면서도 대규모 테스트에 적합한 경량 아키텍처`

## 2.2 로드밸런서
- **Nginx**
    - `이벤트 기반 비동기 처리 방식`
    - `정적 파일 서빙 및 리버스 프록시 가능`
    - `로드밸런싱`
    - `L7, L4 라우팅 지원`
    - `콘텐츠 캐싱 및 압축, 최적화 지원`
    - `SSL/TLS 및 최신 HTTP 프로토콜 지원`
    
    - `Master Process & Worker Process`
    - `Web Server`
    - `Revers Proxy`
    - `Event-Driven Architecture`
    - `Scaling Mechanism`
    - `Module Architecture`
      
- **HAProxy**
    - `로드밸런서`
    - `L7, L4 라우팅 지원`
    - `다양한 로드밸런싱 알고리즘 및 세션 지속성 지원`
    - `헬스 체크 및 고가용성 (HA) 기능`
    - `SSL/TLS 종료(Off-loading) 및 최신 프로토콜 지원`
    - `고성능, 저지연 설계 및 리소스 효율성`
    - `ACL(Access Control List)을 통한 세밀한 트래픽 제어 가능`
    - `강력한 모니터링, 통계 기능 및 용이한 실시간 지표 확인`
    - `여러 환경(온-프레미스, 클라우드, 컨테이너 등)에서 유연하게 배치 가능.`
      
- **AWS ALB**
    - `로드 밸런서`
    - `L7 라우팅 지원`
    - `HTTP/HTTPS 및 HTTP/2, gRPC, WebSocket 지원`
    - `고급 콘텐츠 기반 라우팅 가능`
    - `SSL/TLS 종료 및 보안 통합 가능`
    - `자동 확장 및 고가용성, 대상 상태 감시`
    - `sticky session 지원`
    - `리디렉션 및 고정 응답 기능`
    - `온-프레미스/하이브리브 환경 지원`
      
- **Treafik**
    - `로드밸런서`
    - `L7, L4 라우팅 지원`
    - `자동 서비스 디스커버리 및 동적 설정`
    - `미들웨어 지원 및 관측 기능 내장`
    - `TLS/HTTP2/HTTP3 및 지원 강화`

## 2.3 중앙 집중형 로그 수집기 설계 및 시각화 환경 구축

### 2.3.1 로그 수집기 저장소
- **Elasticsearch**
    - `분산 수평 확장(Distributed & Scalable)`
    - `실시간 색인 및 검색(Real-time ingestion & search)`
    - `다양한 데이터 타입 지원(Heterogeneous data support)`
    - `RESTful API 및 풍부한 쿼리 DSL (RESTful API && Query DSL)`
    - `보안 및 고가용성(Security & High Availability)`
      
- **OpenSearch**
    - `분산 수평 확장(Distributed & Scalable)`
    - `벡터 검색 지원(Vector search)`
    - `다양한 쿼리 언어 지원(SQL/PPL/DSL)`
    - `보안 및 다중 테넌시 지원(Security & Mutil-tenant)`
    - `시각화 대시보드 통합(Visualization & Dashboards)`
      
- **Grafana Loki**
    - `수평확장·고가용성(Horizontally scalable & Highly available)`
    - `메타데이터 중심 인덱싱(Metadata-only indexing)`
    - `라벨 기반 인덱싱(Label-based indexing)`
    - `효율적 저장소·비용효율성(Efficient storage & Cost-effective)`
    - `전용 쿼리언어(LogQL query language)`
      
- **Graylog**
    - `중앙화 로그 수집·분석(Centralized log collection & analysis)`
    - `실시간 검색·탐색(Real-time search & exploration)`
    - `알림·상관 분석(Alerts & correlation analysis)`
    - `시각화 대시보드·컴플라이언스 대시(Visualization dashboards & compliance reporting)`
    - `확장 아키텍처·비용 통제(Scalable architecture & cost control)`

### 2.3.2 로그 수집 에이전트(수집기)
- **Filebeat**
    - `경량 에이전트(Lightweight agent)`
    - `파일 모니터링(Log-file monitoring)`
    - `모듈 지원(Modules support)`
    - `백프레셔 대응(Back-pressure handling)`
    - `클라우드·컨테이너 친화(Cloud & container ready)`  
      
- **Fluent Bit**
    - `초경량·고성능(Ultra-lightweight & high-performance)`
    - `다수 플러그인 지원(Multi-plugin ecosystem)`
    - `SQL유사 스트림 처리(SQL-style stream processing)`
    - `쿠버네티스·컨테이너 최적화(Kubernetes & container optimized)`
    - `내결함성·버퍼링(Error handling & buffering)`  
        
- **Vector**
    - `초고속·메모리효율(Blistering fast & memory efficient)`
    - `로그·메트릭 통합(Logs & metrics unified)`
    - `공급업체 중립(Vendor-neutral)`
    - `프로그래머블 변환(Programmable transforms)`
    - `에이전트·집계기 역할(Agent & aggregator roles)`  
        
- **rsyslog**
    - `표준 syslog 기반(Standard syslog support)`
    - `고성능 처리(High-performance processing)`
    - `모듈화 구조(Modular architecture)`
    - `유연한 필터링(Flexible filtering & routing)`
    - `TLS 및 신뢰성 확보(TLS & reliable transport)`  
        
- **Logstash Forwarder**
    - `경량 로그 포워더(Lightweight log forwarder)`
    - `SSL/TLS 지원(SSL/TLS secure transmission)`
    - `구성 파일 기반 설정(Config-file based configuration)`
    - `Logstash 연계(In tegration with Logstash)`
    - `커스텀 필드 지원(Custom fields per path)`  

### 2.3.3 시각화 모니터링 도구
- **Kibana**
    - `다양한 시각화(Visualization)`
    - `대시보드 구성(Dashboard creation)`
    - `지리공간 분석(Geo-spatial analysis)`
    - `데이터 탐색(Discover & Explore)`
    - `플러그인 및 앱 확장(Plugins & App extensions)`  
    
- **Grafana**
    - `다중데이터소스 통합(Multi-data-source integration)`
    - `인터랙티브 대시보드(Interactive dashboards)`
    - `알림 및 역할기반 접근(Alerting & RBAC)`
    - `플러그인 생태계(Plugin ecosystem)`
    - `실시간 시각화 및 탐색(Real-time visualization & exploration)`  
    
- **OpenSearch Dashboards**
    - `시각화 및 대시보드(Visualization & Dashboards)`
    - `보안·관찰 통합(Security & Observability)`
    - `오픈·확장 아키텍처(Open & Extensible architecture)`
    - `실시간 분석 및 탐색(Real-time analytics & exploration)`
    - `플러그인 및 워크스페이스 개발(Plugin & Workspace support)`  
    
- **Graylog Web UI**
    - `중앙화 로그 관리(Centralized log management)`
    - `실시간 검색(Real-time search)`
    - `대시보드·알림(Dashboards & Alerts)`
    - `확장 가능한 아키텍처(Scalable architecture)`
    - `플러그인 및 API 확장(Plugin & API extensibility)`  
    
- **Datadog Dashboard**
    - `실시간 모니터링(Real-time monitoring)`
    - `맞춤형 대시보드(Custom dashboards)`
    - `고해상도 메트릭 및 이벤트(High-resolution metrics & events)`
    - `위젯 기반 시각화(Widget-based visualizations)`
    - `다양한 데이터 연결(Integrations across data sources)`  

## 2.4 DB 커넥션 풀 튜닝 및 성능 최적화
- **HikariCP**
    - `경량·최소오버헤드(Lightweight & minimal overhead)`
    - `고성능(High throughput & low latency)`
    - `자동 유휴/유출 연결 정리(Idle/leak detection & cleanup)`
    - `스프링부트 기본풀(Default in Spring Boot)`
    - `모니터링·메트릭 지원(Monitoring & metrics support)`
    
- **Apache Commons DBCP2**
    - `풍부한 기능(Feature-rich pooling)`
    - `성능 향상 및 JMX 모니터링(Improved performance & JMX support)`
    - `Commons Pool2 기반(Underlying Commons Pool2 integration)`
    - `다양한 JDBC 버전 지원(Multi-JDBC version support)`
    - `구성 및 튜닝 유연성(Configurable & tunable)`
    
- **Tomcat JDBC Pool**
    - `고동시성 환경 최적화(Optimized for high concurrency)`
    - `비동기 연결 취득(Asynchronous connection retrieval)`
    - `인터셉터 및 사용자정의 훅(Custom interceptors & extension hooks)`
    - `유휴/연령 기반 연결 정리(Idle/age-based connection cleanup)`
    - `표준 DataSource/JNDI 구성(Standard DataSource/JNDI support)`
    
- **c3p0**
    - `전통적 JDBC 드라이버 지원(Legacy JDBC driver support)`
    - `커넥션 및 PreparedStatement 풀링(Connection & PreparedStatement pooling)`
    - `JNDI 바인딩 및 직렬화 가능(Referenceable & Serializable DataSource)`
    - `자원 정리에 집중(Resource cleanup vigilance)`
    - `성숙한 라이브러리(Mature library with long history)`

## 2.5 캐싱 시스템 설계 및 응답 속도 개선
- **Redis**
    - `인메모리 키-값 저장소(In-memory key-value store)`
    - `다양한 데이터 타입 지원(Versatile data structures)`
    - `고성능·저지연(High-performance & low-latency)`
    - `스냅샷·AOF 영속성(Persistence options – RDB & AOF)`
    - `클러스터링·복제 지원(Clustering & replication)`
    
- **Memcached**
    - `분산 메모리 캐시(Distributed memory cache)`
    - `단순 키-값 저장(Simple key-value store)`
    - `대규모 스케일아웃(Scalable usage across nodes)`
    - `LRU 기반 자동 만료(LRU eviction)`
    - `웹 애플리케이션 용도에 최적화(Optimised for web-app caching)`
    
- **Caffeine**
    - `자바 기반 인메모리 캐시(Java-based in-memory cache)`
    - `고성능 읽기/쓰기 최적화(High throughput reads & writes)`
    - `크기 기반 제거(Size-based eviction)`
    - `시간 기반 만료(Time-based expiration)`
    - `간편한 API 사용(Simple and fluent API)`
    
- **Hazelcast**
    - `분산 인메모리 데이터 그리드(Distributed in-memory data grid)`
    - `캐싱 + 스트림 처리 통합(Cache + stream processing)`
    - `클러스터 수평 확장(Cluster horizontal scalability)`
    - `Geo/WAN 복제 및 고가용성(Geo/WAN replication & high availability)`
    - `클라우드/쿠버네티스 네이티브(Cloud-native / Kubernetes ready)`

## 2.6 사용자 정보 관리 및 인증, 인가 보안 설계
- **Spring Security**
    - `인증·인가(Authentication & Authorization)`
    - `공격 방어(Protection against common exploits)`
    - `Spring 생태계 통합(Seamless Spring integration)`
    - `메서드 수준 보안(Method-level security)`
    - `JWT·OAuth2·LDAP 등 표준지원(Standards support: JWT, OAuth2, LDAP)` 
    
- **Apache Shiro**
    - `인증·인가(Authentication & Authorization)`
    - `세션 관리(Session management)`
    - `암호화·해시(Cryptography & hashing)`
    - `플러거블·유연 구조(Pluggable & flexible architecture)`
    - `POJO 기반 사용성(Easy-to-use POJO API)`
    
- **Keycloak**
    - `싱글사인온(SSO: Single-Sign On & Sign-Out)`
    - `OIDC·OAuth2·SAML 지원(OpenID Connect, OAuth2, SAML)`
    - `사용자 연합·LDAP 통합(User federation & LDAP/AD integration)`
    - `소셜 로그인·아이덴티티 브로커링(Social login & identity brokering)`
    - `관리 콘솔 및 역할-정책 기반 권한(Administration console & fine-grained roles/policies)`
    
- **pac4j**
    - `웹 컴포넌트 보안(Web filters & callback/logout endpoints)`
    - `프로파일 관리(Profile management)`
    - `인가 로직(Authorization logic)`
    - `다양한 환경 지원(Multi-environment / web frameworks)`
    - `플랫폼 비종속(Platform-agnostic security engine)`

## 2.7 플레이리스트 관리 모듈 설계 및 구현
### 2.7.1 도메인 설계 방식 비교
-  **도메인 모델 패턴 (Domain Model Pattern, 리치 도메인)**
    - `객체 중심 비즈니스 로직(Business logic in entities)`
    - `고응집·저결합(High cohesion, low coupling)`
    - `표현 계층 독립성(Domain independent of UI/persistence)`
    - `복잡한 도메인 처리 적합(Suitable for rich domains)`
    - `유지보수성 향상(Improved maintainability)`
    
- **트랜잭션 스크립트 (Transaction Script)**
    - `절차 중심 로직(Procedure-based logic)`
    - `요청 단위 메서드 구성(One script per transaction)`
    - `빠른 개발 및 단순 구조(Fast and simple design)`
    - `빈약한 도메인 행위(Little behavior in domain objects)`
    - `확장성 증가 시 유지 난이도(Hard to maintain in complex domains)`
    
-  **액티브 레코드 (Active Record)**
    - `CRUD 포함 엔티티(Entity with CRUD methods)`
    - `직관적 테이블 매핑(Direct table–object mapping)`
    - `단순 애플리케이션 적합(Suitable for small apps)`
    - `비즈니스·영속성 혼재(Mixed business and persistence logic)`
    - `복잡 도메인 비권장(Not ideal for complex domains)`

### 2.7.2 영속성 계층 아키텍처 비교
- **리포지토리 + QueryDSL 기반 구조**
    - `도메인 친화 추상화(Domain-oriented abstraction)`
    - `타입 안전 쿼리(Type-safe queries)`
    - `복잡 조회에 유리(Strong for complex querying)`
    - `영속성·도메인 분리(Separation of concerns)`
    - `리팩토링 용이(Easy to refactor)`
    
- **DAO 패턴 + MyBatis**
    - `높은 SQL 제어권(Full SQL control)`
    - `XML·어노테이션 매핑(XML/Annotation mapping)`
    - `DB 특화 쿼리 강점(Strong for DB-specific logic)`
    - `매핑 수동 관리(Manual object mapping)`
    - `낮은 자동화(less automation compared to ORM)`
    
- **Spring Data JPA / @Query 기반 설계**
    - `메서드 네이밍 쿼리(Method naming query generation)`
    - `표준 CRUD 제공(Standard CRUD and paging)`
    - `단순 구조 적합(Suitable for simple domains)`
    - `복잡 쿼리 제한(Limited for dynamic queries)`
    - `빠른 개발 속도(Fast development cycle)`
    
- **EntityManager 직접 사용**
    - `JPA 직접 제어(Direct JPA control)`
    - `최대 유연성(Maximum flexibility)`
    - `고숙련 필요(High expertise required)`
    - `보일러플레이트 증가(More boilerplate)`
    - `유지보수 난이도(Maintenance complexity)`

### 2.7.3 API 표현 계층 설계 방식 비교
- **DTO 기반 API 계층 분리**
    - `엔티티·표현 분리(Entity–DTO separation)`
    - `결합도 최소화(Low coupling)`
    - `클라이언트 최적화 데이터(Tailored response model)`
    - `보안 강화(Safer boundary)`
    - `대규모 서비스 적합(Good for large systems)`
    
- **엔티티 직접 노출 (Entity Exposure)**
    - `빠른 개발(Rapid API development)`
    - `도메인·API 모델 동일(Same model for API and DB)`
    - `보안 위험 증가(Security exposure risk)`
    - `변경 영향도 높음(High impact on domain model)`
    - `소규모 서비스 적합(Fits small/simple apps)`
    
- **CQRS 스타일 (Query/Command 분리)**
    - `읽기·쓰기 모델 분리(Separate read/write models)`
    - `성능 최적화(Performance optimization)`
    - `구조 복잡도 증가(Higher architectural complexity)`
    - `이벤트 기반과 연동 가능(Event-sourcing friendly)`
    - `유지보수성 향상(Maintainability improvement)`
    
- **GraphQL 기반 뷰 모델 설계**
    - `요청 기반 데이터 구성(Client-defined schema)`
    - `오버·언더패치 감소(Eliminates over/under-fetching)`
    - `강력한 타입 시스템(Strong schema & types)`
    - `단일 엔드포인트(Single endpoint API)`
    - `캐싱·보안 복잡성(Cache/security complexity)`

## 2.8 ChatGPT Open API 연동 및 서비스 적용
- **OpenAI API**
    - `스케일러블 엔터프라이즈 지원(Enterprise-scale features)`
    - `데이터 훈련 제외 및 보존 정책(No train on customer data & retention controls)`
    - `REST·스트리밍 API 지원(REST & streaming APIs)`
    - `다양한 활용 가능(Task-agnostic: generation, summarization, code)`
    - `보안·컴플라이언스(Security & compliance: SOC2, encryption)`
    
- **Claude API**
    - `외부 시스템과 도구 인터페이스 연동(Tool use for external systems)`
    - `코드 실행 및 분석 지원(Code execution & data analysis)`
    - `API 기반 권한/파일 관리(Admin API & Files API)`
    - `프롬프트 개선 및 자동화 지원(Prompt improvement & automation)`
    - `고도로 자율적 에이전트 구축 가능(Agent-like workflows)`
    
- **Gemini API**
    - `멀티모달 입력·출력(Text, image, audio, video support)`
    - `표준 및 스트리밍 REST API(Standard & streaming endpoints)`
    - `배치 처리 및 대용량 파일 지원(Batch mode & file/document handling)`
    - `임베딩 및 검색 벡터 연산(Embeddings & vector operations)`
    - `웹·SDK 통합 및 개발자 친화(Web/SDK integration)`

---

# 3. 분석

## 3.1 로드밸런서
### 3.1.1 적절한 도구 선택 상황
- **Nginx**
    - `웹서버 + 리버스 프록시 + 로드밸런서 역할을 동시에 수행할 필요가 있을 때`
    - `정적 콘텐츠 제공 + HTTP/HTTPS 처리 + 간단한 L7 라우팅이 중심일 때`
    - `컨테이너·마이크로서비스도 있지만, 서비스 탐지 자동화보다는 수동 구성이 충분한 환경일 때`
- **HAProxy**
    - `고성능 및 고트래픽 처리(수백만 요청/초) 환경에서, 라우팅 제어(ACL, 콘텐츠 기반 분기 등)가 세밀하게 필요할 때`
    - `HTTP 및 TCP(L4) 트래픽 모두 다루어야 하고, 장애 대응, 상태 점검(health check) 및 고가용성(HA) 구성이 필수일 때`
- **AWS ALB**
    - `AWS 인프라에서 웹 애플리케이션(API, 마이크로서비스) 구성이 되어 있고, 경로 기반(host/path) 라우팅, 컨테이너/서버리스(Lambda) 통합 등이 필요한 경우`
    - `HTTP/HTTPS 중심이고, 복잡한 앱 콘텐츠 라우팅이 필요하며 클라우드 네이티브 설계가 적용되는 프로젝트`
- **Treafik**
    - `컨테이너 오케스트레이션(Docker, Kubernetes) 환경이 중심이며, 서비스 탐지(auto-discovery) + 동적 라우팅 + 마이크로서비스 중심 구조일 때`
    - `DevOps/플랫폼팀이 자동화, GitOps, 미들웨어 체인 구성, 관측성(모니터링) 등을 중요시하는 경우`

### 3.1.2 각 도구별 차별화된 특징 및 강점
- **Nginx**
    - `가볍고 효율적인 리버스프록시 + 고성능 L7 로드밸런서로, 간단한 설정으로 다수의 동시접속을 처리할 수 있다.`
- **HAProxy**
    - `L4, L7 모두 지원하며, 심층적인 제어(ACL, 상태체크, 고가용성)로 트래픽 안정성과 성능이 중요한 환경에서 빛난다.`
- **AWS ALB**
    - `이너 및 마이크로서비스 환경에 최적화된 자동 서비스 탐지와 동적 라우팅 기능을 갖춘 최신 리버스프록시이다.`
- **Treafik**
    - `AWS 생태계 내에서 HTTP/HTTPS 콘텐츠 기반 라우팅, 다양한 타겟 지원, 자동 확장 및 보안 통합을 제공하는 관리형 L7 로드밸런서다.`

