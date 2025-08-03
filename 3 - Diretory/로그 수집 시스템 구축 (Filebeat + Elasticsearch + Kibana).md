---
created:
---

---
- [[0 Home]]
---

### 개요 
- [GPT - 로그 수집 시스템 구축](https://chatgpt.com/c/687a4c96-59f4-8012-abfa-c0d781523d37)
- 로그 수집 시스템 구축
	- filebeat + elasticsearch + kibana
- 목표
	- [x] project의 stacktrace가 나오도록 한다. ✅ 2025-07-21
	- [x] setup 완료하기 ✅ 2025-07-18
	- [x] project의 test가 실행되면 log 출력이 나오도록하기 ✅ 2025-07-21
	- [ ] login의 요청 처리 속도의 느린 원인을 로그로부터 확인하기
	- [ ] 문제 해결 하기
	- [ ] 각 프로젝트의 가이드 라인을 만들어 이해하기 쉽게 포스팅하기
---
### 타임라인

- 최우선 목표였던 스택 트레이스가 전부 출력이 되지않고 요약되어 출력되는 문제 발생했다. 문제는 내가 이 3가지의 프로그램들의 동작 원리를 이해하고 있지 않기 때문에 뭐가 문제인지 구체적으로 알 수 없다고 판단하여, 우선 이 세가지의 기술에 대해 좀 더 깊이 공부하고 searching을 할 것이다.

- 스택 트레이스가 적용 안되었던 이유
	- filebeat의 multiline은 여러줄로 구성된 로그를 하나의 로그 이벤트로 묶어서 사용하기 위한 용도로 사용된다.
	- parsers: - multiline:
		- 위의 사진을 보면 `18시56분` 시간대에는 멀티라인이 재대로 적용이 되지않아 이벤트가 묶이지 않고 한줄 단위로 나오는걸 볼 수 있다.
	- ![[Pasted image 20250720191306.png]]
		- 그리고 위에 `19시07분`에는 `NullPointException` 기준으로 멀티라인이 잘적용한 것을 볼 수 있다.

	- 트러블 슈팅 multiline 설정 미적용 문제 해결
		이번 작업을 통해 **Filebeat의 버전 차이에 따른 설정 방식의 중요성**을 다시 한 번 실감했다. 기존에 사용하던 `multiline.pattern` 방식은 Filebeat 8.x 이상에서 권장되는 `parsers - multiline` 방식과는 달랐고, `filestream` 타입이 아닌 이전 방식에서는 적용되지 않았다.
		
		처음엔 여러 블로그를 참고했지만, 대부분이 구버전 기반의 내용이라 최신 환경에는 맞지 않았다. 결국 **공식 문서를 직접 확인**했고, 그 안에는 언어별 예외 로그 구조에 맞춘 **멀티라인 설정 방법이 매우 상세하고 명확하게 설명**되어 있었다.
		
		공식 가이드를 참고해 설정을 바꾼 후, Java 스택트레이스가 **정확히 하나의 메시지로 Kibana에 출력되는 것을 직접 확인**할 수 있었다. 이번 경험은, **버전 확인과 공식 문서의 중요성**, 그리고 최신 기술 흐름에 맞는 정보의 선별 능력이 얼마나 중요한지를 깨닫게 해준 계기였다.

---

- kibana에서 불필요한 filed를 제거하고 message, timestemp, log path만 남기도록 해볼 것이다.
- 추후 다시 추가하거나 필요할 떄를 위해 기존의 filed 값을 아래에 남긴다. 
```
@timestamp
agent.ephemeral_id
agent.hostname
agent.id
agent.name
agent.type
agent.version
data_stream.dataset
data_stream.namespace
data_stream.type
ecs.version
host.name
input.type
log.file.fingerprint
log.file.idxhi
log.file.idxlo
log.file.path
log.file.vol
log.flags
log.offset
message
```



---
### 키워드

-  [[Filebeat]]
-  [[Elasticsearch]]
-  [[Kibana]]

---
### 동작 원리

---
### 트러블 슈팅

---
### 명령어
- 자동화 start 명령어
```
cd C:\workspace
.\start-techie.ps1
```

- kibana에서 nginx 에러로그 KQL 찍어보기
```
log_type : "nginx-error"
```

---
### 코드
- filebeat
```
filebeat.inputs:
  - type: filestream
    id: app-logs
    enabled: true
    paths:
      - C:/workspace/filebeat/logs/app.log
    parsers:
      - multiline:
          type: pattern
          pattern: '^[[:space:]]'
          negate: false
          match: after

processors:
  - drop_fields:
      fields: ["log.offset", "log.file.fingerprint", "input.type"]

output.elasticsearch:
  hosts: ["https://localhost:9200"]
  username: "elastic"
  password: "XXX"
  ssl.certificate_authorities: ["C:/workspace/elasticsearch-9.0.3/config/certs/http_ca.crt"]

setup.kibana:
  host: "https://localhost:5601"
```
- elasticsearch
```
xpack.security.enabled: true
xpack.security.enrollment.enabled: true

xpack.security.http.ssl:
  enabled: true
  keystore.path: certs/http.p12

xpack.security.transport.ssl:
  enabled: true
  verification_mode: certificate
  keystore.path: certs/transport.p12
  truststore.path: certs/transport.p12

http.host: 0.0.0.0
cluster.initial_master_nodes: ["ATOO"]
```
- kibana
```
server.port: 5601
server.host: "localhost"

elasticsearch.hosts: ["https://localhost:9200"]
elasticsearch.serviceAccountToken: "AAEAAWVsYXN0aWMva2liYW5hL2tpYmFuYTpMaGZtem83dlJyS2pxeTJFSFFoTExR"

xpack.encryptedSavedObjects.encryptionKey: "a_secure_and_long_key_123456789012345678901234"
xpack.security.encryptionKey: "another_secure_key_abcdefghijklmnopqrstuv"

elasticsearch.ssl.certificateAuthorities: [ "C:/workspace/elasticsearch-9.0.3/config/certs/http_ca.crt" ]
elasticsearch.ssl.verificationMode: full
```

---
### 타임라인 8/3

- Nginx upstream timeout → `8081` 포트에서 응답 없음
```
upstream timed out (10060: A connection attempt failed...) 
while reading response header from upstream,
client: 127.0.0.1,
request: "POST /login",
upstream: "http://127.0.0.1:8081/login"
```
- `JMeter가 보낸 /login 요청이 Nginx를 통해 8081번 백엔드로 전달되었는데 백엔드 서버(8081)가 응답을 주지 않아 타임아웃 발생함.`
- 포스트맨 단일 로그인 요청을 해본 결과 `532ms(0.5초)`로 빠른 응답시간이 확인
- nginx를 통해 로드밸런싱으로 로그인 대량 요청을 할 때 앞의 서버들이 처리하는데 위의 요청들이 대기하다가 결국 죽어버리는 것으로 추측

- 이후 진행해볼 테스트는
	- Spring에 `OncePerRequestFilter`로 모든 요청 로그 찍기
		- 성공/실패 막론하고 진입 시점 기록
	- 로그인 메서드에 진입-종료 로그 추가
		- 어느 단계에서 멈췄는지 추적
	- Hikari 커넥션 상태 모니터링
		- HikariPool-1 - Timeout after ... 로그 확인
	- GC 로그 활성화
		- -Xlog:gc*
	- Nginx proxy_read_timeout 5~10초로 낮추기
		- 문제 구간 빨리 포착 가능
	- 대기 큐 만들어서 문제해결해보기
- Nginx의 Error 로그 분석하기
- Nginx의 유의미한 원인을 못찾으면 k6로 바꿔보기

---

### 참고

[filebeat multiline 설정 가이드 | 공식](https://www.elastic.co/docs/reference/beats/filebeat/multiline-examples)
[multiline 설정 가이드](https://velog.io/@juhwanheo/Elastic-Stack-Filebeat-LogBack-multiline-pattern-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0)
[multiline 테스트](https://go.dev/play/p/uAd5XHxscu)


---