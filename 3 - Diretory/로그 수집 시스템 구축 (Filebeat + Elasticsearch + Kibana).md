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

- Project start 명령어 모음
```
- nginx
cd C:\nginx-1.28.0
.\nginx.exe -c "C:\Users\kkk96\workspace\2 project\team\techie\back-end\nginx\nginx.conf"

- filebeat
cd C:\workspace\filebeat
.\filebeat.exe -e -c filebeat.yml

- elasticsearch
cd C:\workspace\elasticsearch-9.0.3\bin
.\elasticsearch.bat

- kibana
cd C:\workspace\kibana-9.0.3\bin
.\kibana.bat

```



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

[filebeat multiline 설정 가이드 | 공식](https://www.elastic.co/docs/reference/beats/filebeat/multiline-examples)
[multiline 설정 가이드](https://velog.io/@juhwanheo/Elastic-Stack-Filebeat-LogBack-multiline-pattern-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0)
[multiline 테스트](https://go.dev/play/p/uAd5XHxscu)


---