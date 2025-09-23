---
created:
---

---
- [[Home]]
- [[5 - 분류/3 - Area/learning]]
---

- 기본 개념 요약
	- 파일 기반 로그을 수집해 Elasticsearch나 Logstash로 전송하는 경량 에이전트
	- Filebeat는 사용자가 지정한 로그 파일이나 위치를 모니터링하고, 로그 이벤트를 수집하여 인덱싱을 위해 Elasticsearch 또는 Logstash로 전달한다.
	
- 작동 방식
	- Filebeat → 로그 이벤트 전송 → Elasticsearch → 이벤트를 인덱싱 (검색 가능한 JSON 문서로 저장) → Kibana → 검색 및 시각화
	1. Filebeat가 시작하면 로그 데이터로 지정한 위치를 찾는 하나 이상의 입력이 시작된다.
	2. Filebeat가 찾은 각 로그에 대해 Filebeat는 harvester를 시작한다.
	3. 각 harvester는 새 콘텐츠에 대한 단일 로그를 읽고 새 로그 데이터를 libbeat로 전송한다.
	4. libbeat는 이벤트를 집계하여 Filebeat에 설정된 출력으로 데이터를 전송한다.

- Filebeat 특징
	- 애플리케이션 가동 중단은 시스템 환경에 관계없이 언제 어디서나 일어날 수 있다. Filebeat는 로그를 라인별로 읽고 전달하며, 시스템이 중다되는 경우에도 마지막 중단점을 기억하여 재가동 한다.
	  
	- Filebeat는 통핮 가시성과 보안 데이터 소스를 위한 모듈을 통해 전송하며 일반적인 형식의 로그 데이터를 단일 명령으로 간편하게 수집, 구문 분석, 시각화한다. 운영체제를 기반으로 자동 기본 경로를 Elasticsearch의 Ingest Node 파이프라인 정의 및 Kibana 대시보드와 결합하여 이를 수행한다. 또한, 일부 Filebeat 모듈은 미리 구성된 머신 러닝 작업과 함께 전송된다.
	  
	- Filebeat는 복잡한 설정 없이도 단일 명령으로 로그 수집부터 분석, 시각화, 심지어 머신러닝 기반 이상 탐지까지 자동으로 수행할 수 있도록 설계된 모듈 기반 데이터 수집기이다.

- filebeat 구성 다이어그램![[Pasted image 20250719160223.png]]

- filebeat 동작![[filebeat.gif]]


- 키워드
	- [[Log Event]]
	- [[Indexing]]
	- [[harvester]]
	- [[libbeat]]
	- [[spooler]]
	- [[tail]]
	- [[filebeat module]]

- 참고
	- [공식 홈페이지](https://www.elastic.co/docs/reference/beats/filebeat)
	- 

---