
---
- [[0 Home]]
---

- book study
	- `nosql`은 `key-value`로 뽑는게 더 빠르다.
	- 물론 상황에 따라 더 빠른게 다르다.
	- `ai 분야`에서는 `nosql`을 사용할 이유가 없다?
	- 사용의 목적이 조금 다르다?
	- nosql은 즉각적이고 빠른 것이 특징이다.
	- back단의 여러 복잡한 서버를 거치는 것은 시간이 걸리기때문에 즉각적으로 응답할 수 있는 데이터들은 nosql에 적합하다.
	- ai에서는 데이터베이스가 아니라 데이터스토리지가 필요한 것이다.
	- nosql이 로그인 상태정보를 가지고 있는 것이 적합하다.
	- mongodb는 원천 데이터를 빠르게 로그나 데이터를 저장하고 정제해서 rdbms로 옮기는 용도로 많이 사용한다.
	- 서비스마다 db 사용 여부가 다를 수 있을 것 같다.
	- 성능저하는 메모리가 원인이 대부분이다.

- 트러블 슈팅
	- 로드밸런싱 후 테스트하는데 서버에서 에러로그가 안뜬다?
		- 단일 서버로는 에러로그가 뜨는지 확인해보자.
		- 단일 서버에서도 에러로그가 안뜬다.
		- 이상한 점을 발견했다. 로드밸런싱보다 단일서버가 성능이 더 잘나왔다?
		- 단일 서버 - `평균 응답 속도 6480 ms` 로드밸런싱 - `평균 응답 속도 7477 ms`
		- 로드 밸런싱은 인스턴스 서버가 8개인데 말도 안되는 결과이다.
		- 로드밸런싱이 제대로 동작하지 않고 있다? 확인해보자.
		- `successfulAuthentication`, `unsuccessfulAuthentication` 각각 메서드에, sysout을 찍어서 로드밸런싱이 올바르게 분산되는지 확인하고, 덫붙여 로그인에 실패한다면 예외처리 및 로깅이 나오나 확인해보도록한다.
		- 테스트 결과 로드밸런싱은 고르게 분산되는 것을 확인할 수 있었고, 로그인 실패시에는 어떠한 예외처리 로그가 나오지 않았다.
		- 그렇다면.. 서버 에러가 아닌 클라이언트 단에서 발생하는 에러인가?
		- Response Body : `org.apache.http.conn.HttpHostConnectException: Connect to localhost:80 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect`
		- 번역 :  `localhost:80 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1]에 연결하는 데 실패했습니다. 연결이 거부되었습니다.`
		- 아무리 찾아봐도 정확한 원인을 찾을 수 있는 방법을 모르겠다..

| 동시접속자 | 평균 응답 속도(ms) | CPU 최대 사용량(%) | TPS (초당 처리 건수) | 에러율(%) |
|------------|--------------------|---------------------|------------------------|-----------|
| 20         | 179                | 약 49.29%           | 40.0                   | 0.00      |
| 30         | 210                | 약 59.67%           | 60.5                   | 0.00      |
| 40         | 2408               | 약 70.76%           | 76.2                   | 13.57     |

- CPU 최대 사용량을 알기위해 필요한 정보
	- CPU 논리 코어 갯수
	- 테스트 시간
	- 누적 CPU 사용 시간

- 현재 컴퓨터의 CPU 논리 코어(logical processors) 수를 조회
```
Get-CimInstance -ClassName Win32_Processor | Select-Object NumberOfLogicalProcessors
```


- Windows 기준: CPU 최대 사용률 확인 방법
```powershell

## PowerShell 명령어 (즉시 확인용)
## 전체 CPU 사용률 확인 (실시간 퍼센트)

Get-Process java | Sort-Object CPU -Descending | Select-Object -First 5
Get-Counter '\Processor(_Total)\% Processor Time'
```

- DB 최대 사용량 확인 명령어 (MySQL 기준)
```sql
-- 커넥션 기준 최대 사용률
-- 사용률(%) = (Threads_connected / max_connections) × 100
SHOW STATUS LIKE 'Threads_connected';
SHOW VARIABLES LIKE 'max_connections';

-- InnoDB 버퍼 풀 기준 최대 사용률
-- 사용률(%) = (pages_data / pages_total) × 100
SHOW GLOBAL STATUS LIKE 'Innodb_buffer_pool_pages%';

---

SHOW STATUS LIKE 'Threads_connected';
SHOW VARIABLES LIKE 'max_connections';
SHOW GLOBAL STATUS LIKE 'Innodb_buffer_pool_pages%';
```


---
```nginx

worker_processes auto;  
  
events {  
    worker_connections 1024;  
}  
  
http {  
    upstream backend {  
        server localhost:8080;  
        server localhost:8081;  
        server localhost:8082;  
        server localhost:8083;  
        server localhost:8084;  
        server localhost:8085;  
        server localhost:8086;  
        server localhost:8087;  
    }  
  
 server {  
        listen 80;  
        server_name localhost;  
  
        location / {  
            proxy_pass http://backend;  
            proxy_set_header Host $host;  
            proxy_set_header X-Real-IP $remote_addr;  
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;  
            proxy_set_header X-Forwarded-Proto $scheme;  
        }  
    }  
}
```

```nginx
worker_processes auto;  
  
events {  
    worker_connections 1024;  
}  
  
http {  
    # 로그 포맷 커스터마이징  
    log_format main '$remote_addr - $remote_user [$time_local] "$request" '  
                    '$status $body_bytes_sent "$http_referer" '  
                    '"$http_user_agent" "$upstream_addr" "$upstream_status" $request_time';  
  
    access_log logs/access.log main;  
    error_log logs/error.log warn;  
  
    # 로드밸런싱 대상 서버 (죽은 서버 자동 제외)  
    upstream backend {  
        server localhost:8080 max_fails=2 fail_timeout=5s;  
        server localhost:8081 max_fails=2 fail_timeout=5s;  
        server localhost:8082 max_fails=2 fail_timeout=5s;  
        server localhost:8083 max_fails=2 fail_timeout=5s;  
        server localhost:8084 max_fails=2 fail_timeout=5s;  
        server localhost:8085 max_fails=2 fail_timeout=5s;  
        server localhost:8086 max_fails=2 fail_timeout=5s;  
        server localhost:8087 max_fails=2 fail_timeout=5s;  
    }  
  
    server {  
        listen 80;  
        server_name localhost;  
  
        location / {  
            proxy_pass http://backend;  
  
            # 클라이언트 정보 전달  
            proxy_set_header Host $host;  
            proxy_set_header X-Real-IP $remote_addr;  
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;  
            proxy_set_header X-Forwarded-Proto $scheme;  
  
            # 타임아웃 등 설정도 권장 (옵션)  
            proxy_connect_timeout 3s;  
            proxy_read_timeout 10s;  
        }  
    }  
}
```

