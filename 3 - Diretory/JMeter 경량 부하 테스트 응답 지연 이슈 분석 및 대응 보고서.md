

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

---

## 7. 클라이언트 단 분석

	### 7.1 Jmeter - View Results Tree
	
	- Request path
		- `POST http://localhost/login`
	- Request body
	  ```json
	  {
	    "email": "test10970@naver.com",
	    "password": "123456789"
	  }
	  ```
	- Request header
	  ```
	  Connection: keep-alive
	  Content-Type: application/json
	  Accept: application/json
	  Authorization: Bearer ${jwt_token}
	  Content-Length: 64
	  Host: localhost
	  User-Agent: Apache-HttpClient/4.5.14 (Java/17.0.12)
	  ```
	
	- 에러 메세지
		- Response body
		- `org.apache.http.conn.HttpHostConnectException: Connect to localhost:80 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect`
			- org.apache.http.conn.HttpHostConnectException: localhost:80 [localhost/127.0.0.1, localhost/::1]에 연결 실패: 연결이 거부됨: connect
		- Response code
		- `Non HTTP response code: org.apache.http.conn.HttpHostConnectException`
			- HTTP 응답 코드 아님: org.apache.http.conn.HttpHostConnectException  
		- `Response message:Non HTTP response message: Connect to localhost:80 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect`
			- 응답 메시지 아님: localhost:80 [localhost/127.0.0.1, localhost/::1]에 연결 실패: 연결이 거부됨: connect
		
	- 에러 메시지 해석
		- 오류 코드
			- `Non HTTP response code: org.apache.http.conn.HttpHostConnectException
				- `Non HTTP response code`
					- HTTP 응답 코드가 아예 없음
					- 클라이언트(JMeter)가 HTTP 서버에 도달하지 못해 응답을 받지 못함 ( 200, 404 같은 코드조차 없음)
				- `org.apache.http.conn.HttpHostConnectException`
					- Apache HTTPClient에서 호스트 연결 시도 중 예외 발생
					- connect() 시도 중 네트워크 계층에서 에러가 발생했음을 의미
		- 메시지
			- `Connect to localhost:80 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect`
				- JMeter가 localhost:80에 접속을 시도했으나, 해당 포트에 서버가 실행 중이지 않아 연결이 거부되었고 HTTP 응답조차 받지 못했다.
			- `Connect to localhost:80 [...] failed`
				- JMeter가 localhost:80으로 HTTP 요청을 시도했지만 연결 실패
			- `[localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1]`
				- 시도한 주소들 (IPv4 `127.0.0.1`, IPv6 `::1`)
				- 둘 다 로컬 주소이며, 동일한 컴퓨터 내에서 서버를 찾으려 했다는 뜻
			- `Connection refused: connect`
				- 해당 주소(`localhost`)의 80번 포트에 서버가 실행 중이지 않음
				- 즉, 연결 요청을 서버가 거부(Refused)했거나, 아예 리스닝 상태가 아님
	
	- 해당 요청은 JMeter가 `localhost:80` 포트에 연결을 시도했으나, 해당 포트에서 서버가 실행 중이지 않아 연결이 거부되었다. 
	- 이로 인해 HTTP 응답조차 받지 못하고 비HTTP 오류로 처리되었다.

---
### 7.2 Jmeter - Summary Report

- 요청 샘플 요약

| Label                               | # Samples | Average (ms) | Min | Max   | Std. Dev. | Error % | Throughput | Received KB/sec | Sent KB/sec | Avg. Bytes |
| ----------------------------------- | --------- | ------------ | --- | ----- | --------- | ------- | ---------- | --------------- | ----------- | ---------- |
| HTTP Request - login                | 12,000    | 7889         | 0   | 51492 | 8127.14   | 30.58%  | 38.5/sec   | 43.37           | 8.03        | 1153.0     |
| HTTP Request - get playlist details | 12,000    | 1737         | 0   | 39139 | 3760.89   | 32.39%  | 39.1/sec   | 60.02           | 11.91       | 1572.0     |
| TOTAL                               | 24,000    | 4813         | 0   | 51492 | 7039.72   | 31.49%  | 77.0/sec   | 102.51          | 19.76       | 1362.5     |

- 요약 분석

- 총 요청 수 : 24,000건
    - 로그인 요청 : 12,000건
    - 플레이리스트 상세 조회 요청 : 12,000건
- 평균 응답 시간
    - 로그인 요청 : 7.88초
    - 상세 조회 요청 : 1.74초
- 최대 응답 시간
	- 로그인 요청 : 51.5초
- 에러율
    - 로그인 요청 : 30.58%
    - 상세 조회 요청 : 32.39%
    - 전체 평균 에러율 : 31.49%
- 처리율(Throughput)
    - 전체 처리율 : 77.0건/초
    - 로그인 : 38.5건/초
    - 상세 조회 : 39.1건/초


---
### 7.4 Jmeter - Log

---
### 7.5 Jmeter Dashboard

![[Pasted image 20250629200835.png]]
![[Pasted image 20250629200820.png]]
![[Pasted image 20250629200752.png]]
![[Pasted image 20250629201018.png]]
![[Pasted image 20250629201045.png]]

![[Pasted image 20250629204959.png]]

![[Pasted image 20250629205037.png]]

---

### 7.6