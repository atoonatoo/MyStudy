
---
- [[0 Home]]
---

---
- DB Index
	- `EXPLAIN` 분석
	- 
- Full GC
	- jstat
		- jstat -gcutil 3772 1000 10
		- jstat -gc 3772 1000
- slow query
- DB CPU 사용률 + IOPS 확인
- JWT 
- 어플리케이션 코드 문제 확인
	- QueryDsl 문제
- 성능모니터
	- %user time
	- %privilged time
- GC 및 Heap 상태
	
- 대용량 데이터 처리
	- [대용량 데이터베이스의 조회 성능을 개선해보자 (1) : 인덱스 적용](https://velog.io/@sckwon770/%EB%8C%80%EB%9F%89%EC%9D%98-%EB%8D%B0%EC%9D%B4%ED%84%B0%EA%B0%80-%EC%A0%81%EC%9E%AC%EB%90%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EB%A5%BC-%EC%A0%81%EC%9A%A9%ED%95%B4-%EC%B5%9C%EC%A0%81%ED%99%94%ED%95%B4%EB%B3%B4%EC%9E%90)
		- 일대다 방식에 대한 트러블 슈팅 블로그 매우 중요한 참고가 될 것이다.
	- [대량 데이터 조회와 유지보수는 어떻게 해야될까?](https://hyune-c.tistory.com/40)
		- 멘토님이 해주신 말씀을 토대로 준비된 게시물
	- [효율이 좋은 쿼리](https://likenow.tistory.com/51)
	- 대용량 데이터 처리에 대한 일목요연한 설명이 되어있다.
	- [대용량 데이터를 빠르게 조회하기 - 페이징 전략 비교(offset, no offset, Where In)](https://guui-dev-lee.tistory.com/16)
	- [대용량시스템에 대한 이해(5) - 300만건 데이터 삽입 & 조회 실습](https://velog.io/@sunsik08/%EB%8C%80%EC%9A%A9%EB%9F%89%EC%8B%9C%EC%8A%A4%ED%85%9C%EC%97%90-%EB%8C%80%ED%95%9C-%EC%9D%B4%ED%95%B45-300%EB%A7%8C%EA%B1%B4-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%82%BD%EC%9E%85-%EC%8B%A4%EC%8A%B5-%EC%A1%B0%ED%9A%8C)
- 문제 해결 -> 수치화 -> 성능 측정
- [A급 코딩 유튜브 - 딩코딩코](https://www.youtube.com/@%EB%94%A9%EC%BD%94%EB%94%A9%EC%BD%94/videos)



- 코딩 노하우
	-  **모든 플랫폼 공통 – 비즈니스 가치를 위한 아키텍처 전략**
	
	- **기술은 수단, 가치는 목적**이다. 리팩토링은 "깨끗한 코드"가 아니라 "매출, 유지보수 비용, 기회비용 절감"이라는 명확한 KPI 기준에서 우선순위가 결정돼야 한다.
	- **선택적 기술 부채 전략**을 세워라. MVP 단계에서는 일부 하드코딩, 강결합도 전략이 될 수 있다. 단, 추후 제거 가능성과 비용은 명확히 계산하고 문서화해놔야 한다.
	- **의사결정 트리(Decision Tree)를 문서화**하는 습관을 가져라. 왜 React를 썼는지, 왜 Firebase Auth를 선택했는지, 왜 해당 컴포넌트를 쪼갰는지 – 미래의 팀원이 이해 못하면 기술 자산이 아니라 기술 부채가 된다.
	
	---
	
	-  **운영 레벨 꿀팁 – 실전에서 유리한 기술적 디테일**
	
	- `feature flag system`을 구축하라. 새 기능을 바로 배포하지 말고, 내부 테스트 → 전체 적용 → A/B 테스팅까지 유연하게 조절 가능해야 한다. (LaunchDarkly / 자체 Redis 기반 플래그도 OK)
	- 배포 자동화 시 `post-deploy hook`에 알림(Slack/Discord) + 헬스체크 → 일정 시간 후 트래픽 모니터링이 포함된 파이프라인을 구성해두면 **장애를 눈치 못 채는 문제**가 줄어든다.
	- **비용 최적화**도 기술 역량이다. 예: Cloud Function을 줄이고 Spring + API Gateway + Lambda Proxy만으로도 유사 구조를 훨씬 저렴하게 운영 가능.
	  
  
- 과제
	- Http vs Https 공부하기
	- 로드밸런서 공부하기
	- 트러블 슈팅 시나리오 계속 진행하기
	- 이력서 수정 및 지원서 제출
	  
- 트러블슈팅 시나리오 진행사항
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
	- [데이터가 많을 때 조회하는 성능 개선](https://chatgpt.com/c/68145efc-2388-8012-95c3-63818e139064)
	
- 챌린지
	- 스프링프레임워크를 직접 구현하기
	- 공룡책 원본 완독
	- 백준 혹은 프로그래머스 코딩테스트
	- SQL 쿼리문 자유롭게 작성
	- Git 터미널을 통해 명령어 자유롭게 이동하기
	- 손코딩 연습하기
	- CS  공부하기
	- 다양한 기술 스텍을 적용하여 토이 프로젝트 만들기
	- ERD 작성하기
	- 리눅스 연습하기
	- 오픈소스로 프로젝트 작성
	- 새로운 기술 스텍 배우기
	- 내가 배운 지식 남들에게 설명하기
	- 옵시디언 문서 작성 및 정리
	  
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
	- 너무 중요한 LINK
		- [기술스택이 아쉬워도 신입이력서를 잘 쓰는 법](https://www.youtube.com/watch?v=iBE8trz9uHI)
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
	- [HTTPS 심화 강의 - 생활코딩](https://www.youtube.com/watch?v=0cfUVrQW_yg&list=PLCZ-8rvakaqbplQZAoUku8uuxUgbLQm-1)
	- [Spring Security JSON 형식으로 로그인 1](https://goalinnext.tistory.com/136)
	- [Spring Security JSON 형식으로 로그인 2](https://goalinnext.tistory.com/m/146)
	- [Spring Security JSON 형식으로 로그인 3](https://dsjo.tistory.com/4)
	- [개발자가 되는 방법 - 니콜라스](https://www.youtube.com/watch?v=c78j19OpfN0)
	- [HTTP VS HTTPS + SSL + TLS 이해하기 심화편](https://www.stevenjlee.net/2020/11/01/%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-http-vs-https-%EA%B7%B8%EB%A6%AC%EA%B3%A0-ssl-secure-socket-layer/)
	- [대용량 트래픽과 데이터 처리를 위해 공부할 내용](https://velog.io/@seultudy/%EB%8C%80%EC%9A%A9%EB%9F%89-%ED%8A%B8%EB%9E%98%ED%94%BD%EA%B3%BC-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%9C%84%ED%95%B4-%EA%B3%B5%EB%B6%80%ED%95%A0-%EB%82%B4%EC%9A%A9)
	- [대규모 데이터 처리](https://hotechstory.tistory.com/147)
	- [대용량 트래픽 처리하는 6가지 방법](https://jeounpar.tistory.com/29)
	- [우리팀은 카프가를 어떻게 사용하고 있을까 - 우테코](https://techblog.woowahan.com/17386/)
	- [대용량 트래픽을 처리하기 위한 카프카 사용법](https://www.elancer.co.kr/blog/detail/738)
	- [Jmeter playlists get 세팅 성공 사례](https://chatgpt.com/c/682aded9-0834-8012-acaf-5cd483ee8c0e)
	
- 키워드
	- Kubernetes 관리 플랫폼
		- 클러스터 구성, 워크로드 배포 등 쿠버네티스 구성 및 자동화 관리
	- MLOps 플랫폼 (Kubeflow) 구성, 관리 자동화 개발
	- Flask
	- Django
	- gRFC
	- RDBMS
	- NoSQL
---
---