- 톰캣 스레드
- 로그를 모아서 file로 만든다?
- ![[Pasted image 20250615224310.png]]

- 스터디 - 



- Jmeter HTML report
	- Dashboard - 전체 테스트 요약 개요
		- 
	- Charts - 주요 지표 시각화한 그래프 모음 메뉴
		- 
	- Customs Graphs - 커스텀 그래프 추가 기능 (기본으로는 비어 있음)
		- 


| 동시접속자수 | 평균 응답 속도 | CPU 최대 사용량 | DB 최대 사용량 | Redis 최대 사용량 | 에러 비율 |
| ------ | -------- | ---------- | --------- | ------------ | ----- |
|        |          |            |           |              |       |
|        |          |            |           |              |       |
|        |          |            |           |              |       |
|        |          |            |           |              |       |
|        |          |            |           |              |       |
|        |          |            |           |              |       |
|        |          |            |           |              |       |
|        |          |            |           |              |       |
|        |          |            |           |              |       |




- 대용량 데이터 처리 성능 테스트에 대해서 Bcrypt를 해결할 수 있는 방법은 가장 디테일한 방법은 찾지 못했다. 되돌아가며 우선적으로 내가 다시 짚어보아야 할 사항은 다음과 같다.
	1. koomin 블로그 성능 테스트 게시물 참고
	2. 천천히 부하테스트하여 서버 다운 지점 확인
	3. Auto scailing 구축
		- 쿠버네티스 사용을 위한 지식 습득
		- 다만, 리턴 대비 시간 비용이 크기 때문에 당장은 추천하지 않는다.
	4. Server Mornitoring + DB Mornitoring 구축
	5. Bcrypt 알고리즘의 정확한 지식 이해
	6. Bcrypt 알고리즘 대안 알고리즘 Argon 2에 대한 지식 이해 및 대안 알고리즘 채택할지 판단.
	7. 그외 대안 알고리즘 및 CPU 병목 현상에 대항 문제 개선 방안 찾기

- 대용량 데이터 처리 개선 2
	- 서론
		- 기존의 방식은 처음부터 20000명은 동시에 요청을 하고 그 부분을 해결 해보려했지만, 가장 우선적으로 어느 순간까지 동시 요청을 견딜 수 있는지 부터 체크하는게 우선이라는 것을 파악했다. 따라서 2만명의 동시 요청을 하기 이전에 좀 더 객관적이고 검증된 데이터지향적으로 테스트 시나리오를 수립하기로 하였다.
		- DAU 와 동시 사용자 요청 수의 대비는 10/1이 적절하다고 한다. 그에 대한 근거는 추가적으로 조사할 것
		- 동시 요청 수 및 DAU는 점진적으로 증가시킬 것이기 때문에 ${} 형식의 동적으로 인자를 설정할 것
		- Randam Vable이라는 것을 알았다. 무작위 리퀘스트를 보낼 수 있도록 도와준다.
		- Jmeter는 GUI로 하는것을 지양한다?
			- 성능 테스트 및 시나리오 수립 이외에는 GUI를 사용하는 것이 권장되지 않는다고 한다.
			- 아마도 GUI로 발생하는 시각적인 ㄹ
		- 스레드 그룹은 멀티 형식으로 진행하는 것이 더 적절하다는 것을 이해했다.

- bcrypt의 처리 속도가 늦는걸 개선하는 방법
	- 서버를 늘리면 해결된다.
		- 로컬에서는 문제가 없지만 aws 같은 클라우드 서버는 비용이 증가한다는 단점이 존재한다.
	- 적재적소 필요한만큼만 서버를 추가하고 제거하는 오토 스케일링을 도입하면 좋을 것 같다.
- 오토 스케일링
	- 중간에 클라이언트와 서버를 중개해주는 매게체가있을 것이다.
- 쿠버네티스
- 초당 2만명
- 부하 테스트 점진적으로 증가하라
- 테스트 결과를 표로 만들어라
	- ![[Pasted image 20250608224819.png]]
	- 

