---
created:
---

---
- [[0 Home]]
---
- [[#개요]]
- [[#타임라인]]
- [[#명령어]]
---
### 개요 
- [GPT - 로그 수집 시스템 구축](https://chatgpt.com/c/687a4c96-59f4-8012-abfa-c0d781523d37)
- 로그 수집 시스템 구축 : filebeat + elasticsearch + kibana
- 목표
	- [x] project의 stacktrace가 나오도록 한다. ✅ 2025-07-21
	- [x] setup 완료하기 ✅ 2025-07-18
	- [x] project의 test가 실행되면 log 출력이 나오도록하기 ✅ 2025-07-21
	- [ ] login의 요청 처리 속도의 느린 원인을 로그로부터 확인하기
	- [ ] 문제 해결 하기
	- [ ] 각 프로젝트의 가이드 라인을 만들어 이해하기 쉽게 포스팅하기
---
### 타임라인

- 7/21
    - 개요
        - 최우선 목표였던 스택 트레이스가 전부 출력이 되지않고 요약되어 출력되는 문제 발생했다. 문제는 내가 이 3가지의 프로그램들의 동작 원리를 이해하고 있지 않기 때문에 뭐가 문제인지 구체적으로 알 수 없다고 판단하여, 우선 이 세가지의 기술에 대해 좀 더 깊이 공부하고 searching을 할 것이다.
    - 스택 트레이스가 적용 안되었던 이유
    	- filebeat의 multiline은 여러줄로 구성된 로그를 하나의 로그 이벤트로 묶어서 사용하기 위한 용도로 사용된다.
    	- parsers: - multiline:
		- 위의 사진을 보면 `18시56분` 시간대에는 멀티라인이 재대로 적용이 되지않아 이벤트가 묶이지 않고 한줄 단위로 나오는걸 볼 수 있다.
    	- 그리고 위에 `19시07분`에는 `NullPointException` 기준으로 멀티라인이 잘적용한 것을 볼 수 있다.
	- 스택 트레이스 성공 스크린샷
    	- [[Pasted image 20250720191306.png]]
	- 트러블 슈팅 multiline 설정 미적용 문제 해결
		이번 작업을 통해 **Filebeat의 버전 차이에 따른 설정 방식의 중요성**을 다시 한 번 실감했다. 기존에 사용하던 `multiline.pattern` 방식은 Filebeat 8.x 이상에서 권장되는 `parsers - multiline` 방식과는 달랐고, `filestream` 타입이 아닌 이전 방식에서는 적용되지 않았다.
		
		처음엔 여러 블로그를 참고했지만, 대부분이 구버전 기반의 내용이라 최신 환경에는 맞지 않았다. 결국 **공식 문서를 직접 확인**했고, 그 안에는 언어별 예외 로그 구조에 맞춘 **멀티라인 설정 방법이 매우 상세하고 명확하게 설명**되어 있었다.
		
		공식 가이드를 참고해 설정을 바꾼 후, Java 스택트레이스가 **정확히 하나의 메시지로 Kibana에 출력되는 것을 직접 확인**할 수 있었다. 이번 경험은, **버전 확인과 공식 문서의 중요성**, 그리고 최신 기술 흐름에 맞는 정보의 선별 능력이 얼마나 중요한지를 깨닫게 해준 계기였다.
    
- 7/26
    - kibana filed 설정
        - kibana에서 불필요한 filed를 제거하고 message, timestemp, log path만 남기도록 해볼 것이다.
        - 추후 다시 추가하거나 필요할 떄를 위해 기존의 filed 값을 아래에 남긴다. 
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

-  8/3
    - Nginx upstream timeout → `8081` 포트에서 응답 없음
    - log
        `upstream timed out (10060: A connection attempt failed...)`
        `while reading response header from upstream,`
        `client: 127.0.0.1,`
        `request: "POST /login",`
        `upstream: "http://127.0.0.1:8081/login"`
        
    - JMeter가 보낸 /login 요청이 Nginx를 통해 8081번 백엔드로 전달되었는데 백엔드 서버(8081)가 응답을 주지 않아 타임아웃 발생함.
      
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

- 08/11
    - hikari pool size를 16으로 감소 조절하여 5분 9,000 요청을 처리하면서 에러율 0%로 정상동작이 된다는 것을 확인하며 해결..한줄 알았지만, 다시 에러가 발생했다. 내가 왜 이러한 문제와 현상이 생겼는지 설명을 못하고있다는 사실을 자각하였다. 따라서 나는 이전에 있던 개념들을 차근차근 하나씩 다시 되짚어보면서 해당 설정들을 이해하고 설명할 수 있도록 정리해보려고 한다. 시작은 서버단부터 올라가는 방향으로 진행할 것이다.
      [[로그인 성능 문제, 계층별 이해와 분석]]
    - 확인 순서
        1. 현재 문제 상황 인지 및 설명
        2. CPU, 메모리, GC 로그 확인
            1. CPU, 메모리(heap 등), GC 로그 이해하고 확인
        3. application.yml 확인
            1. 각 설정 이해하고 확인
        4. 소스코드 확인
            1. 로그인 로직 소스 코드 이해하고 확인
        5. db 확인
            1. 커넥션 풀, 인덱스 여부 등 이해하고 확인
            2. 서버 로그를 강화해서 히카리풀 또는 하이버네이트 로그 확인
        6. mysql 확인
            1. mysql 풀사이즈 설정, 타임아웃 설정 찾아보고 적절하게 조정
        7. hikari 확인
            1. hikari 설정 이해하고 확인
        8. tomcat thread 확인
            1. tomcat 설정  이해하고 확인
        9. nginx 확인
            1. conf 이해하고 확인
        10. jmeter확인
            1. 세팅이 정상적인지 이해하고 확인
    
    
- 현재 문제 상황 인지 및 설명
    - 프로그램 버전
        - **Java** : Oracle JDK 17
        - **Spring Boot**: 3.3.4
        - **Nginx**: 1.28.0
        - **Jmeter**: 5.6.3
        - **MySQL**: 8.0
        - **HikariCP**: 5.1.0
        - **Hibernate ORM**: 6.5.3.Final
        - **JJWT**: 0.12.3
        - **ModelMapper**: 3.1.1
        - **Filebeat**: 9.0.3
        - **Elasticsearch**: 9.0.3
        - **Kibana**: 9.0.3
        - **CPU Core** : NumberOfCores 14 |  NumberOfLogicalProcessors 18
          
    - 문제 상황
        Jmeter로 내가 만든 로그인 기능의 부하 테스트를 진행하여 20000명 유저를 5분간 분산하여 부하를 주었다. 
        상대적으로 적은 양의 부하를 주었음에도 에러가 평균 30%이상 발생하고 로그인 요청에 대한 평균 응답 시간이 3초 이상 발생
        로그인 요청 응답시간을 정상적으로 줄이기 위해 원인을 찾도록 하였다.
        중요한 것은 단순한 추측으로 내가 여기저기 확인해보는 것이 아닌 로그인 응답 지연의 원인이 되는 로그라는 명확한 증거를 발견하고
        그 원인에 대해 올바른 고민을하고 문제에 대한 해결 수단을 내가 직접 찾고 적용하여 문제에 대한 해결을 하는 것이 궁극의 목표이다.
        여기서 추가적으로 문제를 발견하였다.
        우선 Jmeter test에 대한 에러 로그(스택트레이스)가 서버에 뜨지 않는다.
        서버에서 로그가 안뜨기 때문에 증거가되는 명확한 로그를 볼 수 없다.
        따라서 내가 해본 시도는 log 수집 시스템을 세팅하여 재대로 확인해보았다.
        filebeat, elasticsearch, kibana를 통해 파일비트가 수집한 로그를 모아서 엘라스틱서치 그 로그를 읽고 키바나가 그것을 시각화하여
        보다 효율적으로 로그 관리하여 문제를 찾아보기 위함이었다.
        하지만 여전히 로그인 실패에 대한 유의미한 로그를 찾아 볼 수 없었다.
        server에서는 확인을 못하였기 때문에 nginx에도 로그를 수집하여 확인해 본 결과
        `8080~8087 upstream timed out` 에러를 확인하였다. 이 에러의 의미를 이해하고 원인이 되는지 확인해야한다.
        그 밖에도 hikari pool size(16으로 감소 조절), nginx 설정을 조정하여 테스트해본 결과
        9000명을 5분간 부하테스트한 결과 에러율 0%라는 처음으로 유의미한 결과를 확인하였다.
        20000명을 5분간 부하테스트한 결과에 대해선 여전히 문제가 발생하였다. 
        여기서 내가 막연하게 설정 및 테스트하고 왜 이런 결과가 나왔는지 설명을 못하며, 
        막연하고 어떻게 손을 봐야하는지 감을 못잡았다는걸 깨달았다.
        차근차근.. 내가 지금까지 거쳐왔던 모든 개념들을 완벽하게 이해할 필요가 있다고 느꼈다.
        멘토님께서 주신 과제와 동시에 병행하도록 하자.
        1. 모든 개념을 설명할 수 있도록 이해한다.
        2. 서버 로그를 강화해서 히카리풀 또는 하이버네이트 로그를 발견하자
        
---

```
2025-08-24T02:04:20.416+09:00 ERROR 48120 --- [http-nio-8083-exec-23] o.a.c.c.C.[.[.[/].[dispatcherServlet] : Servlet.service() for servlet [dispatcherServlet] in context with path [] threw exception [Request processing failed: org.springframework.dao.DataAccessResourceFailureException: Unable to acquire JDBC Connection [HikariPool-5 - Connection is not available, request timed out after 10211ms (total=16, active=16, idle=0, waiting=24)] [n/a]] with root cause

```

- Tomcat/Spring) 에러 로그이다.
- 요청 처리 중 DB 커넥션을 얻으려다 **10.211초(`connection-timeout`) 대기 후 실패
- 당시 풀 상태가 `total=16, active=16, idle=0, waiting=24` → 풀 포화였다.
- Spring이 이를 `DataAccessResourceFailureException`으로 래핑해 서블릿에서 에러로 기록한 것
- 원인 후보: 커넥션 누수, 느린/락 쿼리, 톰캣 스레드 과다 대비 풀 크기 부족, DB 연결 한도 등

1. **“예외 메시지 안에 Hikari 에러가 있다”는 뜻**
    
    - 로그 라인은 스프링/톰캣이 찍었지만, 메시지에  
        `HikariPool-5 - Connection is not available, request timed out …` 가 포함됨.
    - 이 문구는 **Hikari 풀**이 던지는 에러라서, **원인=풀에서 커넥션을 못 빌림**을 의미.
        
2. **“10.211초 대기 후 실패”의 뜻**
    
    - 코드가 `DataSource.getConnection()` 호출 → 풀에 빈 커넥션이 없어 **대기**.
    - `connection-timeout(=10초)`까지 기다렸지만 반납이 없어 **타임아웃 예외** 발생.
        
3. **풀이 포화되면 생기는 문제**
    
    - 요청 스레드가 **줄 서서 대기** → **지연↑** → **타임아웃/에러** 증가.
    - 대기 스레드가 많아지면 **연쇄 장애**(큐 폭증, CPU 유휴, 전반적 처리량↓).
        
4. **`total=16, active=16, idle=0, waiting=24` 뜻**
    
    - **total**: 현재 풀에 열린 실제 커넥션 수(= active + idle) → 보통 **최대치(16)** 까지 차있음.
    - **active**: **대여 중**(사용 중) 커넥션 수 = 16 (가득 찼음).
    - **idle**: 즉시 빌릴 수 있는 **여유분** = 0.
    - **waiting**: 커넥션을 **기다리는 스레드 수** = 24 (줄 서 있는 중).
        
5. **`DataAccessResourceFailureException` 뜻**
    
    - 스프링의 표준 **데이터 접근 실패** 런타임 예외.
    - 원래의 `SQLException`(여기선 Hikari 타임아웃)을 **감싸서(래핑)** 던짐.
        
6. **“래핑해서 서블릿에 에러 기록”의 뜻**
    
    - 흐름: `Hikari(SQLException)` → **스프링이 표준 예외로 래핑**(`DataAccessResourceFailureException`) →  
        이 예외가 웹 계층까지 올라와 **DispatcherServlet이 ERROR 로그로 기록**.
    - 로그 끝의 _with root cause_ 는 **원인 예외가 중첩**되어 있음을 뜻함.
        

작은 그림(요약 흐름):  
요청 → 컨트롤러/리포지토리 → `getConnection()` → **풀 대기** → 타임아웃 → `SQLException` → **스프링 래핑** → **서블릿 ERROR 로그**.  


- **용량 부족**: 동시 트래픽 대비 풀/DB 크기가 작음.
    
- **체류 시간 과다**: 느린/락 쿼리, 긴 트랜잭션, **커넥션 누수**로 반납이 늦음.
    

즉, “풀 크기”를 늘리거나 “빨리 반납되게(쿼리·트랜잭션·누수 개선)” 하거나 둘 다 필요해.
  



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


---
- gpt 요청
    - **로그인 요청 쿼리 실행 계획 분석 방법**하고, 지금처럼 p95가 긴 원인별 조치 우선순위표를 만들어줄 수 있어.
- 
git fetch origin
git checkout backend/refact/login_lazy


---

### 참고

[filebeat multiline 설정 가이드 | 공식](https://www.elastic.co/docs/reference/beats/filebeat/multiline-examples)
[multiline 설정 가이드](https://velog.io/@juhwanheo/Elastic-Stack-Filebeat-LogBack-multiline-pattern-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0)
[multiline 테스트](https://go.dev/play/p/uAd5XHxscu)
[데이터베이스 커넥션 풀 및 JPA, 하이버네이트 설정 최적화(https://mangkyu.tistory.com/413)

---