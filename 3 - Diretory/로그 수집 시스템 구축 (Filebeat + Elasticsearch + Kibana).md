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
	- [ ] project의 stacktrace가 나오도록 한다.
	- [x] setup 완료하기 ✅ 2025-07-18
	- [ ] project의 test가 실행되면 log 출력이 나오도록하기
	- [ ] login의 요청 처리 속도의 느린 원인을 로그로부터 확인하기
	- [ ] 문제 해결 하기
	- [ ] 각 프로젝트의 가이드 라인을 만들어 이해하기 쉽게 포스팅하기
---
### 타임라인

- 최우선 목표였던 스택 트레이스가 전부 출력이 되지않고 요약되어 출력되는 문제 발생했다. 문제는 내가 이 3가지의 프로그램들의 동작 원리를 이해하고 있지 않기 때문에 뭐가 문제인지 구체적으로 알 수 없다고 판단하여, 우선 이 세가지의 기술에 대해 좀 더 깊이 공부하고 searching을 할 것이다.

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

- filebeat 실행방법
```
cd C:\workspace\filebeat
.\filebeat.exe -e -c filebeat.yml
```

- elasticsearch 실행방법
```
cd C:\workspace\elasticsearch-9.0.3\bin
.\elasticsearch.bat
```

- elasticsearch 정상 동작 확인 하는 방법 및 팁
```
https://localhost:9200
  - 첫 접속 시 로그인 창 → `elastic` 계정 로그인 필요
  - 비밀번호 없을 경우 아래 명령어로 재설정

- elastic 사용자 비밀번호 재설정
.\elasticsearch-reset-password.bat -u elastic --url https://localhost:9200
  - `y` 입력하여 진행
  - 콘솔에 `New value: ...` 출력 → 해당 비밀번호 사용
```

- kibana 실행 방법
```
cd C:\workspace\kibana-9.0.3\bin
.\kibana.bat
```

---

### 참고

[multiline 설정 가이드](https://velog.io/@juhwanheo/Elastic-Stack-Filebeat-LogBack-multiline-pattern-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0)
[multiline 테스트](https://go.dev/play/p/uAd5XHxscu)


---