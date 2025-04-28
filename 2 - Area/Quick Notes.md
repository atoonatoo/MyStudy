---
created:
---
---
- [[0 Home]]
---
- 다수의 인스턴스로 서버를 생성했다면 분산 시스템을 적용하라
	- LB 로드밸런서가 필요하다.
	- 그럼 어떻게 로드밸런서를 만드는가?
	- nginX를 설치하여서 해결할수있다.
	
- 그렇다면 이방법보다 더 트레픽 분산 시스템을 설계하기 쉬운 것은 무엇인가?
	- 쿠버네티스
	  

- 현재 진행중
	- 외부 API 대량 호출 및 모니터링
		- [Grafana 대시보드 연결 (1차 모니터링 화면 구축)](https://chatgpt.com/c/68060da7-dbc8-8012-8fb0-0e13a30cec6f)
		- Alertmanager 경고 세팅 강화 (2차 알림 시스템 구축)
		- JMeter로 부하 테스트 (모니터링 + 경고 트리거 검증)
		- Grafana 알람(Alert) 설정 (3차 시각적 경고 시스템)
		- 스케일아웃 포트 관리 및 자동화 (4차 확장성 강화)
		- 최종 모니터링 시나리오 작성 및 테스트
		-  순서 제안
			1. Grafana → Prometheus 연결 → 대시보드 세팅
			2. JMeter → 부하 발생 → 모니터링 테스트
			3. Alertmanager → Slack + Webhook 경고 흐름 최종 점검
			4. Grafana Alerts → 추가 알람 설정
		- 선택
			- "👉 먼저 Grafana 대시보드 연결부터 하자"
			- "👉 바로 JMeter 부하 테스트로 넘어가자"
			- "👉 Alertmanager 알람 먼저 세팅 강화하자"
	- [스파이크성 트래픽을 재현](https://chatgpt.com/c/680ddf8e-e858-8012-a55d-b42fc0317ab6)
	- 데이터가 많을 때 조회하는 성능 개선

- 정보처리기사 암기
	- Death of ping
	- Smurfing
	- SYN Flooding
	- Tear drop 
	- Land Attack
	- Ddos
	- LRU
	- VPN
	- 방화벽
	- 칩입탐지시스템(IDS)  
	- 침입방지시스템(IPS)
	- 데이터유출방지(DLP)
	- 웹 방화벽
	- NAC
	- ESM
	- SIEM
	- SSH
	- 탬퍼 프루핑(Tamper Proofing)
	- OAuth (Open Authoration)
	- 생성 패턴 (Creational)
	- 구조 패턴 (Structural)
	- 행위 패턴 (Behavioral)
	- 추상 팩토리
	- 빌더
	- 팩토리 메서드
	- 프로토타입
	- 싱글톤
	- 어댑터
	- 브리지
	- 컴포지트
	- 데코레이터
	- 퍼싸드
	- 플라이웨이트
	- 프록시
	- 책임 연쇄
	- 커맨드
	- 인터프리터
	- 반복자
	- 중재자
	- 메멘토
	- 옵저버
	- 상태
	- 전략
	- 탬플릿 메소드
	- 방문자

- LINK
	- [ChatGPT API Token Limit 해결하기 (요금 줄이기)](https://velog.io/@noh0907/ChatGPT-API-Token-Limit-%ED%95%B4%EA%B2%B0%ED%95%98%EA%B8%B0-%EC%9A%94%EA%B8%88-%EC%A4%84%EC%9D%B4%EA%B8%B0)
	- [GPT 성능 최적화 응답 품질과 속도 개선을 위한 가이드](https://doitevery.com/entry/ChatGPT-%EC%84%B1%EB%8A%A5-%EC%B5%9C%EC%A0%81%ED%99%94-%EC%9D%91%EB%8B%B5-%ED%92%88%EC%A7%88%EA%B3%BC-%EC%86%8D%EB%8F%84-%EA%B0%9C%EC%84%A0%EC%9D%84-%EC%9C%84%ED%95%9C-%EA%B0%80%EC%9D%B4%EB%93%9C#google_vignette)
	- [프롬프트 캐싱 참고문헌 1](https://docs.anthropic.com/ko/docs/build-with-claude/prompt-caching)
	- [프롬프트 캐싱 참고문헌 2](https://wikidocs.net/262049)
	- [PostMan 가이드 Infa](https://inpa.tistory.com/entry/POSTMAN-%F0%9F%92%BD-%ED%8F%AC%EC%8A%A4%ED%8A%B8%EB%A7%A8-%EC%82%AC%EC%9A%A9%EB%B2%95-API-%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%9E%90%EB%8F%99%ED%99%94-%EA%B3%A0%EA%B8%89-%ED%99%9C%EC%9A%A9%EA%B9%8C%EC%A7%80#%ED%85%8C%EC%8A%A4%ED%8A%B8_%EC%A3%BC%EA%B8%B0_%EC%9E%90%EB%8F%99%ED%99%94_monitor_collection)
	- [서버 부하 테스트](https://velog.io/@kimhalin/%EC%84%9C%EB%B2%84-%EB%B6%80%ED%95%98-%ED%85%8C%EC%8A%A4%ED%8A%B8-K6)
	- [외부 API 테스트 1](https://velog.io/@kyle/%EC%99%B8%EB%B6%80-API%EB%A5%BC-%EC%96%B4%EB%96%BB%EA%B2%8C-%ED%85%8C%EC%8A%A4%ED%8A%B8-%ED%95%A0-%EA%B2%83%EC%9D%B8%EA%B0%80)
	- [외부 API 테스트 2](https://velog.io/@jmjmjmz732002/%EC%99%B8%EB%B6%80-API-%EC%84%9C%EB%B2%84%EB%8A%94-mocking%ED%95%98%EC%97%AC-%ED%85%8C%EC%8A%A4%ED%8A%B8%ED%95%B4%EC%95%BC-%ED%95%9C%EB%8B%A4)
	- [외부 API 테스트 3](https://jojoldu.tistory.com/341)
	- [외부 API 테스트 4](https://minnseong.tistory.com/26)
	- [Jmeter 사용법](https://devmango.tistory.com/40)
	- 
	
- 멘토링
	- 메타 인지를 하도록 노력해야한다.
		- 스스로에게 입밖으로 내뱉고 계속 질문하라
		- 
	- 피드백 : 너무 AI 쪽으로 빠져버렸다.
		- 
	- 질문답변 UI 미리 작성
	- 자주 질문 캐싱
	- 우선 순위 설정을 잘정해야한다.
		- 가장 우선 순위 높은 : 내가 이문제를 어떻게 풀어야할지 감이 안온다.
	- 이것 말고도 다른 것을 사용해선 안되는가? 스스로 물어보자

- 키워드
	- Kubernetes 관리 플랫폼
		- 클러스터 구성, 워크로드 배포 등 쿠버네티스 구성 및 자동화 관리
	- MLOps 플랫폼 (Kubeflow) 구성, 관리 자동화 개발
	- Flask
	- Django
	- gRFC
	- RDBMS
	- NoSQL
	
- 












---