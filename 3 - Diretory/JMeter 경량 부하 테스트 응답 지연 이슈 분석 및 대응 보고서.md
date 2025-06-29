

---
- [[0 Home]]
---

## 1. 개요

이번 테스트는 Apache JMeter를 사용하여 로그인 API에 점진적으로 부하를 가하면서, 병목 구간 및 에러 발생 원인을 확인하기 위한 목적으로 진행되었다.

---
## 2. 테스트 환경 및 조건

| 항목             | 값                         |
|------------------|------------------------------|
| 테스트 대상       | 로그인 API                  |
| 성능 테스트 도구 | Apache JMeter               |
| 테스트 시간       | 300초 (5분)                 |
| 총 요청 수        | 12,000건                    |
| 동시 요청자 수    | 40명                        |

---
## 3. 주요 이상 현상

| 항목            | 내용                         |
|-----------------|------------------------------|
| 평균 응답 시간  | 2 ~ 7초 (비정상적 지연)       |
| 에러율          | 20% ~ 60% (지속적으로 높음)  |
| 시스템 판단     | 이 부하는 일반적으로 감당 가능 수준이나, 과도한 지연과 오류 발생 |

---
## 4. 시도된 조치

### 4.1 로드 밸런서 적용

- 요청 분산을 기대하고 로드 밸런서를 도입하였으나, 성능 개선 없음
- 포트별 요청 분산 상태 확인 결과, 다음과 같이 불균형한 분산이 나타남:

| 포트   | 로그인 수 |
|--------|-----------|
| 8080   | 1,248     |
| 8081   | 720       |
| 8082   | 647       |
| 8083   | 670       |
| 8084   | 544       |
| 8085   | 516       |
| 8086   | 552       |
| 8087   | 471       |

- 결과: 포트 번호가 높아질수록 요청 수가 줄어드는 경향을 보이며, 이는 로드 밸런서의 트래픽 분산 불균형을 나타낸다.

### 4.2 클라이언트 ↔ 서버 요청 수 일치 검증

| 구분          | 요청 수     | 에러율(%) | 누락 요청 수 |
|---------------|-------------|------------|----------------|
| 클라이언트     | 12,000      | 30.58%     | 3,670          |
| 서버           | 8,329        | –          | 3,671          |

- 서버 누락 요청 수 = 12,000 - 8,329 = 3,671
- 클라이언트 누락 요청 수 = 12,000 × 30.58% ≈ 3,670

결과  
- 클라이언트에서 발생한 총 요청 수(12,000건)와  
- 서버에서 실제 수신한 요청 수(8,329건)는  
- 에러율 계산을 통해 도출한 누락 수치와 거의 정확히 일치한다.  
- 따라서 수집된 데이터는 신뢰 가능하며, 클라이언트 → 서버까지의 요청 전달 경로는 정상 작동 중이라 판단된다.

---
## 5. 확인된 정보

- 클라이언트와 서버가 받는 실제 요청 수는 일치한다.
- 로드밸런서를 적용하였지만, 성능에 대한 개선을 받지 못하였다.
- 로드밸런서가 트래픽 분산 불균형을 나타낸다.

---
## 6. 분석 방향

문제 원인을 다음과 같은 하향식 절차로 추적할 계획이다:

1. 클라이언트
   - JMeter 로그: View Results Tree, Summary Report, Aggregate Report, Errors
   - JMeter 에러 메시지 유형 (ex. connection refused, read timeout 등)
   - 테스트 스크립트 설정: Ramp-up, Thread 수, Loop Count, Think Time 등

2. 네트워크 경로
   - ping, traceroute, telnet 결과 (지연이나 방화벽 문제 확인)
   - 로드밸런서 앞단 로그 (ex. Nginx, HAProxy access/error 로그)
   - 로드밸런서 설정 파일 (LB 알고리즘, health check 설정 등)

3. 로드 밸런서
   - 분산 로그: 각 포트별 실제 요청 수 (이미 제공됨)
   - LB의 응답 지연 로그 (timeout, failover 발생 여부)
   - LB 서버 리소스 사용률 (CPU, Memory) — htop, vmstat, sar 등

4. WAS (Spring Boot)
   - 스레드 수 / 동시 처리 가능 수 확인: server.tomcat.max-threads, Executor 설정
   - GC 로그: GC pause time, Full GC 유무 (-Xlog:gc*)
   - Actuator 지표: /actuator/metrics, /actuator/health, /actuator/threads
   - 에러 로그 (ex. RejectedExecutionException, OutOfMemoryError)
   - HikariPool 경고 로그: connection timeout, starvation 등

5. DB (MySQL)
   - SHOW PROCESSLIST 또는 performance_schema 기반의 쿼리 대기 상태
   - DB connection pool 최대치 (maximumPoolSize, 실제 active connections 수)
   - 느린 쿼리 로그 (slow_query_log)
   - 인덱스 여부, 쿼리 실행 계획 (EXPLAIN)
   - MySQL 리소스 사용량: CPU, IO wait (top, iostat, mysqladmin)

6. 공통 모니터링 툴 (권장)
   - Grafana + Prometheus: JVM, DB, 시스템 리소스를 실시간으로 시각화
   - VisualVM, JConsole: 실시간 스레드/메모리 상태 추적
   - Netdata, nmon, Glances: OS 레벨 모니터링

각 구간의 자원 사용률, 처리율, 스레드 수, GC 동작, DB 커넥션 풀 상태 등을 종합적으로 분석하여 병목 요인을 추출할 것이다.