- 왜 로그인 API는 1.9초 씩이나 걸렸을까?에 대한 원인을 찾는 것이 우리의 목표
	- 어떤 로직이 병목이었을까?
		- 어떤 로직이 병목이라는건 어떻게 찾는거지?
			- [Profile Java applications with ease](https://lp.jetbrains.com/intellij-idea-profiler/?source=google&medium=cpc&campaign=APAC_en_KR_IDEA_Profiler_Search&term=jvm%20profiler&content=708224323159&gad_source=1&gad_campaignid=14001267836&gbraid=0AAAAADloJzgvxIZSpMclcWPZH61Ejs0qL&gclid=Cj0KCQjw9O_BBhCUARIsAHQMjS4FqYtXpJBHb68s4CZZklGNiXJpHEYUQ1eO2WIm9SI3NNzREeCnSC4aAjiREALw_wcB)
			- [Profile Java applications with ease 가이드](https://www.jetbrains.com/ko-kr/pages/intellij-idea-profiler/)
	- MySQL 서버가 죽었어요
	    - MySQL도 모니터링이 필요할 수 있다.
	    - 그라파나를 사용해보자
		    - Grafana + Prometheus

- intelij profile java application with ease
	- intelij profile java application with ease은 무엇인가?
	- 내가 작성한 Java 코드의 성능 분석을 쉽게 할 수 있도록 도와주는 `IntelliJ Ultimate Edition`에서 제공되는 내장 프로파일링 도구
	- profile
		- 애플리케이션 실행 중일 때, 메모리 사용, CPU 사용, 쓰레드 상태, 메서드 호출 시간 등을 분석하는 행위
		- 즉, 내 코드가 어디서 느려지는지, 메모리를 어디가 많이 쓰는지 등을 실시간으로 시각적으로 확인할 수 있는 기능이다.
	- 기능 목적
		- 성능 병목 탐지
			- 특정 메서드가 CPU를 과도하게 점유하는지 확인
		- 메모리 누수 추적
			- 객체가 계속 메모리에 남아있는 이유 파악
		- GC 빈도 확인
			- 가비기 컬렉션이 너무 자주 발생하는지 확인
		- 쓰레드 상태 분석
			- 데드락, 기아 상태 등 확인 가능
	- 사용하는 방법
		1. Run > Profile `YourApp`  클릭
			- 또는 상단 실행버튼 오른쪽 🔽 버튼 → `Profile` 선택
		2. JVM이 부트되며 자동으로 분석 시작
		3. 실행 중에 실시간 그래프, 힙 사용량, CPU 점유율 등 확인 가능
	- 주요 도구
		- CPU 사용량
		- Memory allocation
		- Threads
		- Flame Graph
	-  프로파일링 결과 분석하는 방법
		- Flame Graph
			- 스레드별로 그룹화되어 있다.
			- 전체 스레드가 병합된 결과를 확인할 수 있고, 특정 스레드를 선택하여 자세히 조사할 수 있다.
			- 각 항목
				- y축 : 호출 스택
				- x축 : 리소스를 가장 많이 소비하는 함수 순서(사용률이 높을 수록 왼쪽에 위치하며 너비가 넓음)
				- 색상 : 파란색 : native call, 노란색 : java call, 회색 : library call
			- 분석 방법 예시
				- main의 실행에는 a 및 b 메서드가 기여했고, a는 다음으로 c를 호출
				- c는 주로 ArrayList에 요소에 추가하는데, 이때 대부분 grow를 처리하느넫 많이 소요
				- b는 대부분의 경우 IndexOutOfBoundsException을 처리하므로, 예외 발생 위치 조사와 조치 등이 필요
			- ![[Pasted image 20250607145253.png]]
			- Flame Graph에서 우클릭하면 나오는 `Focus on method in Call Tree`를 활용하면 해당 소스로 바로 이동할 수 있다.
			- ![[Pasted image 20250607145341.png]]
			- 그리고 연관된 코드로 넘어가면 다음과 같이 intelij에서 분석 결과를 바로 확인할 수 있다. 리소스를 가장 많이 소비하는 메서드에는 빨간색과 함께 불 아이콘이 표시된다.
			- ![[Pasted image 20250607150000.png]]
		- Call Tree
			- 리소스 사용량이 높은 순서로 호출 스택이 정렬되어 있다.
			- ![[Pasted image 20250607150423.png]]
		- Method List
			- 프로파일링된 데이터의 모든 메서드를 수집하여 누적 샘플 시간별로 정렬한다. 항목은 samples와 own samples로 나뉘어 지는데, 각각 다음과 같이 구별하면 된다.
			- alloction size
				- 해당 메서드를 포함한 전체 호출 스택의 누적 결과
				- 즉, 이 메서드가 직접 호출되었거나 다른 메서드를 통해 간접적으로 호출된 것까지 모두 포함
			- own allocation size
				- 하위 호출 메서드들을 제외하고 해당 메서드 자체에서만의 결과
				- 즉, 이 메서드 안에서 직접 소요된 것만 포함
				- ![[Pasted image 20250607151603.png]]
				- 예시![[Pasted image 20250607151639.png]]
				- 위의 결과에서 User.isAdult의 Allocation Size가 18.62 GB라는 것은 해당 메서드가 실행되는 동안, 직접적 또는 간접적으로 총 18.62GB의 객체가 힙 메모리에 할당되었다는 뜻이다. 즉 isAdult()에서 직접 할당한 객체들 뿐만 아니라 내부의 다른 호출 메서드들이 할당한 객체들의 총 합이 18.62GB라는 의미이다. 그리고 own allocation size가 0B라는 것은 해당 메서드 안에서 직접 new나 컬렉션 연산 등으로 생성된 것은 없다는 의미이다. 따라서 isAdult() 내부의 어떠한 메서드들에 의해 18.62GB나 할당되었는지 살펴보아야 할 필요가 있다.
				- 3가지 Tap
					- Back Traces
						- 메서드 호출자의 계층 구조를 보여주며, 이를 통해 선택한 메서드를 호출하는 메서드를 호출할 수 있다.
					- Meged Calles
						- 메서드의 호출 계층 구조 아래 메서드를 요약한 호출 트리
					- Calle List
						- 호출 계층 구조에 따라 메서드를 요약한 메서드 목록
					- ![[Pasted image 20250607152033.png]]
					- 위 분석만으로는 충분한 어플리케이션 분석이 어려울 수 있다.
					- 
		- Timeline
		- Events


- 병목지점이란 무엇인가
	- 전체 데이터의 흐름 중 가장 느린 구간을 의미?
		- 라우터 처리 능력 부족
			- 여러 장비가 연결되어 있지만 라우터가 데이터를 빠르게 전달하지 못함.
		- 서버 네트워크 카드 속도 제한
			- 서버는 빠른데 NIC가 100Mbps만 지원하면 병목
		- 스위치 포트 간 속도 차이
			- 기가비트 장비끼리 연결되었지만, 중간에 100Mbps 스위치가 있음.
		- 백엔드 서버의 느린 DB 응답
			- 클라이언트 요청은 빠르게 도착했지만, DB 응답이 느려 전체 트래픽 지연 발생.
		- ISP 회선 대역폭 한계
			- 내부망은 빠르지만, 인터넷 회선 자체가 느림.
			  
	- 중요한 이유?
		- 병목을 해결하지 않으면 하드웨어를 아무리 업그레이드해도 전체 성능 향상이 제한된다.
		- 정확한 병목 지점 파악 없이 무작정 업그레이드하면 비효율적인 낭비가 발생한다.
		- 성능 테스트를 하고 문제를 해결하기위해서는 정확한 병목지점을 보고 이해하며 원인을 좁혀갈 수 있는 능력이 필요하다.
		  
	- 탐지 방법?
		- 모니터링 툴 활용
			- 서버/네트워크 모니터링 도구를 사용해 어느 구간에서 트래픽 지연이 생기는지 확인한다.
			- wireshark - 패킷 수준 분석
			- iftop, nload - 리눅스에서 실시간 트래픽 확인
			- Netdata, Zabbix, Prometheus + Grafana - 종합적인 모니터링
			- Ping, Traceroute, mtr - 경로 추적과 지연시간 확인
		- 네트워크 구간별 테스트
			- 클라이언트 <-> 스위치 <-> 라우터 <-> 서버 간의 각 지점에 대해 ping, iperf, traceroute를 통해 응답속도와 패킷 손실율을 확인한다.
		- 서버 로그 분석
			- 서버 응답이 느릴 경우, WAS 및 DB 로그를 통해 I/O 지연, DB 쿼리 속도 등 병목 원인을 찾아야 한다.
			  
	- 병목 해결 방법?
		- 하드웨어 업그레이드
		- 트래픽 분산
			- 로드밸런서를 도입해 특정 서버나 링크에 집중되는 트래픽을 여러 서버로 분산
				- 예시 - Nginx, HAProxy, L4 스위치 등
		- Qos 설정 (Quality of Service)
			- 중요 트래픽에 우선 순위를 부여해 트래픽 혼잡 시에도 필수 서비스는 원활히 동작하도록 설정.
		- 네트워크 구성 최적화
			- 허브  -> 스위치 구조로 변경 (허브는 트래픽 전체를 브로드 캐스팅 하므로 병목 초래)
		- 서버/DB 성능 튜닝
			- 네트워크 병목이 아닌 애플리케이션 병목일 경우
				- DB 인덱스 추가
				- 쿼리 최적화
				- 비동기 처리 도입
				- GC 튜닝 (가장 최후의 수단)
				  
	- 병목 탐지시 체크리스트
		- CPU 사용률
			- top, htop, 모니터링 툴
		- 네트워크 대역폭 사용률
			- iftop, vnstat, 라우터 모니터링
		- 패킷 손실률
			- ping, mtr, traceroute
		- 응답 시간
			- curl, Jmter, 로그 응답시간
		- DB 쿼리 성능
			- slow query log, 실행계획(EXPLAIN)

- nginx란 무엇인가
	- nginx는 고성능 웹서버이자 오픈 소스 웹 서버이다.
	- 등장 배경
		- 기존 대표적인 웹서버였던 Apache HTTP Server는 스레드 기반 동기 처리 방식이었다. 이는 동시 접속자 수가 많아질수록 성능이 급격하게 저하되는 문제를 가지고 있었고, 시스템 자원을 많이 소비했다. 당시 웹서버가 C10K 문제를 처리하는데 한계를 드러내자 이에 대응하기 위해 Nginx가 등장하게 된다.
		- C10K 문제
			- `Client 10,000`의 약자
			- 하나의 서버에서 10,000명 이상의 클라이언트의 동시 연결을 처리하려고 할 때 생기는 성능 문제를 의미
			- 기존 웹서버들은 클라이언트 연결 하나당 하나의 스레드를 생성하는 구조였기 때문에, 동시 접속 수가 증가하면 CPU 및 메모리 자원이 급격히 소모되었다.
			- 이를 해결하기 위해 Nginx는 이벤트 기반 비동기 I/O 모델을 채택하여 가볍고 빠른 성능을 구현했다.
	- 주요 역할
		- 웹서버
			- HTML, CSS, JS 등 정적 파일을 매우 빠르게 제공
				- HTML, CSS, JS는 이미 완성된 형태로 저장되어 있기떄문에 요청이 오면 그냥 읽어서 보내기만 하면된다.
				- 복잡함 로직 처리, DB 조회, 랜더링 X
		- 리버스 프록시
		- 로드 밸런싱 
		- HTTP 캐시를 빠르고 효율적으로 처리
			- 정적 콘텐츠 고속 전송 목적으로 설계됨
			- 디스크 캐시 + 메모리 캐시 이중 지원
			- `proxy_cache` 등 캐시 지시어 제공
			- 이벤트 기반 처리(Event-driven I/O)
				- 동시 수천 요청도 스레드 생성 없이 처리 가능
				- 캐시된 응답도 매우 낮은 리소스 사용량으로 전달 가능
	- nginx를 왜 사용하는 이유
		- 일관된 고성능
			- 10년 이상 검증된 고성능 reverse proxy & static proxy server 실사용 기준에서 Node.js나 Apache보다 일관된 성능 유지
		- 설정 단순 + 강력한 기능
			- proxy_pass, load balancing, caching, gzip, SSL, rate, limiting 등 대부분의 웹 요구를 간단한 conf 한두줄로 구성 가능
		- 멀티 역할 기능
			- 웹서버 + 리버스 프록시 + 캐시 서버 + API 게이트웨이 역할까지 모두 가능.
			- 전용 장비 없어도 아키텍쳐 설계 간결화 가능
		- 높은 경량성
			- Node.js도 비동기지만, 런타임 비용이 크다.
			- Nginx는 C로 작성되어 런타임 오버헤드가 극히 낮다.
		- 프론트단 최적화에 최적
			- HTML, CSS, JS, 이미지같은 정적 파일을 매우 빠르게 처리가능
			- 정적 파일 처리에 있어선 거의 독보적이다.
		- 폭넓은 채택과 생태계
			- 전 세계 상위 웹사이트 중 과반이 NGINX 사용 문서 많고 튜토리얼 많고, 문제 해결도 쉬움
	- 간단한 nginx 동작 구조
		- Master-Worker 프로세스 모델로 구성
		- Master Process
			- 설정 파일을 읽고, Worker Process를 관리
		- Worker Process 
			- 클라이언트의 요청을 처리하며, 각 Worker는 독립적으로 동작

- 웹 서버란 무엇인가?
	- HTTP 요청을 받고, HTTP 응답을 제공하는 서버
	- 주기능은 정적 파일 제공, 백엔드 전달, 보안, 로깅
	- 정적파일이면 직접 응답하고 동적 요청이면 백엔드 서버에 전달
	- 응답 결과를 HTTP 응답 형태로 사용자에게 전달
	- 웹서버 vs WAS
		- 웹서버
			- 정적 콘텐츠 제공, 리버스 프록시
			- Nginx, Apache HTTP Server
		- WAS
			- 동적 콘텐츠 처리 (java, Python 등)
				- 프로그램 실행환경과 DB 접속 기능 제공
				- 여러 개의 트랜잭션(논리적인 작업 단위) 관리 기능
				- 업무를 처리하는 비즈니스 로직 수행
			- Tomcat, Spring Boot, Flask, Django
		- 보통은 웹서버 + WAS 구조로 함께 사용
		- 웹서버가 요청을 받고, 동적 처리는 WAS에 넘긴다.
	- 웹서버와 WAS를 구분하는 이유
		- 웹서버가 필요한 이유?
			- 정적 컨텐츠만 처리하도록 기능을 분배하여 서버의 부담을 줄인다.
		- WAS가 필요한 이유?
			- WAS를 통해 요청에 맞는 데이터를 DB에 가져와서 비즈니스 로직에 맞게 그때 그때 결과를 만들어서 제공함으로써 자원을 효율적으로 사용할 수 있다.
		- 그렇다면 WAS가 웹서버의 기능도 모두 수행하면 되지 않을까?
			- 기능을 분리하여 서버 부하 방지
				- WAS는 DB 조회, 다양한 로직을 처리하느라 바쁘기 때문에 단순한 정적 컨텐츠는, 웹서버로 빠르게 클라이언트에 제공하는 것이 좋다.
				- WAS는 기본적으로 동적 컨텐츠를 제공하기 위한 서버이다.
			- 물리적인 분리하여 보안 강화
				- SSL에 대한 암복호화 처리에 웹서버를 사용
			- 여러 대의 WAS를 연결 가능
				- Load Balancing을 위해서 웹서버를 사용
				- fail over(장애 극복), fail back 처리에 유리
				- 특히 대용량 어플리케이션의 경우 (여러개의 서버 사용), 웹서버와 WAS를 분리하여 무중단 운영을 위한 장애 극복에 쉽게 대응할 수 있다.
				- 예를들어, 앞 단의 Web Server에서 오류가 발생한 WAS를 이용하지 못하도록 한후 WAS를 재시작함으로써 사용자는 오류를 느끼지 못하고 이용할 수 있다.
			- 여러 웹 어플리케이션 서비스 가능
				- 예시 - 하나의 서버에서 PHP Application, Java Application을 함께 사용하는 경우
			- 기타 접근 허용 IP 관리, 2대 이상 서버에서의 세션 관리 등도 웹서버에서 처리면 효율적이다.
			- 즉, 자원 이용의 효율성 및 장애 극복, 배포 및 유지보수의 편의성을 위해서 웹서버와 WAS를 분리

- 프록시 서버란 무엇인가?
	- 클라이언트와 실제 서버 사이에서 중개 역할 하는 서버
	- 왜 프록시 서버를 사용하는가?
	- 보안 강화
		- 클라이언트와 실제 서버 간의 IP  주소를 숨겨 프라이버시 보호
	- 캐싱을 통한 성능 향상
		- 자주 요청되는 데이터를 저장해 빠르게 응답
	- 접근 제어
		- 특정 사이트 차단, 내부망 보호 등
	- IP 우회
		- 다른 지역 IP로 접속하여 차단 우회
	- 로드 밸런싱
		- 여러 서버에 트래픽 분산 가능
	- 프록시 서버 종류
		- 정방향 프록시(Forward Proxy)
			- 클라이언트 앞단에 위치
			- 클라이언트에서 요청할 때 직접 요청하는 것이 아닌 프록시서버로 거치는 방식
				- 사용자의 프라이버시 보호
		- 역방향 프록시(Reverse Proxy)
			- 서버 앞단에 위치
			- 서버에서 클라이언트 직접 데이터를 전달하지 않고 프록시 서버를 거치는 방식
				- nginx, apache 등 웹서버에서 사용
		- 오픈 프록시
			- 누구나 접근 가능한 프록시 (보안 취약점 우려)

- DB index란 무엇인가?
	- ![[Pasted image 20250601190104.png]]
	- 추가적인 쓰기 작업과 저장 공간을 활용하여 데이터베이스 테이블의 검색 속도를 향상 시키기위한 자료 구조이다.
	- 데이터베이스에서 원하는 데이터를 더 빠르게 찾기 위해 사용하는 자료구조이다.
	- 책의 목차처럼, 데이터를 빠르게 찾기 위한 키 목록
		- 책에서 특정 단어를 찾으려면 목차나, 색인(index)를 보고 찾듯이, DB에서도 마찬가지로, 전체 테이블을 다 뒤지는 대신 인덱스를 통해 빠르게 위치를 찾아가는 방식이다.
	- 인덱스를 활용하면 데이터를 조회하는 SELECT 외에도 UPDATE, DELETE의 성능이 함께 향상된다. 그러한 이유는 해당 연산을 수행하려면 해당 대상을 조회해야만 작업을 할 수 있기 때문이다.
	- `UPDATE USER SET NAME = 'MangKyu' WHERE NAME = 'Mang';`
		- Mang이라는 이름을 업데이트 해주기 위해서는 Mang을 조회해야 한다.
	- 인덱스가 없는 경우
		- `SELECT * FROM users WHERE email = 'a@example.com';`
		- 전체 테이블을 한 줄씩 읽으며 비교 -> 느림
	- 인덱스가 있는 경우
		- `email` 컬럼에 인덱스를 걸면 인덱스에서 먼저 위치를 찾고, 그 위치의 데이터를 바로 조회 -> 매우 빠름
	- 사용 예시
		- email 컬럼에 인덱스 생성
		- `CREATE INDEX idx_email ON users(email);
	- 인덱스의 자료구조
		- Hash Table
			- 정확한 값 검색에 빠름, 범위 검색은 불가능
			- 해시 테이블 기반의 DB 인덱스는 (데이터=컬럼의 값, 데이터의 위치)를 (Key, Value)로 사용하여 컬럼의 값으로 생성된 해시를 통해 인덱스를 구현하였다. 해시 테이블의 시간복잡도는 O(1)이며 매우 빠른 검색을 지원한다. 하지만 DB 인덱스에서 해시 테이블이 사용되는 경우는 제한적인데, 그러한 이유는 해시가 등호(=) 연산에만 특화되었기 때문이다. 해시 함수는 값이 1이라도 달라지면 완전히 다른 해시 값을 생성하는데, 이러한 특성에 의해 부등호 연산(>,<)이 자주 사용되는 데이터베이스 검색을 위해서는 해시 테이블이 적합하지 않다. 즉, 예를들면 `나는`으로 시작하는 모든 데이터를 검색하기 위한 쿼리문은 인덱스의 혜택을 전혀 받지 못하게 된다. 이러한 이유로 데이터베이스의 인덱스에서는 B+Tree가 일반적으로 사용된다.
		- B+Tree
			- 범위 검색, 정렬된 탐색에 유리
			- B+Tree는 DB 인덱스를 위해 자식 노드가 2개 이상인 B-Tree를 개선시킨 자료구조이다. B+Tree는 모든 노드에 데이터(Value)를 저장했던 B-Tree와 다른 특성을 가지고 있다.
				- 리프노드(데이터노드)만 인덱스와 함께 데이터(Value)를 가지고 있고, 나머지 노드(인덱스 노드)들은 데이터를 위한 인덱스(Key)만을 갖는다.
				- 리프노드들은 LinkedList로 연결되어 있다.
				- 데이터 노드 크기는 인덱스 노드의 크기와 같지 않아도 된다.
			- 데이터베이스의 인덱스 컬럼은 부등호를 이용한 순차 검색 연산이 자주 발생될 수 있다. 이러한 이유로 B-Tree의 리프노드들은 LinkedList로 연결하여 순차검색을 용이하게 등 B-Tree를 인덱스에 맞게 최적화하였다. (물론 Best Case)에 대해 리프노드까지 가지 않아도 탐색할 수 있는 B-Tree에 비해 무조건 리프노드까지 가야한다는 단점도 있다.)
			- 이러한 이유로 비록 B+Tree는 O(log2n)의 시간복잡도를 갖지만 해시테이블보다 인덱싱에 더욱 적합한 자료구조가 되었다.
			- InnoDB에서 사용된 B + Tree 구조![[Pasted image 20250601194715.png]]
			- InnoDB에서의 B+Tree는 일반적인 구조보다 더욱 복잡하게 구현이 되었다. InnoDB에서는 같은 레벨의 노드들끼리는 Linked List가 아닌 Double Linked List로 연결되었으며, 자식 노드들은 Single Linked List로 연결되어 있다.
	- 인덱스의 장점
		- 테이블을 조회하는 속도와 그에 따른 성능을 향상 시킬 수 있다.
		- 전반적인 시스템의 부하를 줄일 수 있다.
	- 인덱스의 단점
		- 저장 공간 사용
			- 인덱스를 관리하기 위해 DB의 약 10%에 해당하는 저장공간이 필요하다.
		- 쓰기 성능 저하
			- INSERT/UPDATE/DELETE 시 인덱스도 같이 갱신해야 해서 느려질 수 있다.
		- 너무 많으면 역효과
			- 필요한 컬럼에만 걸어야 효율적이다.
	- 인덱스의 관리
		- DBMS는 index를 항상 최신의 정렬된 상태로 유지해야 원하는 값을 빠르게 탐색할 수 있다.
		- 그렇기 때문에 인덱스가 적용된 컬럼에 INSERT, UPDATE, DELETE가 수행된다면 각각 다음과 같은 연산을 추가적으로 해주어야 하며 그에 따른 오버헤드가 발생한다.
		- INSERT
			- 새로운 데이터에 대한 인덱스를 추가
		- UPDATE
			- 삭제하는 데이터의 인덱스를 사용하지 않는다는 작업을 진행함
		- DELETE
			- 기존의 인덱스를 사용하지 않음 처리하고, 갱신된 데이터에 대해 인덱스를 추가함
	- 인덱스를 사용하면 좋은 경우
		- 규모가 작지 않은 테이블
		- INSERT, UPDATE, DELETE가 자주 발생하지 않는 칼럼
		- JOIN이나 WHERE 또는 ORDER BY에 자주 사용되는 칼럼
		- 데이터의 중복도가 낮은 칼럼
		- 기타 등등
		- 인덱스를 사용하는 것 만큼 생성된 인덱스를 관리해주는 것도 중요하다 그러므로 사용되지 않는 인덱스는 바로 제거를 해주어야 한다.
  
- DTO
	- DTO란 무엇인가?
		- Data Transfer Object (데이터 전송 객체)를 뜻한다.
		- 계층 간 데이터 전송을 위해 도메인 모델 대신 사용되는 객체이다.
		- 이때 계층이란 Presentation(View, Controller), Business(Service), Persistence(DAO, Repository) 등을 의미한다.
		- DTO는 순수하게 데이터를 저장하고, 데이터에 대한 getter, setter 만을 가져야한다고 한다. 
		- 위키피디아에 따르면 DTO는 어떠한 비즈니스 로직을 가져서는 안되며, 저장, 검색, 직렬화, 역직렬화 로직만을 가져야 한다고 한다.
		- 직렬화 / 역직렬화
			- 직렬화는 DTO를 Byte, Json, Xml 등의 형태로 변환하는 것을 의미한다.
			- 역직렬화는 그 반대를 의미한다.
	- DTO를 사용하는 이유?
		- DTO 대신 도메인 모델을 계층간 전달에 사용하면, UI 계층에서 도메인 모델의 메서드를 호출하거나 상태를 변경시킬 수 있다. 또한 UI 화면 마다 사용하는 도메인 모델의 정보는 상이하다. 하지만 도메인 모델은 UI에 필요하지 않은 정보까지 가지고 있다. 이러한 모든 도메인 모델 속성이 외부에 노출되면 보안 문제가 발생할 수 있다. 즉 도메인 모델을 캡슐화 하여 보호할 수 있다.
		- 또한 도메인 모델을 계층간 전송에 사용하면, 모델과 뷰가 강하게 결합 될 수 있다. 뷰의 요구사항 변화로 도메인의 코드를 변경해야할 일이 생기는 것은 좋지 않다. DTO를 사용하면 이 결합을 느슨하게 만들 수 있다.
	- DTO가 사용되는 계층
		- DTO는 영속 계층(Persistence Layer)까지 도달하는 것은 공통적으로 지양한다. 
		- 마틴 파울러는 Service Layer 란 애플리케이션 비즈니스 로직 즉, 도메인을 보호하는 레이어라고 말한다. 즉, 이 정의를 명확히 지키기 위해서는 Presentation Layer 에 도메인을 노출해서는 안된다. 따라서 이러한 관점으로는 도메인은 서비스 레이어에서 DTO로 변환되어 컨트롤러로 전달되어야 한다.
	
- Business Losic
	- 해당 프로그램이 해결하려는 실제 문제를 처리하는 구체적인 규칙과 절차
	- 소프트웨어가 단순히 데이터를 주고 받는 것 이상으로, `어떻게 처리해야 하는가`, `어떤 조건에서 어떤 행동을 해야 하는가` 정의한 업무 규칙
	
- Domain Model
	- 도메인이란 무엇인가?
		- 프로그래밍으로 문제를 해결하기 위해 만들 소프트웨어 프로그램을 위한 요구사항, 용어, 기능을 정의하는 학문 영역의 도메인 공학이다. 쉽게 말하면 도메인은 해결하고자 하는 문제 영역 정도가 된다.
		- 도메인은 다시 하위 도메인으로 나눠질수 있다.
		- 예시![[Pasted image 20250602203203.png]]
	- 도메인 모델은 무엇인가?
		- 도메인에 대한 지식을 선택적으로 단순화하고 의식적으로 구조화한 형태이다. 도메인 모델은 반드시 실제적인 무언가로 표현되지 않아도 존재한다.
		- 도메인 모델에 대한 표현을 코드로 나타낸다면 이를 도메인 객체 모델이라고 한다. 이를테면 Item 클래스, User 클래스로 표현할 수있다. 그리고 이것이 인스턴스화 된 것이 우리는 도메인 객체라고 부를 수 있는 것이다.
	
- 프로젝트 폴더 및 파일
	- .git
		- git 버전관리 시스템의 핵심 디렉토리
		- 커밋 기록, 브랜치 정보, 원격 저장소 설정 등 모든 Git 내부 정보를 담고 있다.
		- 파일명 앞에 .이 붙으면 숨김 폴더라는 의미이고 사용자가 실수로 건드리지 않도록 일부러 숨김 폴더로 지정한 것이다.
	- .idea/
		- InteliJ IDEA의 프로젝트 설정
		- 개인 개발환경 설정 - 탭 위치, 창 크기, 최근 열람 파일, 실행 설정 등
		- 공유할 필요 없는 정보가 많아 `.gitignore`로 무시
		- 단, 팀에서 InteliJ를 공통으로 쓸 경우 일부 설정 파일(module.xml)은 선택적으로 공유
	- front-end.iml
		- InteliJ가 인식하는 프론트엔드 모듈의 구성 정보 파일
		- SDK, 소스 디렉토리, 빌드 출력 등의 메타데이터 포함
		- 보통 `.idea/modules.xml`에서 이 `.iml`을 참조함
		- 지우면 InteliJ가 해당 모듈을 인식 못함 > 다시 등록 필요
		- 팀 개발 시 충돌 우려로 `.gitignore`로 무시하는 경우가 많다.

- MySQL 서버가 죽었다.
	- 문제 mysql cli에 접속하여 비밀번호를 맞게 입력해도 몇초후 반응이 없다가 강제 종료가 된다.
	- jmeter 트러블 슈팅하는 과정에서 mysql 프로세스를 강제 종료했더 기억이 났다.
	-  `tasklist | findstr mysqld` - 
		  
	- `Get-Service | findstr MySQL` - 윈도우 서비스 중 mysql만 찾는 명령어
		`Stopped MySQL80 MySQL80` - 중단되어있는걸 볼 수 있다.
	- `Start-Service MySQL80` - 
		`경고: 'MySQL80(MySQL80)' 서비스가 시작될 때까지 기다리는 중...`
	- `Get-Service | findstr MySQL` - 다시한번 실행하여 확인
		`Running  MySQL80 MySQL80`
	
- Layer
	- 소프트웨어 엔지니어링에서 말하는 Layer는 네트워크 통신을 기능별로 분류하여 독립적인 층(Layer)을으로 구성한 것
	- 각 계층은 자신의 역할에만 집중적으로 수행하고, 바로 위/아래 계층과만 상호작용한다. 
	- 계층으로 나누는 이유
		- 역할 분리
			- 각 계층은 자신에게 주어진 역할만 처리 > 설계와 구현이 쉬워진다.
		- 모듈화
			- 계층간 내부 구현을 몰라도 된다. 각 계층만 교체하거나 개선 가능
		- 호환성
			- 서로 다른 시스템/운영체제도 동일한 계층 규칙만 따르면 통신 가능
		- 유지보수 용이
			- 특정 계층만 수정해도 전체 시스템 재작성 없이 개선 가능
		- 문제 추적 쉬움
			- 네트워크 오류 발생 시 어느 계층에서 문제가 생겼는지 쉽게 추적 가능
	
- TCP/IP 4 Layer
	- TCP/IP 4 Layer란?
		- 컴퓨터 간 통신을 4가지 역할을 계층으로 나눈 인터넷 프로토콜 구조이다.
		- 우리가 실제 사용하는 인터넷 통신의 기본 설계 구조이다.
	- 1계층 네트워크 엑세스 계층 (Network access Layer)
		- OSI 7계층의 물리 계층과 데이터 링크 계층에 해당한다.
		- 데이터 링크 계층에서 사용되는 주소
		- WIFI, LAN, 패킷망 등에 사용된다.
	- 2계층 인터넷 계층 (Internet Layer)
		- OSI 7계층의 네트워크 계층에 해당한다.
		- 통신 노드 간의 IP 패킷을 전송하는 기능과 라우팅 기능을 담당한다.
		- 프로토콜 - IP, ARP, RARP
	- 3계층 전송 계층 (Transport Layer)
		-  OSI 7계층의 전송 계층에 해당한다.
		- 통신 노드 간의 연결을 제어하고, 신뢰성이 있는 데이터 전송을 담당한다.
		- 프로토콜 - TCP, UDP
	- 4계층 응용 계층 (Application Layer)
		- OSI 7계층의 세션 계층, 표현 계층, 응용 계층에 해당한다.
		- 사용자와 직접 상호작용하는 애플리케이션의 네트워크 동작을 담당하며, HTTP, SMTP, FTP 등의 프로토콜을 통해 데이터를 주고받는다.
		- 프로토콜 - FTP, HTTP, SSH
	- 데이터 흐름과 캡슐화
		- 캡슐화
			- 상위 계층의 데이터를 하위 계층으로 내려보내면서 각 계층의 헤더를 덧붙이는 과정 
		- 송신측 (보내는 쪽)
			1. 응용 계층 (Application Layer)
				- 사용자가 작성한 이메일, 웹 요청 등의 실제 데이터 생성
				- 예 : `GET '/index.html HTTP/1.1`
			2. 전송 계층 (Transport Layer)
				- 이 데이터에 TCP 헤더(포트 번호, 순서, 에러 검출 정보 등)를 붙여 `Segment`로 포장
				- UDP일 경우 UDP 헤더 붙여 `데이터그램` 생성
			3. 인터넷 계층 (Internet Layer)
				- 이 세그먼트에 IP 헤더를 붙여 IP 패킷으로 만듦
				- 목적지 IP 주소 등 포함
			4. 네트워크 엑세스 계층 (Network Access Layer)
				- IP 패킷에 이더넷 헤더(MAC 주소 포함)와 트레일러를 붙여 `Frame`으로 변환
				- 이후 0과 1의 `Bit Stream`으로 물리 전송
		- 수신측 (받는 쪽) - 역캡슐화(Decapsulation)
			- 받은 비트 스트림을 `Frame` > `Packet` > `Segment` > `Data` 순으로 헤더를 벗기며 위로 전달
			- 최종적으로 응용 계층이 사용자에게 정보를 보여준다.
- Header
	- Header란?
		- `데이터가 어떻게, 어디로, 어떤 방식으로 전달되어야 하는지 설명하는 메타정보`를 담기 위한 존재
		- 즉, 데이터 자체가 아니라, 그 데이터를 제대로 전송하고, 해석하기 위한 메타정보이다.
	- 핵심 목적
		- 전송 정보 전달
			- 목적지 주소(IP, MAC), 포트 번호, 시퀀스 번호 등
		- 데이터 구조 설명
			- 데이터 길이, 형식, 인코딩 방식 등
		- 처리 방식 안내
			- 이 데이터가 요청인지 응답인지, 암호화 여부 등
		- 보안 및 인증
			- JWT API 키 등 접근 권한/검증 정보 포함 가능(HTTP 계층 등)
- Body
	- 실제로 전달하고자하는 데이터 내용물(문자열, JSON, 파일, 영상 등)
---
- Routing
	- Routing이란?
		- 네트워크 세계에서 라우팅이란, 패킷에 포함된 주소 등의 상세 정보를 이용하여 목적지까지 데이터 또는 메세지를 체계적으로 다른 네트워크에 전달하는 경로 선택(Path Determination) 그리고 스위칭(Switching)하는 과정을 의미한다.
		- 쉽게 말하면 라우팅이란 데이터가 전달되는 과정에서 여러 네트워크들을 통과해야하는 경우가 생길 수 있는데, 여러 네트워크들의 연결을 담당하고 있는 라우터 장비가 데이터의 목적지가 어디인지 확인하여 빠르고 정확한 길을 찾아 전달해주는 것이다.
		- 우리가 처음 가보는 장소를 찾아가기 위해 하는 모든 행동들을 라우터가 패킷을 전달하는 라우팅 과정에 비교하면 쉽게 이해할 수 있다.
		- 맛집을 찾아가기 위해 지도앱으로 찾아가는 과정을 예시로 우리가 `맛집의 정확한 위치를 파악`하는 것처럼 전달받은 패킷을 전달하기 위해 라우터도 가장 먼저 목적지가 어디인지 `IP주소를 확인한다.` 그런 뒤에 `가장 빠른 경로가 어디인 지를 확인`하고 그 경로를 가기 위해서는 자신의 `어느 인터페이스로 패킷을 내보내야 하는 지 결정할 것`이다. 그런 뒤에 결정한 인터페이스로 패킷을 전달하면 그 패킷은 또 다른 라우터로 전달되어 위와 같은 과정을 목적지 네트워크에 도착할 때까지 반복할 것이다.
		- 이처럼 데이터를 목적지까지 전달하기 위한 모든 일련의 과정을 통틀어 Routing이라고 한다.
	- Routing을 하기 위해서 필요한 것
		- 출발지와 목적지의 네트워크 정보
			- 만약 장비가 목적지가 있는 네트워크의 존재를 모른다면 경로 설정을 해줄 수가 없을 것이고, 그렇기 때문에 전달이 불가능해질 것이다.
		- 목적지로 가는 모든 경로
			- 출발지와 목적지 사이의 어떤 경로들이 있는지 알고 있어야 그 중에서 최적 경로를 선택할 수 있다.
		- 최적 경로
			- 데이터를 전달하기 위해서 모든 경로를 사용할 필요가 없기 때문에 학습한 경로 중 가장 최적의 경로를 하나 선택한다. 이결로를 저장하는 곳을 Routing Table이라고 부르며 L3 장비는 이 Table 정보를 사용하여 패킷을 전달한다.
		- 지속적인 네트워크 상태 확인
			- 데이터를 전달해주려는 경로가 어딘 지는 만약 그 경로가 다운된 상태라서 사용할 수 없는 경우라면?
			- Routing Table에 저장된 경로로 전달이 가능한 상태인지 지속적으로 네트워크 상태를 확인해서 네트워크 정보를 항상 올바른 최신 정보로 유지해야한다.
	- Routing에서 말하는 경로는 무엇인가?
		- Routing은 무수히 많은 경로 중 가장 최적의 경로를 찾기 위한 과정이라면.. 이 경로에 대한 실체는 무엇인가 의문을 가져보았다.
		- 경로는 실제 물리적 선이자 논리적 연결 정보이다.
		- 물리적으로는 전 세계를 잇는 케이블, 광섬유, 라우터, 스위치 등



- JSON
- IP
- Port
- Sessoion
- LazeLoading이란 무엇인가요?

- DB slow query가 무엇인가?

- 로드밸런싱이란 무엇인가?

- application.yml의 hikari, apache tomcat server 설정에 대해 설명해주세요
	- hikari:  
		  maximum-pool-size: 400  
		  minimum-idle: 20  
		  idle-timeout: 10000   
		  max-lifetime: 30000 
	- server:  
		  tomcat:  
		    threads:  
		      max: 2000   
		    accept-count: 3000   
		    connection-timeout: 30000 

- DB conection pool이란 무엇인가?
- 요청 대기 큐를 왜 사용하였는가?
- jmeter 테스트 결과 분석을 어떻게 하였고, 원인을 어떻게 추정하였는가?
	- 원인 분석 방법
		- summary report - 평균요청시간, 초당응답률, 에러율을 분석
		- SpringBoot log를 통해 발생한 에러 확인
		- Jmeter - view reulst tree의 response data (request body)의 에러 확인
		- 각 에러에 대한 search, 평균 요청시간 낮추기, 초당 응답율 높이기, 에러율 낮추기 위한 search
- 원인
	- DB Index 
	- DTO 변환 작업이 무겁고 반복적
	- DB 커넥션 고갈
	- API 서버 단일 인스턴스 병목
	- Nginx proxy 설정 미흡
	- JMV 튜닝 미흡

- 로드밸런싱 - nginx


- [[Nginx] 엔진엑스 기본 환경 설정](https://12bme.tistory.com/366)




---
