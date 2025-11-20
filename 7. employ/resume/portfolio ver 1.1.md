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

**부하 테스트 도구**  
JMeter, k6, Locust, nGrinder

**로그 수집기(저장소)**  
Elasticsearch, OpenSearch, Loki, Graylog, ClickHouse, Splunk, Datadog, New Relic

**로그 수집 에이전트(수집기)**  
Filebeat, Fluent Bit, Vector, rsyslog, Logstash Forwarder

**시각화 및 모니터링 도구**  
Kibana, Grafana, OpenSearch Dashboards, Graylog Web UI, Datadog Dashboard

**로드밸런서**  
Nginx, HAProxy, AWS ALB, Traefik

**데이터 접근 계층**  
Spring Data JPA, MyBatis, JDBC Template, JOOQ

**쿼리 빌더**  
QueryDSL, JPQL, Criteria API, JOOQ

**커넥션 풀 관리**  
HikariCP, Apache DBCP2, Tomcat JDBC Pool, c3p0

**캐싱 및 세션 관리**  
Redis, Memcached, Caffeine, Hazelcast

**인증 및 인가**  
Spring Security, Apache Shiro, Keycloak, pac4j

**생성형 AI 모델 API (LLM 서비스)**
ChatGPT OpenAI API, Claude API, Gemini API

---

# 2. 도구 별 키워드 정리
## 2.1 부하 테스트 도구
- **Jmeter**
    - `GUI에 특화된 초심자 친화적 테스트 도구`
    - `다양한 프로토콜과 플러그인 지원`
    - `GUI (XML)or CLI 기반 실행기`
    - `다양한 리스너 기반 리포트 자동 생성 및 시각화`
    - `JVM 스레드 기반으로 수천 ~ 수만 단위 동시 사용자까지 현실적 한계`
    - `시나리오 단위 스레드 유지, 루프 종료 시 일괄 해제`
- **k6**
    - `개발자 친화적 코드 기반 성능 테스트 도구`
    - `JavaScript로 테스트 시나리오 작성 및 제어`
    - `Go 엔진 + V8 JS 런타임 하이브리드 구조`
    - `경량 Goroutine 기반 고성능 동시성 처리`
    - `CLI 중심으로 CI/CD 자동화 및 DevOps 연동 용이`
    - `멀티 환경 일관 실행 유연성`
    - `다양한 성능, 통합 테스트 지원`
    - `모니터링, 메시징, 관찰 도구와 폭 넓은 통합`
    - `확장 가능한 오픈소스 구조`
- **nGrinder**
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
- **Locust**
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

## 2.3

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

