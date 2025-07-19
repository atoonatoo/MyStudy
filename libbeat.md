---
created:
---

---
- [[0 Home]]
---

- Beats 계열의 모든 데이터 수집기(Filebeat, Metricbeat, Packetbeat 등)가 공통적으로 사용하는 내부 라이브러리이자 프레임워크

---

- Filebeat
	- Filebeat의 핵심 구성 요소 중 하나
	- libbeat는 Filebeat 내부에서 수집된 로그 데이터를 처리하고, 구성된 출력(output) 대상으로 안전하게 전송하는 중간 처리기이며, Beat 계열 전체에서 공통적으로 사용하는 핵심 라이브러리이다.
	- harvester가 파일을 열어서 새로 생긴 로그 줄을 읽는 역할이라면, libbeat는 그 줄들을 모아서 정리하고 외부로 전송하는 전송하는 역할이다. 즉, harvester는 로그 파일 감시자, libbeat는 이벤트 처리 엔진이다.
	  
	- 구체적인 역할
		- 이벤트 집계(event buffering)
			- 여러 harvester가 읽은 로그를 한 곳으로 모음
		- 파이프라인 구성(pipeline)
			- 필터링, 변환, 프로세서 적용 등 전처리
		- 출력 전송(output)
			- Elasticsearch, logstash, kafka 등 설정된 대상으로 전송
		- 보안 및 인증 처리
			- TLS, 인증 설정 등을 통해 안전하게 데이터 전송
		- 공통 로직 제공
			- 모든 Beats가 공통으로 사용하는 로직 제공(retry, 압축, ACK 등)
	- 동작 흐름
		1. 로그 파일 : 읽기
		2. Harvester : event 단위로 전달
		3. libbeat : 집계 + 처리 + 변환
		4. Output 모듈
		5. Elasticsearch / Logstash / Kafka / 파일 / 콘솔 ..

---