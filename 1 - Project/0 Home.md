---
created: 2024-06-21
updated: 2024-09-20
tags:
  - bookmark
---

---
# Home

1. [Quick Notes](#quick-notes) - 메모장
2. [Today](#today) - 스케줄
3. [LINK](#link) - 링크
4. [PROMPT](#prompt) - 명령어
5. [Employment](#employment) - 취업
6. [Study List](#study-list) - 스터디
7. [Coding Test](#coding-test) - 코딩 테스트
8. [Learning LoadMap](#learning-loadmap) - 학습 로드맵
9. [Topics](#topics) - 의문점, 공부 주제, 한줄 설명
10. [Life](#life) - 일상
11. [Program Project](#program-project) - 프로젝트
12. [Development log](#development-log) - 개발일지
13. [Good Information](#good-information) - 좋은 정보
14. [Spec](#spec) - 스펙
15. [Annotation Study Method](#annotation-study-method) - 어노테이션 학습
16. [Trouble Shooting](####trouble-shooting) - 트러블 슈팅
17. [Analects](#analects) - 저명한 프로그래머들의 어록
18. [Notebook Archive](#notebook-archive) - 분류 문서

---
# Content







#### quick-notes

- 문제 해결 -> 수치화 -> 성능 측정
- [A급 코딩 유튜브 - 딩코딩코](https://www.youtube.com/@%EB%94%A9%EC%BD%94%EB%94%A9%EC%BD%94/videos)


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
#### today 

######  **Schedule***

|     | 월요일 | 화요일 | 수요일 | 목요일 | 금요일 | 토요일  | 일요일 |
| --- | --- | --- | --- | --- | --- | ---- | --- |
| 오전  |     |     |     |     |     | 프로젝트 | X   |
| 오후  |     |     |     |     |     | 블로그  | X   |

---
###### **Todo List**

| Todo List       | Challenge          | Lost Ark            |
| --------------- | ------------------ | ------------------- |
| 📑 옵시디언 노트 정리   | 💬 커뮤니티 댓글 CRUD 구현 | 🏆 주간 레이드           |
| 📂 포트폴리오 업데이트   | 🔄 리프레시 토큰 구현      | ⚔️ 카오스 던전           |
| 📝 입사 지원        | 🔐 쿠키 보안 문제 해결     | 🐉 가디언 토벌           |
| 🎯 코딩 테스트       | 🧦 양말 당근마켓         | 🎟️ 주간 에포나 (큐브)     |
| 🚀 프로젝트 진행      | 📱 스마트폰 바꾸기        | 🌲 생활 (벌목)          |
| ✍️ 기술 블로그 작성    | 💧 정수기 수리          | 🏭 아비도스 공장          |
| 💪 헬스           | 📚 정보처리기사 실기       | 🔥 카오스게이트 or 필드보스   |
| 📚 정보처리기사 실기 공부 | x☁️ AWS 강의, 이해     | 💰 싱글 주화 & 길드 혈석 상점 |

---
###### **정보처리기사 일정**

![[스크린샷 2025-03-18 142921.png]]

---
###### **프로젝트 일정**

- [x] controller 리팩토링 
- [x] service 리팩토링
- [x] refresh token 구현
- [x] security 리팩토링
- [ ] gpt 리팩토링

---
#### link  

- **💡A급 블로그**
	- [민동현](https://donghyeon.dev/)
	- [Inpa Dev](https://inpa.tistory.com/)
	- [나의 공부 저장소]( https://programforlife.tistory.com/)
	- [다민 블로그](https://www.jeong-min.com/52-gatsby-blog/)
	- [멘토 블로그](https://minkukjo.github.io/framework/2020/12/18/Spring-142/)
	- [개발자가 자주 보면 좋은 사이트](https://brunch.co.kr/@skykamja24/639)
	- [개발 실력을 위한 IT기업 기술 블로그 45곳 모음](https://brunch.co.kr/@sicle-official/35)
---
- **💡블로그**
	- Infa blog
		- [lamda 표현식](https://inpa.tistory.com/entry/%E2%98%95-Lambda-Expression)
		- [infa 프로세스 멀티 스레드](https://inpa.tistory.com/entry/%F0%9F%91%A9%E2%80%8D%F0%9F%92%BB-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4-%E2%9A%94%EF%B8%8F-%EC%93%B0%EB%A0%88%EB%93%9C-%EC%B0%A8%EC%9D%B4)
		- [infa TCP / UDP](https://inpa.tistory.com/entry/NW-%F0%9F%8C%90-%EC%95%84%EC%A7%81%EB%8F%84-%EB%AA%A8%ED%98%B8%ED%95%9C-TCP-UDP-%EA%B0%9C%EB%85%90-%E2%9D%93-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EC%9E%90)
	- 기술 면접 질문 모음
		- [운영체제 질문 1](https://velog.io/@min9288/%EB%B0%B1%EC%97%94%EB%93%9C-%EA%B0%9C%EB%B0%9C-%EB%A9%B4%EC%A0%91-%EC%A7%88%EB%AC%B8%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C)
	    - [면접 질문 모음](https://dev-coco.tistory.com/159)
	- 워니 개발자 이력서 관리법
		- [이력서 작성법](https://wonny.space/writing/work/engineer-resume)
		- [실제 합격 이력서](https://wonny-log.notion.site/Wonny-Public-c2f8051bfb574f349406a30d2bc71a45)
	- AWS 관련 에러 및 설정
	    - [AWS 502 에러 해결](https://choo.oopy.io/0563a1cd-17b0-4513-9e59-49f0bd89834b)
	    - [AWS Elastic Beanstalk 에러 해결](https://billtech.tistory.com/23?utm_source=chatgpt.com)
	    - [AWS Elastic Beanstalk 배포 참고](https://velog.io/@bbamjoong/AWS-Java-SpringBoot-Elastic-BeanStalk-%EB%B0%B0%ED%8F%AC-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-3%EC%9D%BC%EA%B0%84%EC%9D%98-%EC%82%BD%EC%A7%88)
	    - [AWS Auto Scaling 가이드](https://inpa.tistory.com/entry/AWS-%F0%9F%93%9A-EC2-%EC%98%A4%ED%86%A0-%EC%8A%A4%EC%BC%80%EC%9D%BC%EB%A7%81-ELB-%EB%A1%9C%EB%93%9C-%EB%B0%B8%EB%9F%B0%EC%84%9C-%EA%B0%9C%EB%85%90-%EA%B5%AC%EC%B6%95-%EC%84%B8%ED%8C%85-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC)
	- Git 가이드
	    - [Git Pull Request 사용법](https://wayhome25.github.io/git/2017/07/08/git-first-pull-request-story/)
	    - [Git ignore 설정 방법](https://pixx.tistory.com/384)
	- 데이터베이스 정규화 및 ERD
	    - [데이터베이스 정규화](https://mangkyu.tistory.com/110)
	    - [스타벅스 ERD 작성 요령](https://velog.io/@jcinsh/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%8A%A4%ED%83%80%EB%B2%85%EC%8A%A4-%EA%B3%BC%EC%A0%9C)
	- [카카오 뉴인턴에서 정규직 전환 실패에 대한 회고](https://zorba91.tistory.com/286)
	- [기록과 정리의 중요성](https://jojoldu.tistory.com/)
    - [Docker 가이드](https://special-seat-581.notion.site/Docker-f93316d8eb944ce98daa8312039ef72e)
    - [웹 서버의 기초 개념](https://velog.io/@josworks27/%EC%9B%B9-%EC%84%9C%EB%B2%84Server%EC%9D%98-%EA%B8%B0%EC%B4%88-%EA%B0%9C%EB%85%90)
	- [스프링부트 Autoconfiguration 원리 및 만들어보기](https://donghyeon.dev/spring/2020/08/01/%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8%EC%9D%98-AutoConfiguration%EC%9D%98-%EC%9B%90%EB%A6%AC-%EB%B0%8F-%EB%A7%8C%EB%93%A4%EC%96%B4-%EB%B3%B4%EA%B8%B0/)
	- [프로젝트 캐싱 적용하기](https://kerobero.tistory.com/35)
	- [효율적인 캐싱 전략과 구현 방법](https://f-lab.kr/insight/effective-caching-strategies-20240620)
	- [모노레포 멀티 모듈 프로젝트 만드는법](https://umbum.dev/1177/)
	- [MSA 팀프로젝트](https://techblog.lotteon.com/%EB%89%B4%EC%98%A8%EC%9D%B4%EB%93%A4%EC%9D%98-%EC%B2%AB-msa-%EC%84%9C%EB%B9%84%EC%8A%A4-%EB%8F%84%EC%A0%84%EA%B8%B0-d336186a7e31)
	- [webflux](https://gratis-bread-c6b.notion.site/WebFlux-144c300c8414803ca71dec614b966aa2)
	- [스터디 운영 방식 노하우](https://studywithowl.tistory.com/entry/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EC%8A%A4%ED%84%B0%EB%94%94-%EC%9A%B4%EC%98%81-%EB%B0%A9%EC%8B%9D-%ED%8C%81-feat-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EA%B3%B5%EB%B6%80-%EA%BF%80%ED%8C%81)

---
- **💡유튜브**
	- [cpu 알고리즘 스케줄링 1](https://www.youtube.com/watch?v=w1z6WCyMdhQ)
	- [cpu 알고리즘 스케줄링 2](https://www.youtube.com/watch?v=LgEY4ghpTJI)
	- [컴퓨터 구조와 cpu 작동 원리 - 제어장치 연산장치](https://www.youtube.com/watch?v=mJpwUPqpxhw)
	- [AWS 쉽게 배포하기](https://www.youtube.com/watch?v=cOUhREAWJNw)
    - [혼자 공부하는 운영체제 강의](https://www.youtube.com/watch?v=bls_GjX-4U8&list=PLVsNizTWUw7FCS83JhC1vflK8OcLRG0Hl)
    - 
---
- **💡리포지토리**
	- 좋은 Git Repository 사례
	    - [우아한테크캠프 프로젝트 사례](https://github.com/woowacourse-teams/2022-pickpick)
	    - [기술 스택 참고](https://github.com/midaslmg94/wing-project-msa)
	- 
---
- **💡공식 홈페이지**
	- [Java Reference와 GC](https://d2.naver.com/helloworld/329631)
	- 
---
- **💡ETC**
	- 노션 이전 데이터
		- [HTML](https://www.notion.so/HTML-38c0253a06da4d96aea187ddc0850f3d?pvs=21)
		- [JAVASCRIPT](https://www.notion.so/JAVASCRIPT-3e6c185a97f74ea79e58c0c01d57856e?pvs=21)
		- [CSS](https://www.notion.so/CSS-0acbf7864e83464a9e66f275437446e8?pvs=21)
		- [DB](https://www.notion.so/DB-36755b54970945ada1188b60ecdb7ccb?pvs=21)
		- [Spring](https://www.notion.so/Spring-ccd599184e0f45879d5734c5c1f249ce?pvs=21)
		- [정보처리기사](https://www.notion.so/e98cef12c3134e43b107451301ea41f0?pvs=21)
		- [HotelLobbyist](https://www.notion.so/HotelLobbyist-7914fa86b5874481a371bb64259ed889?pvs=21)
	- 
---
#### prompt  

##### **PowerShell**
###### VSCode powershell에서 관리자 모드로 변경해주는 명령어
- Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
---
##### **Git**
###### main과 develop과 커밋이 일치하지않을 경우 main에 develop을 덮어 버리기
```git
git fetch origin develop:develop 
git checkout main git merge -s ours develop --allow-unrelated-histories 
git checkout develop -- . 
git commit -m "[1.0.0] 1차 배포 진행" 
git push
```
---
##### **SQL**

	###### 테이블 데이터 지우기
- 테이블 참조가 되어서 외래 키 제약조건때문에 직접 지우기 불가능한 경우
- 일시적으로 외래키 제약 비활성화 후
- `실업무에는 위험` `테스트 DB에만 사용할 것`
  
```
SET FOREIGN_KEY_CHECKS = 0;

DELETE FROM users;

SET FOREIGN_KEY_CHECKS = 1;
```

---
##### **MarkDown**

- **기본 문법**
	`- **굵게**`
	`- *기울임*`
	`- 리스트`
	`- [ ]` `체크박스`
	- `# 제목`
	- `## 제목`
	- `### 제목`
	- `#### 제목`
	- `##### 제목`
	- `###### 제목`
	-  `---` `구분선`

- **Link**
	- 링크 기본 사용법
		- [[Stream]] 
		- 해당 링크로 이동하게 된다.
		- 해당 링크를 연결하면 그래프 뷰로 연결 리스트가 활성화된다.
		  
	- 링크는 유지하고 타이틀만 변경
		- [[Stream |링크 타이틀만 변경]] 
			- 글자 뒤에 | 를 추가하여 이름 변경해도 링크 위치는 유지된다.
			  
	- 해당 웹피이지로 이동하는 링크
		- [구글](https://google.com)
			- 웹페이지로 이동하는 링크 
			  
	- 로컬 이미지 삽입
		- 옵시디언 내에 이미지 드래그하고 놓기
		- ![[]] 내부에 링크 이미지 주소 입력
		- 이미지 관리를 위해 폴더 단위에 관리하기
		- 설정 - 파일 및 링크 - 새 첨부 파일을 만들 위치 - 아래에 지정된 폴더 - files 폴더 설정

- **명령어 팔레트 즐겨찾기**
	- ctrl + p = 커멘드 실행 즐겨찾기 추가하는 법
	- 설정 - 명령어 팔레트 -
 
- **이모티콘**
	- `:memo:` → 📝 (메모)
	- `:book:` → 📚 (책)
	- `:notebook:` → 📓 (노트북)
	- `:page_with_curl:` → 📃 (페이지)
	- `:writing_hand:` → ✍️ (글쓰기 손)
	- `:clipboard:` → 📋 (클립보드)
	- `:bookmark:` → 🔖 (책갈피)
	- `:spiral_notepad:` → 🗒️ (소형 노트)
	- `:pen:` → 🖊️ (펜)

- **테이블**
	
	| 헤더1 | 헤더2 | 헤더3 |
	|-------|-------|-------|
	| 내용1 | 내용2 | 내용3 |
	| 내용4 | 내용5 | 내용6 |

-  **콜아웃**
---
#####  **Obsidian PlugIn**
- 1. 코드 직접 실행 기능 (Execute Code)
	
	- 기본 사용법
		- 읽기 모드로 변경 후 Run
		- 에러가 날 경우 - 언어 별 Path 경로를 찾아야 한다.
		- 언어 별 Path 경로 설정 및 찾기
			- cmd which node - Javascript
			- cmd which python - Python
	- 주된 사용 목적
		- 나중에 사용하기 위한 코드
		- 이해를 돕기 위한 학습에 활용
		- 알고리즘 테스트 등
	
-  2. 코드 블록 스타일 (Code Styler)
	
	###### 코드 블록 - 라인 번호 표시
	코드 블록 - 하이라이트
	- 언어 뒤에 한칸 띄어쓰고  hl:4
	- hl:4
		- 4번째 줄 하이라이트
	- hl:2-5
		- 2번째에서 5번쨰 줄 하이라이트
	- print 
		- print까지 포함하여 하이라이트
	- 여러가지 색상 하이라이트 사용법
		- CodeStyler 설정
		- Choose Settings Page -> code block stylering 변경
		- Choose Codeblock Settings -> CodeBlockBody -> CodeBlockhighlighting 변경
		- add alternative Highlight -> add 버튼
	- error:5
		- 5번째줄에 추가로 만든 error 하이라이트
	``` java hl:4 error:5
	
	import java.util.ArrayList; // 필요한 클래스를 임포트
	
	public class MainClass {
		public static void main(String[] args) {
			// ArrayList 인스턴스 생성
			ArrayList<String> list = new ArrayList<>();
	
			// 리스트에 항목 추가
			list.add("Hello");
			list.add("World");
	
			// 리스트 항목 출력
			for (String item : list) {
				System.out.println(item);
			}
		}
	}
	
	
	
	```
	
	###### 코드 블록 - 제목, 링크 추가
	
	``` java title:"코드 블록 - 제목 추가하는 법"
	
	import java.util.ArrayList; // 필요한 클래스를 임포트
	
	public class MainClass {
		public static void main(String[] args) {
			// ArrayList 인스턴스 생성
			ArrayList<String> list = new ArrayList<>();
	
			// 리스트에 항목 추가
			list.add("Hello");
			list.add("World");
	
			// 리스트 항목 출력
			for (String item : list) {
				System.out.println(item);
			}
		}
	}
	
	
	```
	
	- 참고할 노트 입력
		- reference의 ref:[[]] 입력
		- 뒤에 title:"" 추가하면 제목은 title이 되지만 링크는 유지된다.
	``` java ref:[[1 CS 목록 - 0%]] title:"타이틀 설정하는 법"
	
	import java.util.ArrayList; // 필요한 클래스를 임포트
	
	public class MainClass {
		public static void main(String[] args) {
			// ArrayList 인스턴스 생성
			ArrayList<String> list = new ArrayList<>();
	
			// 리스트에 항목 추가
			list.add("Hello");
			list.add("World");
	
			// 리스트 항목 출력
			for (String item : list) {
				System.out.println(item);
			}
		}
	}
	
	
	
	```
	###### 코드 블록 - 아이콘, 태그 추가, 헤더 스타일 추가
	
	- **아이콘 포함 기능**
		- Choose Codeblock settings
			- Codeblock header 변경
			- Language Tag, Icon -> Always 변경
	``` python 
	
	import java.util.ArrayList; // 필요한 클래스를 임포트
	
	public class MainClass {
		public static void main(String[] args) {
			// ArrayList 인스턴스 생성
			ArrayList<String> list = new ArrayList<>();
	
			// 리스트에 항목 추가
			list.add("Hello");
			list.add("World");
	
			// 리스트 항목 출력
			for (String item : list) {
				System.out.println(item);
			}
		}
	}
	
	
	```
	
	- **인라인 코드 - 스타일링**
		- `console.log("hello world")`
		- 앞에 중괄호 추가하고 안에 언어
		- {js}
		- `{js}console.log("hello world")`
		- `{java}System.out.print("hello world");`
		
		- `{js icon title:" 인라인 블록 타이틀 추가 테스트"}console.log("hello world")`
	
	- **인라인 코드 - CSS 스니펫**
		- 
	
- 3. 소스 코드 파일 - VScode Editor 
	- VScode처럼 코드를 실행 및 편집할 수 있다.
	- Ctrl + P = 명령어창 열기
	- vscode 입력
	- create new code file
	- 새로운 제목 입력
	- 확장자 선택
	- create 선택
	
- 4. 불필요한 파일 정리 (File cleaner redux)
	
- 5. 노트별 뷰 모드 개별 설정 (Force note view mode)
	
- 6. 슬래시(/)로 명령어 입력 (Slash commander)
	
- 7. 태그 관리 플러그인 (Tag wrangler)
	
- 8. 리본, 탭바 등 아이콘 생성 (Commander)
	
- 9. 리본 원클릭 노트 열기 (Pinned note)
	
-  10. 웹페이지 스크랩 (Slurp)
	
- 11. 노트 마지막 커서 위치 기억 (Remember cursor position)
---
#### employment  
 
##### 1. 면접 방식

- **면접 진행:** 2대 16(면접관 2명, 지원자 16명)
  
- **면접관:** 인사담당자 (비개발자) + 퇴사 예정이자 인수인계자
  
- **진행 방식:** 시간 관계상 집단 면접으로 진행되었으나, 1인 개발이 가능하다고 밝힌 지원자에게만 질문하는 형태

##### 2. 회사 및 개발팀 현황

- 홈페이지 리뉴얼이 주 업무이며, DB를 제외한 전면 개편 예정
  
- 기존 시스템은 **스파게티 코드**, JSP 기반의 구식 기술 스택** 사용
  
- 개발팀은 1명(인수인계자)뿐이며, 근무 경력 7개월
  
- 인사담당자는 개발지식 대한 이해도가 부족하며, 인수인계자의 의견을 존중하지 않고 독단적으로 진행하는 모습

- 개발자가 단독으로 프로젝트를 맡게 될 가능성이 높아 보인다.

##### 3. 면접 분위기 및 문제점

1. 16명을 한 번에 면접하는 방식으로 진행되었으나, 개별 질문 없이 1인 개발 가능 지원자만 질문하는 비효율적인 구조

2. 입사가 목적이 아닌 면접 경험을 늘리기 위한 목적이기 때문에 1인 개발 가능하다고 손을 들었다.
  
3. 인수인계자는 기술 질문을 담당, 인사담당자는 불필요한 개입 및 관여
  
4. 면접 도중 인사담당자가 “아직도 다 못 끝냈냐 왜 이렇게 오래 걸리냐” 며 짜증을 내며 공통 질문만 하라고 하는 등 비전문적인 태도를 보임 

5. 결국 1시간도 안되서 내 차례가 오기도전에 인사담당자가 너무 오래걸린다고 면접을 독단적으로 종료.

6. 면접을 16명을 한꺼번에 면접을 진행하기로 정했으면서 1인 개발 가능한 사람만 질문하라는둥 대놓고 지원자들 무시하는 태도가 좋지 못하였다. 또한 1시간도 안지났는데 짜증을 내며 면접을 종료한 것에 대해 매우 어처구니가 없었다.
  
- 회사가 연봉을 합격자와 협상 후 결정하는 방식이라 연봉에 대한 정보 부족
	- 다만, 신입 1인이서 모든 개발을 맡기며, 개발자에 대한 지식 부족과 배려심이 심각하게 부족한 독단적인 태도로 보아 향후 입사하더라도 비합리적인 지시와 무리한 요구가 빚발치고 책임을 오로지 내가 받을 것으로 추측된다. 또한 홈페이지 리뉴얼을 혼자에게만 맡기는걸로 보아 최대한 인건비를 싸게 먹으려는 태도가 노골적으로 드러난다. 결론적으로 3000천이하 연봉을 줄 것으로 추측

##### 4. 지원자들의 반응 및 수준

- 지원자들의 역량이 제각각으로
- 질문의 취지에 안맞는 엉뚱한 답변을 한 지원자
- CS 지식이 많이 부족하여 아무것도 대답을 못한 지원자
- 질문에 대한 답변을 생각하는데 천장을 바라보며 눈을 위로 뒤집으며 생각하고 어..음..하는 지원자
- 가장 기억에 남는 지원자는 3명 정도이다.
	  
- 게임업계 출신자
	1. "여긴 게임 개발이 아닌 웹 개발인데 웹 개발자들 사이에서 본인의 강점은 무엇인가?" 질문이 왔다.
	2. 자기는 다른 웹개발자들과 똑같이 잘할 자신있다고 주장하였지만 그에 대한 근거를 제시 하지 못했다.
	3. 본인은 Java와 html(..?)을 조금 다루었기 때문에 얼마든지 잘할 자신있다는 뇌절을 하였다.
	4. 면접관은 신뢰를 하지 못한 반응 보였고 그렇다면 객체지향 프로그래밍 4가지 원칙에 대해 설명해달라 질문을 하였다.
	5. 자신있게 대답할 수 있다고 하였지만, 내용에 대해 전혀 모르고 있었고 잘못된 내용을 당연히 맞는 것처럼 이야기하며 어버버하다가 끝났다.
	   
- 리뉴얼되는 홈페이지에 고객들의 정보가 있는 기존 DB 삭제 가능 여부를 묻는 지원자
	- 면접관은 가장 격양된 목소리로 고객의 정보가 있는데 그걸 지우면 어떡하냐고 황당하며 대답하였다.
	
- 가장 면접을 잘 본 것 같은 지원자
	- 질문에 대한 답변을 면접관이 만족스럽게 생각하진 않았지만 나름 자신감있게 설명하였다.
	- 모르는 질문에 대해 즉각적으로 "모르겠습니다."라고 함.
	- 면접관이 "그게 다인가요? 라는 답변에" 당황하지 않고 이어서 추가로 더 정보를 이야기함.
	  
- 인수인계자는 답변에 대한 부정적인한 반응과 긍정적인 반응을 숨기지 않고 드러내었다.

##### 5. 기술 면접 질문

- DFS와 BFS의 차이 설명
- REST API 개념 및 GET, POST, PUT, DELETE 차이
- URL 입력 시 내부적으로 처리되는 과정 설명
- CORS 에러 해결 방법
- 정규화 개념

- SQL Injection 개념
- 기본키, 외래키, 후보키의 차이
- 기본키를 username으로 하면 안 되는 이유
- 객체지향 4가지 원칙
- Java에서 본인의 강점
- 본인이 맡았던 프로젝트 소개 및 역할
- 개발지식이 없는 일반인에게 개념을 설명하는 방식 요구

##### 6. 종합 평가

- 비효율적인 면접 방식
	- 다수의 지원자를 한 번에 모아두고 일부 지원자만 질문하는 형식으로 진행되어 면접의 실효성이 떨어짐
	  
- 인사담당자의 비전문적인 태도
	- 개발 관련 이해도가 부족하면서도 면접 진행 방식에 개입하여 부정적인 분위기를 조성
	  
- 기술 스택 및 환경이 낙후됨
	- JSP 기반의 스파게티 코드 유지보수 및 전면 개편이 필요함
	- 개발자에 대우가 매우 처참할 것으로 예측됨
	  
- 인수인계자의 태도
	- 기존 팀원이지만 면접 과정에서 충분한 발언권을 가지지 못했으며, 회사의 의사결정이 본인의 의견을 반영하지 않는 듯한 분위기
	  
- 연봉 미공개
	- 합격 후 협상 방식으로, 지원자 입장에서 불확실성이 큼
	- 또한 인사담당자의 태도로 보아 3000 이하로 예상된다.


##### 이력서 & 채용 정보 리스트

- Resume
	- https://www.notion.so/Atoo-153b93b7d02480d28e9bdd2a48748527
- Job description
	- https://www.notion.so/153b93b7d0248071bf69fa82a40533b0

##### Study

- 내가 코드를 작성할 때 이해하면서 배우려면?
	- 주석 공부법를 해야한다.
- 
##### List

- CI 툴(Jenkins, Github Actions 등)을 통한 파이프라인 구축/운영 경험이 있는 분을 찾아요.
	-  github action?
	- jenkins
- 개발자 직군 종류
	- https://www.youtube.com/watch?v=qMu05OFnhrI

##### my company

- 1순위 : 성장가능성
- 2순위 : 대기업
- 3순위 : 연봉
- 4순위 : 출퇴근 거리 및 , 원격근무 유무

- 코딩 테스트 필수
	- 코딩 테스트 수상 경력?
		- 내가 가능할까?
- 유니콘 기업, 괜찮은 스타트업
	- 철저한 능력주의
	- 역시 코딩 테스트 필수
- 좋은 회사 고르는 법 
	1. 기준의 높아야 한다. (코딩 테스트가 무조건 있는 회사를 가는게 좋다.)
	2. 분야가 명확하게 나뉘는 회사를 가는게 좋다. (구체적으로 뽑는 회사)
	3. 규모가 어느정도 있어야 한다. (스타트업이지만 개발팀이 2명이다? X)
- 이직 주기 1~ 2 년
	- 보통은 10% 연봉이 오르고 많게는 30% 올리는 경우도 있다.
	- 1년을 어떻게 보냈는지가 아주 중요하다.

- 성장가능성 
	- 스타트업
		- https://www.youtube.com/watch?v=3U-syPE9yTQ
		- 필살기를 만들기 위해 가는 곳
	- 좋은 스타트업을 선택하는 기준
		- 성장성
			- 1일 1지원을 하라 -> 합격을 해보는 것을 경험하라
			- 매출 , 수익 -> 추세가 우상향 그래프 -> 무조건 지원해라
			- 적자가 발생해도 .. -> 매출을 계속 늘고있어야 한다.
			- 중요한 건 개선이 되고 있어야한다.
			- 스타트업인데 매출이 늘지 않고 있다? -> 스타트업이 아닐 확률이 크다.
			- 즉, 매출 증가는 필수 조건, 수익까지 증가한다면 무조건 좋은 기업이다 ! 
				- 무조건 지원하라
		- 리더십
			- CEO의 철학과 일하는 방식이 매우 중요하다.
			- 어떤 관점, 철학 , 목표로 창업을 하였는가?
			- 외부에 이러한 정보가 노출되면 정독하고 없다면, 면접에 물어보자
		- 기술력
			- 취업은? -> 체인지업이다.
		- 셋 중 하나라도 있다?
			- 가능성이 있는 회사이다.
			- 무조건 지원하라.
			- 지원을 일단하고, 면접 기회가 있으면 면접 연습하러도 간다.
			- 그러고나서 최종 합격하면 이 회사 후기도 보고, 이 회사 갈지 말지 그 때 판단하면 된다.
			- 우리는 많은 경험을 쌓고 많은 면접을 봐보는 것이 훨씬 중요하다.
		- 스타트업 입사 후 꼭 해야 하는 것
			- 필살기 만들기
				- 유사경험
				- 성공경험
				- 인사이트
					- KPI 조사 -> KPI 작성
					- 기록(고객)과 피드백
					- 수치화
						- 회사에서 일할 때 3C와 4P를 절대 잊지마라
	
	- 내년 상반기 : 대기업 (네카라쿠배) 대기업 + 스타트업 지원하라
	- 스타트업의 성장가능성을 찾아보자
		- THEVC : https://thevc.kr/
		- 시리얼 A 이상은 당분간 망할 걱정은 없다.
	- 스타트업의 매출 정보를 찾아보자
		- 크레딧잡, 잡플래닛, 사람인 기업 정보 확인
		- 매출 정보가 파악하기 어려울 경우 주요 서비스의 DAU
		- 즉 하루 접속자 수가 얼마인지 면접에서 물어보아야 한다.
		- DAU가 5만 이상이면 회사가 원할하게 굴러간다고 생각하면 된다.
	- 회사 분위기를 보고 회사를 파악할 수 있다.
		- 잡플래닛, 블라인드 눈팅
			- 재직 후기로 회사의 분위기 파악해보자
			- 5점 리뷰는 인사팀의 주작
			- 3점 이하 구시렁대는 악담에 이 회사의 핵심이 다 들어가 있다.
			- 블라인드에 회사 뒷소문이 있나 확인
	- 회사가 다루는 기술 스택을 기준으로 회사 파악
		- 인기 없는 언어 : PHP, RUBY, 단넷
		- 인기 있는 언어 : JAVA, JS, 파이썬
		- 수요가 많은 언어를 선택해야 한다.
		- 면접 과정에서 회사가 어떤 언어와 스택으로 서비스를 운영하는지 질문해서 파악해야 한다.
		- 미래에 무엇으로 바꿀 것이다 라는 답변은 걸러라 현재 무슨 언어를 사용하는지를 알아야하는게 관건
	- 미래 직속 상사가 나와 같은 분야의 개발자인지 확인
		- 들어갈 팀에 내 직무와 같은 개발자가 몇 명인지 확인
		- 연차분포는 어떻게 되는지 확인
		- 면접 마지막에 물어보며 확인할 수 있다.
		- 본격 채용중이라 계속 사람을 늘려간다고 말할 것이다.
		- 하지만 사람이 들어오는 만큼 나가는 사람이 더 많다는 걸 간과하면 안된다.
		- 즉, 현재 재직하는 숫자 그대로 받아들이면된다.
		- 내 직속 상사가 나와 기술분야가 다를 경우 기술적 지도를 받기 어렵다.
		- 신입은 의사소통 능력이 부족, 상사가 내가 하는 파트를 모를 경우 그 마저 불가능
	- 좋은 회사의 복지 종류
		- 개발 도서를 무제한으로 제공
		- 컨퍼런스를 지원, 컨퍼런스 발표 누가 많이 나오느냐
		- 개발자의 성잡을 돕고있는 여러가지 제도
		- AWS 계정을 마음껏 사용할 수 있는 복지
	- 기술 블로그를 얼마나 활성화 시켰느냐에 따라 회사의 가치를 판단
		- 기술 블로그가 활성화가 적다면?
			- 회사가 너무 바빠서 기술 블로그 쓸 사람이 없거나
			- 회사에서 기술 블로그에 크게 중점을 두지 않는다.
		- 바쁨에도 불구하고 꾸준히 기술 블로그 하는 회사는 회새의 브랜딩이나 개발 문화를 어필할 수 있는 메리트를 생각하는 회사이다.
		- 잘쓰는 한명이 쓰는 것보다 , 실력 상관없이 여러명이 쓰는 회사가 좋다.
		  
	- 협업 도구에 대해 관심도가 얼마나 높느냐도 좋은 어필 포인트가 된다.
		- slack을 안쓰는 회사..? 
		- 3명 이하는 이해할 수 있지만 개발팀이 5명 이상이면 sleck정도는 필수로 써야한다고 생각된다.
		- Gmail , Naver 메일 등을 개인 계정을 사용하느냐, 회사 계정을 사용하느냐에 따라도 네거티브 유무를 가를 수 있다.
	- CTO의 존재여부
		- 작은 회사면 없을 수도 있다.
	- 내가 팔로우하고 있는 좋은 시니어 엔지니어들이 그 회사로 몰리고 있느냐?
		- 시니어가 이 회사로 몰리는 이유가 무엇일까? 라고 고민해봐야 한다.
	- 내가 같이 일해보고 싶다고 생각되는 시니어 개발자들을 다 팔로우 하고 그 사람의 현재 직장이 바뀌면 그 회사들을 중점으로 보면 좋을 것이다.
	- 예시로 스프링은 모두 훌륭한 시니어 엔지니어들이 모인 회사이다.
	  이 회사의 모든 엔지니어들을 팔로우하고 그 엔지니어들의 각각의 이직하면
	  그 회사들을 이직 리스트로 만들고 따라서 지원해보는게 좋은 방법이라고 생각할 수 있다.
	- A 시니어 개발자 (우테코) -> OOO 회사로 이직 -> THEVC로 그 회사를 검색 -> 어떤 회사인지, 재무적인 부분도 판단할 수 있다.
##### GPT
- mycompany의 내용들을 토대로 솔루션을 제공해줘
- cs, 코딩 테스트, 채용회사 서칭, 포트폴리오 프로젝트 코딩, 노트 정리를 하루에 9시간안에 다 해야 한다면? 적절하게 시간을 배분해줘
- 성장가능성이 높은 기업이란 구체적으로 내가 남들에게 자신있게 설명할 수 있도록 알려줘
- 아주 못하는 초짜도 코딩 테스트를 준비하는 방법
- cs 공부 순서
- SI VS 비IT VS IT VS 서비스 기업이란?


##### IT 대기업이 요구하는 인재

- 참고 영상 - https://www.youtube.com/watch?v=OhSlSl_C2OM
  
- 프로젝트를 잘하는 사람
- 알고리즘을 잘하는 사람
- CS 지식이 탄탄한 사람
- 오픈 소스 컨트리뷰터

- 이 4가지 영역 중 하나를 잘하는 사람을 뽑아주지않을까?

- 프로젝트
	- 지원자격, 우대사항에 적혀있는 기술 스택을 공부하고 보유하여라
	- 기술 스택은 어느정도 깊게, 모든 기술들을 다 깊게 공부할 순 없다.
	- 자신이 강점으로 내새울만한 기술은 더욱 깊게
	- Docs + 강의 + 책
	- 정리
		- `지원자격 + 우대사항 기술 base + 깊게`
- 알고리즘
	- 필수적인 개념학습 (중요 :: 아래의 내용을 순차적으로 공부 !!)
		- 누적합
		- 구현
		- 그래프 이론
		- DFS
		- BFS
		- 트리순회
		- 완탐
		- 백트래킹
		- 비트마스킹
		- 그리디
		- 라인스위핑
		- 투포인터
		- LIS
		- 이분탐색
		- DP
		- 최단거리
		- 펜윅트리
	- 문제 풀기 : 플레티넘 수준까지
		- 최소 다합쳐서 160문제는 풀어야함
		- 정리
			- `강의 : 인프런 - 10주완성 C++ 코딩 테스트`
			- 백준 플레이상 또는 프로그레밍 레벨 5
- CS
	- 인프런 - CS지식의 정석 / KMOOC 강의
	- 면접 인터뷰 구글링 위주
- 오픈 소스
	- 6개월 동안 하루 2시간씩
	- 이슈 분석, 코어 분석, 댓글, 지속된 PR
	- GitHubstar 1만 이상의 오픈소스를 목표로
	- 목표 오픈소스 주변의 오픈소스부터
	- 스프링, vue.js 컨트리뷰터가 되는 걸 목표로 하라

---

#### coding-test  

---
#### learning-loadmap

- [[6 - CS/4 wait/Data Structure]]
- [[Algorithem]]
- [[Operating System]]
- [[Network]]
- [[1 - Project/4 plan/1 list/Design Pattern|Design Pattern]]
- [[DataBase|DataBase]]
---
- **그림으로 보는 자료구조 알고리즘 목차**
	- **1장 데이터 구조**
	    - 1-1 데이터 구조란?
	    - 1-2 배열
	    - 1-3 연결 리스트
	    - 1-4 스택
	    - 1-5 큐
	    - 1-6 해시 테이블
	    - 1-7 트리
	    - 1-8 이진 탐색 트리
	- **2장 정렬**
	    - 2-1 정렬이란?
	    - 2-2 버블 정렬
	    - 2-3 선택 정렬
	    - 2-4 삽입 정렬
	    - 2-5 합병 정렬
	    - 2-6 퀵 정렬
	    - 2-7 힙 정렬
	- **3장 검색**
	    - 3-1 이진 검색
	    - 3-2 해시 검색
	    - 3-3 트리 검색
	    - 3-4 순차 검색
	- **4장 그래프**
	    - 4-1 그래프의 정의
	    - 4-2 그래프의 표현 방법
	    - 4-3 그래프 탐색 (DFS, BFS)
	    - 4-4 최단 경로 알고리즘 (다익스트라, 벨만-포드)
	- **5장 문자열 처리**
	    - 5-1 문자열 매칭
	    - 5-2 KMP 알고리즘
	    - 5-3 보이어-무어 알고리즘
	    - 5-4 트라이
	- **6장 동적 프로그래밍**
	    - 6-1 동적 프로그래밍의 개념
	    - 6-2 피보나치 수열
	    - 6-3 최장 공통 부분 수열
	    - 6-4 배낭 문제
	- **7장 알고리즘 분석**
	    - 7-1 알고리즘의 시간 복잡도
	    - 7-2 알고리즘의 공간 복잡도
	    - 7-3 빅오 표기법
	    - 7-4 알고리즘 최적화
	- **8장 문제 해결**
	    - 8-1 유클리드 호제법
	    - 8-2 소수 판별법
	    - 8-3 문자열 매칭
	    - 8-4 큐스-모리스-프렛 알고리즘
	    - 8-5 페이지랭크
	    - 8-6 하노이의 탑
---
- **CS 로드맵**
	- **[[6 - CS/4 wait/Data Structure]]**
		- [[6 - CS/4 wait/Stack]]
		- [[6 - CS/4 wait/Queue]]
		- [[6 - CS/4 wait/Linked List]]
		- [[Array]]
		- [[6 - CS/4 wait/Tree]]
		- [[6 - CS/4 wait/Heap]]
		- [[Graph]]
		- [[6 - CS/4 wait/Hash Table]]
		- [[1 - Main/1 CS/Array|Array]]
	- [[Operating System]]
		- [[1 - Project/4 plan/2 Study/CPU]] 
		- [[CPU Architecture]] 
		- [[CPU Scheduling Algorithms]] 
		- [[FCFS]] 
		- [[SJF]] 
		- [[Round Robin]] 
		- [[SRF]] 
		- [[Multilevel Queue]] 
		- [[Process]] 
		- [[Process Structure and States]] 
		- [[Thread]] 
		- [[Virtual Memory System]] 
		- [[Memory Allocation Methods]] 
		- [[Paging]] 
		- [[Segmentation]] 
		- [[Page Replacement Algorithms]] 
		- [[FIFO]] 
		- [[LRU]]
	- **[[Algorithem]]**
		- [[big-O]]
		- [[Sorting Algorithms]] 
		- [[6 - CS/4 wait/Bubble Sort]] 
		- [[6 - CS/4 wait/Selection Sort]] 
		- [[6 - CS/4 wait/Insertion Sort]] 
		- [[6 - CS/4 wait/Heap Sort]] 
		- [[6 - CS/4 wait/Merge Sort]] 
		- [[6 - CS/4 wait/Quick Sort]] 
		- [[Search Algorithms]] 
		- [[Breadth-First Search (BFS)]]
		- [[Depth-First Search (DFS)]] 
		- [[Dijkstra's Algorithm]]
	- [[1 - Project/4 plan/1 list/Design Pattern|Design Pattern]]
		- [[Creational Patterns]]
			1. [[SingleTon]]
			2. [[Factory Method]]
			3. [[Abstract Factory]]
			4. [[Builder]]
			5. [[Prototype]]
		- [[Structural Patterns]]
			1. [[Adapter]]
			2. [[Bridge]]
			3. [[Composite]]
			4. [[Decorator]]
			5. [[Facade]]
			6. [[Flyweight]]
			7. [[Proxy]]
		- [[Behavioral Patterns]]
			1. [[Chain of Responsibility]]
			2. [[Command]]
			3. [[Interpreter]]
			4. [[Iterator]]
			5. [[Mediator]]
			6. [[Memento]]
			7. [[Observer]]
			8. [[State]]
			9. [[Strategy]]
			10. [[Template Method]]
			11. [[Visitor]]
		- [[Concurrency Patterns]]
			1. [[Thread Pool]]
			2. [[Active Object]]
			3. [[Monitor Object]]
			4. [[Scheduler]]
			5. [[Lock]]
		-  [[Architectural Patterns]]
			1. [[MVC]]
			2. [[MVVM]]
			3. [[MVP]]
			4. [[Layered Architecture]]
			5. [[Microservices Architecture]]
			6. [[Event-Driven Architecture]]
			7. [[Client-Server Architecture]]
			8. [[Hexagonal Architecture (Ports and Adapters]]
			9. [[CQRS (Command Query Responsibility Segregation)]]
			10. [[Event Sourcing]]
		- [[OOP]]
		- [[FP]]
	- [[Network]]
		- [[TCP/IP Model (4 Layers)]] 
		- [[OSI Model (7 Layers)]] 
		- [[Network Topologies]] 
		- [[Bus Topology]] 
		- [[Star Topology]] 
		- [[Ring Topology]] 
		- [[Mesh Topology]]
		- [[Hybrid Topology]] 
		- [[Packet Switching Methods]] 
		- [[Datagram Packet Switching]] 
		- [[Virtual Circuit Packet Switching]] 
		- [[Encapsulation]] 
		- [[Subnetting]] 
		- [[How Browsers Work]] 
		- [[DNS Servers]] 
		- [[Load Balancers]]
	- [[DataBase]]
		- [[Database Models]]
		  - [[Relational Model]]
		  - [[NoSQL Models]]
		    - [[Key-Value Stores]]
		    - [[Document Stores]]
		    - [[Column-Family Stores]]
		    - [[Graph Databases]]
		- [[Database Management Systems (DBMS)]]
		  - [[SQL-Based DBMS]]
		  - [[NoSQL DBMS]]
		  - [[NewSQL DBMS]]
		- [[SQL (Structured Query Language)]]
		  - [[DDL (Data Definition Language)]]
		  - [[DML (Data Manipulation Language)]]
		  - [[DCL (Data Control Language)]]
		  - [[TCL (Transaction Control Language)]]
		- [[Normalization]]
		  - [[First Normal Form (1NF)]]
		  - [[Second Normal Form (2NF)]]
		  - [[Third Normal Form (3NF)]]
		  - [[Boyce-Codd Normal Form (BCNF)]]
		- [[Indexes]]
		  - [[Clustered Index]]
---
-  **5대 CS**
	-  1. **알고리즘 및 자료구조**
		- **공부 순서:**
		    1. **기본 자료구조**: 배열, 연결 리스트, 스택, 큐, 해시 테이블
		    2. **트리와 그래프**: 이진 트리, 이진 탐색 트리(BST), 힙, 그래프 이론(DFS, BFS)
		    3. **정렬 및 탐색 알고리즘**: 버블 정렬, 선택 정렬, 병합 정렬, 퀵 정렬, 이진 탐색
		    4. **고급 알고리즘**: 동적 프로그래밍(DP), 그리디 알고리즘, 분할 정복
		    5. **복잡도 이론**: 시간 복잡도, 공간 복잡도, 빅오 표기법
	-  2. **컴퓨터 아키텍처**
		- **공부 순서:**
		    1. **기본 개념**: CPU 구조, 메모리 계층구조, 캐시 메모리
		    2. **명령어 집합 구조**: RISC, CISC
		    3. **병렬 컴퓨팅**: 멀티코어 프로세서, 스레드
		    4. **메모리 관리**: 가상 메모리, 페이징, 세그멘테이션
		    5. **입출력 시스템**: 장치 제어, 버스 구조, 인터럽트
	- 3. **운영체제(OS)**
		- **공부 순서:**
		    1. **운영체제 기본 원리**: 프로세스, 스레드, 다중 프로그래밍
		    2. **프로세스 관리**: 스케줄링, 컨텍스트 스위칭, 동기화(세마포어, 뮤텍스)
		    3. **메모리 관리**: 페이징, 세그멘테이션, 가상 메모리
		    4. **파일 시스템**: 디스크 관리, 파일 시스템 구조
		    5. **네트워크 및 보안**: 소켓 프로그래밍, 암호화, 사용자 인증
	- 4. **네트워크**
		- **공부 순서:**
		    1. **OSI 7 계층 모델**: 물리, 데이터 링크, 네트워크, 전송, 세션, 표현, 응용 계층
		    2. **TCP/IP 모델**: IP, TCP, UDP, ICMP
		    3. **라우팅 및 전송**: 라우팅 프로토콜, IP 주소 체계, 서브넷팅
		    4. **보안 프로토콜**: SSL/TLS, HTTPS, VPN
		    5. **네트워크 기초**: LAN, WAN, VLAN, DHCP, DNS
	- 5. **데이터베이스(DB)**
		- **공부 순서:**
		    1. **데이터베이스 기본 개념**: 데이터 모델링, ERD, 관계형 데이터베이스
		    2. **SQL**: 기본 쿼리, 조인, 서브쿼리, 트랜잭션
		    3. **데이터베이스 설계**: 정규화, 무결성 제약 조건, 인덱스
		    4. **트랜잭션 관리**: ACID, 트랜잭션 격리 수준, 잠금(Locking)
		    5. **분산 데이터베이스**: 분산 트랜잭션, NoSQL, 데이터베이스 샤딩
---
-  1. 알고리즘 및 자료구조
	-  1.1 기본 자료구조
		- [[Array]]
		- [[1 - Main/1 CS/Linked List]]
		- [[6 - CS/4 wait/Stack]]
		- [[6 - CS/4 wait/Queue]]
		- [[6 - CS/4 wait/Hash Table]]
	- 1.2 트리와 그래프
	- 1.3 정렬 및 탐색 알고리즘
	- 1.4 고급 알고리즘
	- 1.5 복잡도 이론
---
-  JAVASCRIPT
	-  1단계: **기초 개념 다지기**
		1. **JavaScript 기본 문법**
		    
		    - 변수 선언 (`var`, `let`, `const`)
		    - 데이터 타입 (문자열, 숫자, 배열, 객체 등)
		    - 연산자 (산술, 비교, 논리 등)
		    - 조건문 (`if`, `else`, `switch`)
		    - 반복문 (`for`, `while`, `forEach` 등)
		2. **함수**
		    
		    - 함수 선언 및 호출
		    - 매개변수와 반환값
		    - 화살표 함수 (`=>`)
		    - 콜백 함수의 이해
		3. **DOM 조작**
		    
		    - DOM(Document Object Model)이란?
		    - `document.querySelector`, `getElementById` 등 DOM 요소 선택
		    - DOM 요소 추가/수정/삭제
		    - 이벤트 처리 (`addEventListener`)
	-  2단계: **심화 학습**
		1. **ES6+ 문법**
		    
		    - 템플릿 리터럴
		    - 디스트럭처링 (구조 분해 할당)
		    - 모듈화 (`import`, `export`)
		    - 프로미스 (`Promise`, `async/await`)
		2. **객체와 배열 다루기**
		    
		    - 객체와 배열의 메서드 (`map`, `filter`, `reduce` 등)
		    - 깊은 복사와 얕은 복사
		    - 객체의 속성과 프로토타입
		3. **비동기 프로그래밍**
		    
		    - `setTimeout`과 `setInterval`
		    - AJAX와 Fetch API
		    - 비동기 처리의 원리 (Event Loop, Callback Queue)
	-  3단계: **프로젝트 경험**
		1. **작은 프로젝트**
		    
		    - 간단한 계산기
		    - Todo 리스트
		    - 날씨 정보 가져오기 (OpenWeather API 활용)
		2. **웹 브라우저 API 활용**
		    
		    - 로컬 스토리지와 세션 스토리지
		    - Canvas API를 사용한 간단한 그래픽 작업
	-  4단계: **프레임워크와 라이브러리**
		1. **React.js**
		    
		    - 컴포넌트 기반 설계
		    - 상태 관리 (State, Props, Context API)
		    - React Router로 SPA 구현
		2. **Node.js와 Express.js**
		    
		    - 서버 구축 기본
		    - RESTful API 설계
		    - 데이터베이스 연동 (MongoDB, MySQL 등)
	-  5단계: **고급 주제**
		1. **테스트**
		    
		    - 단위 테스트와 통합 테스트
		    - Jest, Mocha 같은 도구 사용
		2. **성능 최적화**
		    
		    - 코드 최적화 기법
		    - 렌더링 최적화
		    - Webpack, Babel 등의 도구 활용
		3. **타입스크립트**
		    
		    - 자바스크립트에 정적 타입 추가
		    - 타입 안전성 확보
	-  6단계: **심화 프로젝트**
		1. **완성도 있는 프로젝트**
		    
		    - 풀스택 애플리케이션 개발
		    - 배포 (Netlify, Vercel, Heroku 등)
		    - GitHub Actions로 CI/CD 구성
		2. **오픈소스 기여**
		    
		    - GitHub에서 작은 프로젝트 기여
		    - 코드 리뷰와 협업 경험 쌓기
---

---
#### topics

- **topic to study**
	- 키-값 쌍 구조가 빠른 이유 VS 계층적 구조가 데이터를 해석하는 과정이 무겁고 속도가 느린 이유
	- SOAP은 엄격한 스펙을 따라야 하며, WSDL(Web Services Description Language)을 사용하여 서비스 구조를 정의하는 것에 대하여
	- SOAP의 Stateful(상태 저장) 방식이 확장성과 성능 저하를 초래하는 이유
	- 자바에서 ;의 의미가 무엇이고 내부 동작이 어떻게 되는지?
	- @CrossOrigin 내부 동작
	- 
	abuse 방지
	SaaS 서비스
	클럭
	메모리 버퍼레지스터
	메모리 어드레스 레지스터
	cpu 스케줄링
	가장 공정한 cpu 스케줄링
	프로세스 우선순위
	스케줄링 큐
	준비 큐 
	대기 큐
	프로세스 상태 다이어그램
	선점형 비선점형 스케줄링
	cpu 스케줄링 알고리즘
	선입 선처리 스케줄링
	최단 작업 우선 스케줄링 
	라운드 로빈 스케줄링 
	최소 잔여 시간 우선 스케줄링 
	우선순위 스케줄링 
	다단계 큐 스케줄링 
	다단계 피드백 큐 스케줄링
	해시테이블 VS 해시맵
	- 어레이리스트란 어떻게 구조되어있는가
	- 연결 리스트와 어레이리스트의 차이
	- 해시충돌이 많을 때 충돌이 무엇인지, 해결 방법
	- MSA gateway webflux
	- db가 아닌 
	- 유튜브에서 바로 끌고오는 방식
	- 사용자 재생목록에 비디오, 좋아요 등등 만 DB에 저장하는 방식
	- Big O 정의 
	- N을 앞지른다.
	- little o 
	- 코테준비는 파이썬으로 (훨씬 쉽다.)
	- 대용량 데이터 트래픽 
	- 실제 사용자를 받는다.
	- 뭐라도 다른걸 한다.
	- redis 분산락 
		- redis , MSA, kafka
	- 유저 수를 고려하고 
	- 테스트 툴
		- jmeter
		- 프로메테우스
		- 스카우터
- **simple word**
	- ERP 
		- 기업 자원 계획 | Enterprise Resource Planning
		- 기업의 다양한 업무 (재무, 인사, 생산 등)를 하나의 통합 시스템으로 관리하여 효율성을 높이는 소프트웨어이다.
	- Private Cloud 관리 플랫폼
		- 회사 내부에서 사용하는 클라우드 서버
	- OpenStack API 및 SDK을 활용한 가상 서버 생성 및 자동화 관리
		- 사용자가 버튼을 눌러서 실행하는 것이 아닌 자동으로 생성 및 관리를 하는 것을 의미
---
#### life

- [[다경이]]
- [[골드 거래 사기 대처법]]
- [[My Profile]]
---
#### program-project

---
#### development-log  

- **느낀점**
	-  **기록은 나의 정신을 맑게 해준다. **
		- 집중력이 흐트러졌을 때는 배울 항목의 지식을 기록하며 정신을 가다듬자.
		
	- **졸리면 차라리 한숨 자라**
		- 컨디션이 안좋은 상태에서 해봤자 힘들다. 그냥 한숨자고 일어나서 마저하자.

---
- **의문점**
	- 왜 스프링 버전과 자바 버전에 따라 호환이 되고 안되는 것인가?
		
	- 옵시디언의 효율적인 문서 연결 방식을 알고 싶다.
---
-  **예열**
	- 일단 예제에 따라 쳐라
		  
	- 한줄한줄 다 이해해라
		  
	- 백엔드 개발자 취업 로드맵
		  
	- 근거 기반 답변할수있어야함
		그래들 저장소는 메이븐 리포지토리
		lts - 가장 안전한 버전 그쪽에서 정한다.
---
- **지식**
	- **채팅은 일반적인 백엔드와 많이 다른 영역이다**
		- 샌드버드 - 채팅 대기업
			- 대부분 채팅 API는 여기서 지원 받는다.
			- 대표적인 기능들 중 ChatBot이 있다.
		
	-  **CRUD를 만들 때 주의할 점**
		- 단순한 curd를 만들더라도 좋은 구조 설계 객체지향적으로 만들었는가를 고민해야한다.
		  
	- **Spring에 대해 공부할 때 구글에 좋은 검색 방법**
		- how dose spring framework?
		
	- **챗지피티로 코드의 흐름을 설명을 요청할 때 팁**
		- 이 코드를 설명해줘 "~한다면 ~할것이다"라는 느낌으로 
		  설명해달라고 하면 이해하기 쉽게 설명할 것이다.

---
#### good-information  
- **famous saying**
	- 버락 오바마
		**휴대폰을 갖고 놀지만 말고 프로그램을 만들어라. 코딩을 배우는 것이 여러분의 미래는 물론 조국의 미래에도 매우 중요하다.**
	- Larry Flon - 구조적 프로그래밍에 대한 연구 저자
		**아무리 구조가 잘 되어 있더라도, 프로그래머가 나쁜 프로그램을 만드는 걸 막아주는 프로그래밍 언어는 없다.**
	- 임백준
		**페어프로그래밍이 의미를 갖는 것은 물론 공평한 규칙이 지켜지는 것에 한해서이다.  
		공평한 규칙의 요소는 "실력"이 아니라 "열정"이다. 프로그래밍 실력은 차이가 나도 페어프로그래밍을 수행하는데 아무 상관이 없다.  
		그렇지만 열정의 수준은 동등해야 한다.**
- **Book**
	- 클린 코드  
##### GPT 질문 예시

- **`stream()`**: "모든 사람의 이름을 차례로 가져와!"
- **`map()`**: "이 사람 이름을 다른 형태로 바꿔줘!"
- **`collect()`**: "바꾼 결과들을 다시 리스트로 만들어서 나한테 줘!"

이렇게 `stream()`을 사용하면 **데이터를 쉽게 변환**하고 **리스트로 모을 수** 있어서 코드가 더 짧고 간결해집니다.

---
##### 2. 유용한 코드

- 더미데이터 메서드
		//    대량 insert 더미 데이터 메서드  
	//    @GetMapping("test")  
	//    public String test(HttpSession session) {  
	//        UserDTO logIn = (UserDTO) session.getAttribute("logIn");  
	//        if (logIn == null) {  
	//            return "redirect:/";  
	//        }  
	//        for (int i = 1; i <= 300; i++) {  
	//            ItemDTO itemDTO = new ItemDTO();  
	//            itemDTO.setName("테스트 상품이름 " + i);//            itemDTO.setDescription("테스트" + i + "번 상품 설명입니다.");  
	//            itemDTO.setPrice(1000);  
	//            itemDTO.setQuantity(100);  
	//            itemDTO.setUserId(logIn.getId());  
	//            itemService.insert(itemDTO);  
	//        }  
	//  
	//        return "redirect:/item/showAll";  
	//    }

---
##### 3. 아이디어 
###### 상용 정보
- 상영정보를 이렇게 활용해 볼수 있지 않을까?!
``` java
@RestController
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{userId}")
    public ResponseEntity<User> getUserById(@PathVariable Long userId) {
        // userId를 사용하여 특정 사용자 정보 조회
        User user = userService.getUserById(userId);
        if (user != null) {
            return ResponseEntity.ok(user);
        } else {
            return ResponseEntity.notFound().build();
        }
    }
	
    @GetMapping("/{userId}/posts/{postId}")
    public ResponseEntity<Post> getPostById(@PathVariable Long userId, @PathVariable Long postId) {
        // userId와 postId를 사용하여 특정 사용자의 특정 포스트 조회
        Post post = postService.getPostById(userId, postId);
        if (post != null) {
            return ResponseEntity.ok(post);
        } else {
            return ResponseEntity.notFound().build();
        }
    }
    // 추가적인 API 메서드들...
}
```



---




---
#### spec

- **언제든 설명할 수 있는 지식**

---
#### annotation-study-method  


---
#### analects

---

#### trouble-shooting

##### Jmeter 로그인 대용량 트래픽 테스트을 위한 필수 세팅

- CSV Data Set Config 설정
    - Filename: users.csv (email,password 포함된 파일)
    - Variable Names: email,password
    - Ignore first line: True
    - 예시:
        - `email,password test1@naver.com,123456789`
    
- Thread Group 설정
    - Number of Threads: 테스트할 사용자 수 (예: 30)
    - Loop Count: 반복 횟수 (1로 설정하면 사용자당 1회 로그인)
    
- HTTP Request 설정
    - Method: POST
    - Path: /login
    - Body Data: 아래 JSON 형식 입력
    - Use multipart: 체크하지 않음
    - Body 예시:
        - `{   "email": "${email}",   "password": "${password}" }`
    - 필수 Header:
        - Content-Type: application/json
        - Accept: application/json
    
- 서버 쪽 사전 조건
    - 로그인 API는 email, password 필드명을 JSON으로 받아야 함
    - csrf().disable() 설정 필요 (CSRF 토큰 없이도 POST 가능)
    - /login 경로가 permitAll()로 허용되어야 함
    - DB의 비밀번호는 반드시 BCrypt 해시로 저장되어야 함
    - `BCryptPasswordEncoder.matches("123456789", dbHash)`가 true가 되어야 로그인 성공
    
- View Results Tree 확인
    - 전송된 JSON에 `${email}`이 실제 사용자 이메일로 치환됐는지 확인
    - 응답 상태 코드가 200 OK인지, 아니라면 401 메시지 내용 확인
    
- 로그인 성공 시 토큰 추출 (선택 사항)
    - JSONPath Extractor로 token 값 추출 가능
    - 이후 API 요청에 Authorization: Bearer ${token} 헤더 추가 가능

---

- 요약 순서
    
    - CSV 설정 (email/password)
        
    - Thread Group 사용자 수 설정
        
    - HTTP Request → POST + JSON + Header
        
    - 서버 로그인 API 구조와의 정합성 확인
        
    - View Results Tree로 응답 및 치환 여부 확인


## notebook-archive

- Gpt 활용법
	- 지금부터 너는 15년차 경력자로서 나에게 답변을 구해줘
	- 10살 아이에게 설명하듯 쉼게 설명해줘
	- 정답을 알려주지는 말고 힌트를 알려줘
	  
- 코딩테스트
	- 알고리즘
		- GCD - 최대 공약수 구하기
		- LCD - 최소 공약수 구하기
		- 올림 나눗셈
		  
	- 코딩테스트 접근법
		1. 문제 분석
		2. 아이디어 도출
		3. 컴포넌트 학습
		4. Paseudocode 작성
		5. 코딩 및 검증

- 멘토링
	- cs 근거를 기반으로 문제해결방안을 적용해야한다.
	- 문제를 일부러 만들어서 해결하라(일부러 데이터를 많이 넣어보아라)
		- 사용자경험을 통해서 등등
	1. 문제를 만들어라
	- 멘토님 숙제
		- 프로젝트를 더 내용을 채우고 싶다면,
		    1. 문제가 없다면? 직접 만들 수 있어야한다
		        1. 예를 들어, 데이터를 왕창 집어넣어서 의도적으로 쿼리를 느리게 만들어야한다.
		        2. 동시성 문제가 없었는데 내가 그걸 어거지로 시나리오를 만들어서 했다던지.
		            1. 없는 시나리오를 직접 제안해서 그 상황을 맞딱뜨린다.
		    2. 문제를 만들어서 개선을 한다면 어떤 내용이 중점이 되어야하는가?
		        1. 나의 기본기를 드러낼 수 있어야한다.


---
- java
	- 자바의 특징 및 장점에 대해 설명해 주세요.
		- 플랫폼 독립성
		- 객체지향 프로그래밍 지원
		- 풍부한 라이브러리, API
		- 메모리 관리, 가비지 컬렉션
		- 보안성
		- 멀티스레딩 지원
		- 풍부한 개발 도구
		  
	- JVM, JRE, JDK의 차이점은 무엇인가요?
		- JVM - 자바 바이트 코드 실행 가상 머신
		- JRE - 자바 애플리케이션 실행 환경 제공
		- JDK - 개발 및 빌드 패키지
		  
	- 객체지향 프로그래밍(OOP)의 4대 원칙에 대해 설명해 주세요.
		- 캡슐화
		- 상속
		- 다형성
		- 추상화
		  
	- 메소드 오버로딩과 오버라이딩의 차이점을 설명해 주세요.
		- 오버로딩 - 같은 클래스 내에 같은 메서드의 매개변수 종류, 개수를 재정의
		- 오버라이딩 - 상위 클래스에 정의된 메서드를 하위 클래스에서 재정의
		  
	- 자바의 예외 처리 메커니즘에 대해 설명해 주세요.
		- 구성요소 - `try-catch-finally`
		- 예외유형
			- Checked Exception - 컴파일 시점 예외처리 강제, 명시적 예외 처리
			- Unchecked Exception - 컴파일 예외, 필수는 아니지만 오류 유발 가능성
		- 전파 및 선언
			- throws 키워드 메서드가 발생시킬 수있는 예외 선언 , 상위 호출자로 전파
			  
	- 자바 컬렉션 프레임워크의 주요 인터페이스와 각 자료구조의 특징은 무엇인가요?
		- List - 순서가 있는 요소의 모음
			- ArrayList
			- LinkedList
		- Set - 중복을 허용하지 않는 요소의 집합
			- HashSet
			- TreeSet
		- Map - 키와 값의 쌍으로 데이터 저장, 키는 중복불가능
			- HashMap
			- TreeMap
		- Queue - FIFO 방식, 작업 대기열등에 사용
			- LinkedList(큐로 활용)
			- PriorityQueue
			
	- 자바에서 쓰레드 생성 및 동기화 방법에 대해 설명해 주세요.
		- 
	- 가비지 컬렉션의 작동 원리와 자바에서의 메모리 관리 방법에 대해 설명해 주세요.
	- 자바 8에서 도입된 람다 표현식과 스트림 API의 주요 개념과 장점은 무엇인가요?
	- 불변 객체(Immutable Object)란 무엇이며, 자바에서 불변 객체를 구현하는 방법은 무엇인가요?
- spring boot
	- Spring Boot란 무엇이며, 기존 Spring Framework와의 주요 차이점은 무엇인가요?
	- Spring Boot의 주요 특징과 장점에 대해 설명해 주세요.
	- Spring Boot에서 자동 구성(Auto-Configuration)은 어떻게 동작하며, 이를 통해 얻는 이점은 무엇인가요?
	- Spring Boot Starter의 개념과 활용 방법에 대해 설명해 주세요.
	- Spring Boot 애플리케이션에서 application.properties 또는 application.yml 파일의 역할과 설정 방법은 무엇인가요?
	- Spring Boot Actuator의 기능과 모니터링 역할에 대해 설명해 주세요.
	- Spring Boot에서 내장 톰캣(Embedded Tomcat)의 장단점은 무엇이며, 이를 활용한 배포 방식에 대해 설명해 주세요.
	- Spring Boot에서 RESTful API를 구축할 때 사용하는 주요 어노테이션과 설계 방법은 무엇인가요?
	- Spring Boot에서 데이터베이스 연동을 위한 JPA 또는 JDBC 설정 및 활용 방법에 대해 설명해 주세요.
	- Spring Boot에서 프로파일(Profile) 개념은 무엇이며, 이를 통해 애플리케이션 환경을 어떻게 분리하고 관리할 수 있나요?
- mysql
	- MySQL이란 무엇이며, 주요 특징은 무엇인가요?
	- MySQL의 아키텍처와 내부 동작 방식에 대해 설명해 주세요.
	- MySQL에서 인덱스(Index)의 역할과 종류, 그리고 사용 시 고려사항은 무엇인가요?
	- MySQL에서 다양한 데이터 타입(숫자, 문자열, 날짜 등)에 대해 설명해 주세요.
	- MySQL에서 조인(Join)의 종류(내부 조인, 외부 조인 등)와 사용 방법에 대해 설명해 주세요.
	- MySQL의 트랜잭션(Transaction)과 ACID 특성에 대해 설명해 주세요.
	- MySQL에서 데이터베이스 정규화(Normalization)의 개념과 필요성에 대해 설명해 주세요.
	- MySQL의 뷰(View)와 저장 프로시저(Stored Procedure)의 차이점 및 사용 사례는 무엇인가요?
	- MySQL의 복제(Replication) 기능과 이를 구성하는 방법에 대해 설명해 주세요.
	- MySQL 성능 최적화를 위한 주요 전략과 도구에는 어떤 것들이 있나요?
- spring security
	1. 스프링 시큐리티란 무엇이며, 주요 기능은 무엇인가요?
	2. 스프링 시큐리티에서 인증(Authentication)과 인가(Authorization)의 차이점은 무엇인가요?
	3. 스프링 시큐리티의 기본 필터 체인(Filter Chain)이란 무엇이며, 어떻게 동작하나요?
	4. CSRF(Cross-Site Request Forgery) 공격에 대한 방어 방법과 스프링 시큐리티에서의 구현 방식은 무엇인가요?
	5. 스프링 시큐리티의 Remember-Me 기능은 무엇이며, 어떻게 구성하나요?
	6. 사용자 정의 로그인 페이지와 인증 처리를 스프링 시큐리티에서 설정하는 방법은 무엇인가요?
	7. PasswordEncoder의 역할과 스프링 시큐리티에서 제공하는 구현체에 대해 설명해 주세요.
	8. 스프링 시큐리티의 메소드 보안(Method Security) 기능과 관련 어노테이션(@PreAuthorize, @PostAuthorize 등)의 사용법은 무엇인가요?
	9. OAuth2를 활용한 인증 및 인가 구현 시 스프링 시큐리티의 구성 요소와 흐름은 어떻게 되나요?
	10. 스프링 시큐리티를 적용한 REST API의 보안 설정 시 고려해야 할 주요 사항은 무엇인가요?
- rest ful api
	1. RESTful API란 무엇이며, REST 아키텍처의 주요 원칙은 무엇인가요?
	2. HTTP 메소드(GET, POST, PUT, DELETE 등)가 RESTful API에서 각각 어떤 역할을 하는지 설명해 주세요.
	3. RESTful API 설계 시 리소스(Resource)와 URI 설계 원칙에 대해 설명해 주세요.
	4. RESTful API에서 HTTP 상태 코드의 역할과 적절한 사용 방법에 대해 설명해 주세요.
	5. HATEOAS(Hypermedia as the Engine of Application State)의 개념과 RESTful API 설계에서의 장점은 무엇인가요?
	6. RESTful API의 버전 관리 방법과 그 필요성에 대해 설명해 주세요.
	7. RESTful API에서 요청 및 응답 데이터 포맷(JSON, XML 등)의 선택 기준과 각각의 장단점은 무엇인가요?
	8. RESTful API 보안을 위해 고려해야 할 인증(Authentication) 및 인가(Authorization) 전략은 무엇인가요?
	9. RESTful API 문서화를 위한 도구(예: Swagger)와 그 활용 방법에 대해 설명해 주세요.
	10. RESTful API 성능 최적화를 위한 캐싱 전략 및 기법에는 어떤 것들이 있으며, 이를 어떻게 구현할 수 있나요?
- docker
	1. **Docker란 무엇이며, 기존 가상 머신과 비교할 때의 장점은 무엇인가요?**
	2. **Docker 이미지(Image)와 컨테이너(Container)의 차이점은 무엇인가요?**
	3. **Dockerfile의 역할과 기본 구성 요소에 대해 설명해 주세요.**
	4. **Docker Compose란 무엇이며, 여러 컨테이너를 어떻게 관리할 수 있나요?**
	5. **Docker Hub와 자체 Docker Registry의 차이점은 무엇인가요?**
	6. **Docker 네트워킹의 기본 개념과 컨테이너 간 통신 방법에 대해 설명해 주세요.**
	7. **Docker 볼륨(Volume)과 바인드 마운트(Bind Mount)의 차이점은 무엇인가요?**
	8. **Docker 컨테이너의 보안 모범 사례와 관련 설정 방법은 무엇인가요?**
	9. **다중 스테이지 빌드를 활용하여 Docker 이미지 크기를 최적화하는 방법에 대해 설명해 주세요.**
	10. **Docker의 로그 관리와 모니터링 전략은 무엇이며, 어떤 도구들을 활용할 수 있나요?**
- aws
	1. **AWS란 무엇이며, 클라우드 컴퓨팅의 주요 장점은 무엇인가요?**
	2. **AWS의 주요 서비스(예: EC2, S3, RDS 등)의 기능과 역할에 대해 설명해 주세요.**
	3. **EC2 인스턴스와 Auto Scaling의 개념 및 이를 통한 애플리케이션 확장 방법은 무엇인가요?**
	4. **S3 버킷의 구성 요소와 데이터 보안을 위한 주요 설정 방법에 대해 설명해 주세요.**
	5. **AWS IAM(Identity and Access Management)의 역할과 정책 작성 방법은 무엇인가요?**
	6. **AWS VPC(Virtual Private Cloud)의 기본 구성 요소(서브넷, 라우팅 테이블, 게이트웨이 등)에 대해 설명해 주세요.**
	7. **AWS에서 인프라를 코드로 관리하기 위한 도구(예: CloudFormation, Terraform)의 차이점은 무엇인가요?**
	8. **AWS Lambda와 서버리스 아키텍처의 주요 장단점 및 활용 사례는 무엇인가요?**
	9. **AWS RDS의 고가용성(HA) 구성 방법과 백업 전략에 대해 설명해 주세요.**
	10. **AWS CloudWatch를 이용한 모니터링과 로그 관리는 어떻게 이루어지며, 주요 활용 사례는 무엇인가요?**
- git
	1. **Git의 기본 개념과 분산 버전 관리 시스템(DVCS)의 장점은 무엇인가요?**
	2. **Git과 기존 버전 관리 시스템(SVN 등)과의 주요 차이점은 무엇인가요?**
	3. **Git의 기본 워크플로우(커밋, 푸시, 풀, 클론 등)에 대해 설명해 주세요.**
	4. **Git 브랜치(Branch) 관리 및 머지(Merge) 전략에 대해 설명해 주세요.**
	5. **Git에서 Rebase와 Merge의 차이점과 각각의 사용 시나리오는 무엇인가요?**
	6. **Git에서 발생하는 충돌(Conflict)을 해결하는 방법에 대해 설명해 주세요.**
	7. **Git의 스태시(Stash) 기능은 무엇이며, 언제 활용하면 좋은지 예를 들어 설명해 주세요.**
	8. **Git 태그(Tag)의 역할과 버전 관리를 위한 사용 방법은 무엇인가요?**
	9. **Git의 히스토리 관리(예: log, reflog) 기능과 이를 활용한 문제 해결 방법에 대해 설명해 주세요.**
	10. **협업 환경에서의 Pull Request(PR) 프로세스와 코드 리뷰의 중요성에 대해 설명해 주세요.**
- linux
	1. **Linux 운영체제의 기본 구조와 커널의 역할에 대해 설명해 주세요.**
	2. **Linux에서 프로세스(Process)와 스레드(Thread)의 차이점은 무엇인가요?**
	3. **파일 및 디렉토리 관리를 위한 주요 Linux 명령어(ls, cp, mv, rm 등)에 대해 설명해 주세요.**
	4. **Linux에서 사용자 및 권한 관리를 위한 주요 명령어(chmod, chown, useradd 등)와 개념은 무엇인가요?**
	5. **시스템 모니터링을 위한 Linux 명령어(top, ps, htop 등)의 사용법과 특징에 대해 설명해 주세요.**
	6. **패키지 관리 도구(apt, yum, dnf 등)의 역할과 사용 방법에 대해 설명해 주세요.**
	7. **Linux 셸 스크립트의 기본 구조와 이를 활용한 자동화 작업의 예제에 대해 설명해 주세요.**
	8. **Linux에서 네트워크 설정 및 문제 해결을 위한 주요 명령어(ifconfig, ip, netstat, ping 등)에 대해 설명해 주세요.**
	9. **Linux 시스템에서 로그 파일 관리의 기본 위치와 주요 로그 파일(예: /var/log/syslog, /var/log/messages 등)에 대해 설명해 주세요.**
	10. **Linux 부팅 과정과 관련된 부트로더(예: GRUB) 및 init 시스템(systemd, init.d 등)의 역할에 대해 설명해 주세요.**
---

1. 프로젝트 정보
	- 네이버 클라우드 로그인 정보
		- code - camp26
		- id - camp26
		- ps - ncloudcamp26!
	- server
		- server name - 
		- 공인 IP - 
		- SSH 보안 키 - 
	- mysql db
		- username - 
		- password - 
	- docker login
		- donguk963@gmail.com
		- ehddnr963!
	- docker repository
		- atoonatoo/solo-project-repository
	  
2.  프로젝트 생성
	- **Spring Boot 프로젝트 생성
	- Spring Stater DI 주입
	- Gradle Build 사용
	- application.yaml 사용
	
3. git repository 생성

---
#### 📚 4) 프로젝트 + Git 연동
#### 📚 5) 클라우드 서버 생성
#### 📚 6) SSH 배포 구성 설정
#### 📚 7) DB 생성 및 설정 
#### 📚 8) 프로젝트 + DB Conection 연동
#### 📚 9) Docker 컨테이너 + 이미지 + Hub 생성
#### 📚 10) Cloud Server 내부 세팅
#### 📚 10) Remote Host + docker Compose.yaml 복사

#### 📚 11) Cloud Server + Git Pull
#### 📚 12) Docker Compose DB 세팅 
#### 📚 13) Cloud Server + Spring Boot 실행
#### 📚 14) Front End 프로젝트 세팅
#### 📚 15) Cloud Server + Front End 내부 세팅 
#### 📚 16) Cloud Server + Front End 실행
#### 📚 17) 최종 세팅 테스트 


#### 📚 2) 프로젝트 생성

> [!info]
프로젝트를 실질적으로 개발하기 위한 IDE 프로젝트에 구동을 위한 필수적인 세팅을 완료한다.

- **프로젝트 폴더 위치**
	- 사용자 단에 위치해야 한다.
- **환경 세팅**
	- `build.gradle`, `application.yaml` 정상적인 구동 가능하도록 설정한다.

#### 📚 3) NCloud 생성 및 관리

#### 📚 4) Docker 설치 및 관리

- **컨테이너 생성**: Docker 컨테이너 생성
- **이미지 생성**: Docker 이미지 생성

#### 📚 5) **컨테이너 프로비저닝 (Container Provisioning)**:
> [!info]
> 본 프로젝트는 클라우드 서버 내의 Docker 컨테이너를 활용하여 프로젝트를 세팅 할 것이다. 
> Docker는 기본적으로 Linux 컨테이너 기술을 기반으로 한다.
> Linux 커널의 기능을 직접 활용하며 그 밖의 패키지 여러가지 많은 
> 
  
##### 패키지 매니저
	
- 각 리눅스 배포판마다 패키지 설치를 위한 매니저가 있으며, 애플리케이션 실행에 필요한 패키지를 설치할 수 있습니다.
	
- Ubuntu 계열 
	
	apt-get update
	apt-get install -y <패키지명>
	
- Alpine Linux:
	  
	apk update
	apk add <패키지명>

##### 필수 시스템 패키지
	
- 애플리케이션을 실행하기 위해 컨테이너 내에 필요한 기본 유틸리티나 라이브러리를 설치해야 할 수 있습니다. 
- 예를 들어, 네트워크 도구나 디버깅을 위한 툴들이 필요할 수 있습니다.
	
- **curl**
	- 네트워크 요청을 테스트할 때 많이 사용
	- apt-get install -y curl
- **vim** 또는 **nano**
	- 파일 편집을 위한 텍스트 에디터.
	- apt-get install -y vim

##### 개발 환경 패키지

- 애플리케이션을 개발하거나 빌드할 때 필요한 컴파일러나 빌드 도구를 설치해야 할 수 있습니다.

- **build-essential**
	- C/C++ 컴파일러와 관련 라이브러리.
	- apt-get install -y build-essential
- **Git**
	- 소스 코드를 Git 저장소에서 클론할 때 필요합니다.
	- apt-get install -y git

##### 프로그래밍 언어 런타임

- Docker 이미지 내부에서 특정 프로그래밍 언어로 개발된 애플리케이션을 실행하려면, 해당 언어의 런타임 환경을 설치해야 합니다.

- **Java (OpenJDK)**
	- Java 애플리케이션 실행을 위해 필요
	- apt-get install -y openjdk-11-jdk
- **Python**
	- Python 애플리케이션을 실행하려면 Python 런타임을 설치해야 합니다.
	- apt-get install -y python3
- **Node.js**
	- JavaScript/TypeScript 기반의 애플리케이션을 실행하려면 Node.js를 설치해야 합니다.
	- apt-get install -y nodejs npm

##### 데이터베이스 관련 패키지

- Docker 컨테이너 내부에서 데이터베이스를 설치하고 사용하려면 해당 데이터베이스의 관련 패키지를 설치해야 합니다.

- **MySQL**
	- apt-get install -y mysql-server
- **PostgreSQL**:
	- apt-get install -y postgresql

##### 추가적인 런타임 의존성

- 애플리케이션을 실행하기 위해 추가적인 라이브러리나 런타임이 필요할 수 있습니다.

- **libssl**
	- SSL/TLS 통신을 위한 필수 라이브러리.
	- apt-get install -y libssl-dev
- **libpq**
	- PostgreSQL 관련 라이브러리
	- apt-get install -y libpq-dev
#### 3. Docker 설치

#### 📚 6) DB 연동

- **MYSQL Workbench 설정**:
    1. IntelliJ 우측 DB 아이콘 클릭
    2. 추가 버튼 → 데이터 소스 → MYSQL 선택
    3. 이름: `DB명@localhost`
    4. 사용자: `root`
    5. 비밀번호 입력
    6. 적용 후 확인

#### 5. SSH Configuration

- **Remote Host 설정**:
    1. 검색 → Remote Host
    2. `...` 클릭
    3. 서버 추가: SFTP
- **SSH 배포**:
    1. 호스트: N클라우드 공인 IP
    2. 사용자 이름: `root`
    3. 비밀번호: 서버 보안 키
    4. 비밀번호 변경: `passwd` 명령어 사용
    5. 연결 테스트 성공 후 적용

#### 6. VSCode에 있는 `application.yaml` 가져오기

- **파일 경로**:
    1. 스프링부트 프로젝트에 `application.yaml` 붙여넣기
    2. Remote Host SSH 서버의 `home` 디렉토리에 옮기기

#### 6-2. Docker Compose Up 사용법

- **Docker Compose**: 여러 개의 Docker 컨테이너를 쉽게 관리할 수 있는 도구로, 여러 서비스를 한 번에 실행할 수 있다.

##### Docker Compose Up 실행 방법

1. **`docker-compose.yml` 파일 작성**:
    
    - Docker Compose 설정을 위한 `docker-compose.yml` 파일을 프로젝트 루트 디렉토리에 생성한다.
    - 서비스 정의:
        - **web 서비스**: Nginx 이미지를 사용하고, 호스트의 8080 포트를 컨테이너의 80 포트에 매핑.
        - **db 서비스**: MySQL 이미지를 사용하며, 루트 비밀번호를 환경 변수로 설정.
    
    **구성 예시**:
    
    - 버전: `'3'`
    - 서비스:
        - **web**:
            - 이미지: `nginx`
            - 포트: `8080:80`
        - **db**:
            - 이미지: `mysql`
            - 환경 변수: `MYSQL_ROOT_PASSWORD: example`
2. **`docker-compose up` 명령어 실행**:
    
    - 터미널에서 해당 프로젝트 디렉토리로 이동 후, `docker-compose up` 명령어를 실행하여 정의된 모든 컨테이너를 한 번에 실행.
    - `-d` 옵션을 사용하면 백그라운드에서 실행된다: `docker-compose up -d`.
3. **컨테이너 상태 확인**:
    
    - `docker-compose ps` 명령어로 현재 실행 중인 컨테이너 상태를 확인할 수 있다.
4. **컨테이너 종료**:
    
    - 실행 중인 컨테이너는 `Ctrl + C`로 종료할 수 있으며, `docker-compose down` 명령어를 사용하여 모든 컨테이너와 네트워크를 중단하고 삭제할 수 있다.

##### 요약

- **Docker Compose**는 여러 서비스를 동시에 실행하고 관리할 수 있는 도구이다.
- **`docker-compose.yml` 파일**에 각 서비스 설정을 작성하고, `docker-compose up` 명령어로 이를 실행하면, 여러 Docker 컨테이너가 한 번에 시작된다.
- 실행 후, 컨테이너의 상태를 확인하거나 종료할 수 있는 명령어로 쉽게 관리가 가능하다.

이 과정을 통해 여러 Docker 서비스를 동시에 간편하게 설정하고 운영할 수 있습니다.

#### 7. NCloud Server 생성

- **NCloud 계정 로그인**: [NCloud 서브계정 로그인](https://auth.ncloud.com/login)
- **서버 생성 및 관리**:
    1. NCP에서 서버 생성
    2. 공인 IP 설정
    3. ACG(Access Control Group) 설정
    4. 서버에 Docker 설치
    5. Docker 이미지 생성 및 업로드
    6. Docker 이미지 실행하여 애플리케이션 배포
    7. Redis, RabbitMQ 같은 추가 서비스 Docker 컨테이너로 배포

#### 8. NCloud 서버에 프로그램 설치

- **필요 소프트웨어 설치**:
    1. JDK 설치
	    - 시스템 패키지 업데이트
		    - sudo apt update
		- OpenJDK 17 설치
			- sudo apt install -y openjdk-17-jdk
		- 
    2. Git 설치 및 Repository Clone:
        - `sudo apt update`
        - `sudo apt install git`
        - `git clone https://github.com/사용자이름/리포지토리이름.git`
        - Git 사용자 정보 설정:
            - `git config --global user.name "atoonatoo"`
            - `git config --global user.email "donguk963@gamil.com"`
        - Personal Access Token 등록:
            1. GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic) → Generate new token
            2. Repository 토큰 설정:
                - `git remote set-url origin https://<토큰>@github.com/사용자이름/리포지토리이름.git`
            3. 확인: `ls`

#### 9. Docker로 추가 서비스 배포

- **배포할 서비스**: MySQL, MongoDB, Redis 등
- **참고**: [CI/CD 가이드](https://velog.io/@gjwjdghk123/CI-CD1)

#### 10. Gradle 빌드 및 Jar 설치

- **빌드 과정**:
    1. `./gradlew build` 명령어로 빌드
    2. 빌드 파일 확인: `cd build/libs/` → `ls`
    3. JAR 파일 실행: `java -jar application-0.0.1-SNAPSHOT.jar`

#### 11. Ubuntu 22에서 Java 환경변수 설정 및 Vim 사용법

##### 1. **Vim으로 `JAVA_HOME` 환경변수 설정**

- Java 설치 후, `JAVA_HOME` 환경변수를 설정해야 한다. 이 과정에서 Vim을 사용해 환경변수 파일을 수정한다.
    
- **환경변수 설정 과정**:
    
    1. **Vim으로 파일 열기**:
        - sudo vim /snap/bin 
        - 명령어로 환경변수 파일을 연다.
    2. **JAVA_HOME 설정 추가**:
        
        - 파일 내에 아래와 같이 `JAVA_HOME` 경로를 추가한다.
            
            `JAVA_HOME="/usr/lib/jvm/java-<버전>"`
            
        - 예시: `JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"`
            
    3. **파일 저장 후 종료**:
        
        - `Esc`를 누르고, `:wq` 명령어로 파일을 저장하고 종료한다.

##### 2. **`JAVA_HOME` 확인 및 반영**

- **환경 변수 반영**:
    
    - 파일을 수정한 후, 다음 명령어로 환경 변수를 시스템에 반영한다:
        
        `source /snap/bin`
        
- **설정 확인**:
    
    - `echo $JAVA_HOME` 명령어로 `JAVA_HOME`이 올바르게 설정되었는지 확인할 수 있다.
#### 12. Front-end 세팅 (React/Next.js)

- **필수 설치 패키지**:
    
    1. **Yarn 설치**: 자바스크립트 패키지 매니저로, 프로젝트 의존성을 관리.
    2. **React 설치**: Next.js와 함께 프론트엔드 개발에 필수적인 라이브러리.
    3. **TypeScript 설치**: 자바스크립트의 상위 언어로, 정적 타입을 제공.
    4. **Chocolatey 설치**: 윈도우에서 패키지 관리를 위한 매니저로, 다른 필수 도구들을 쉽게 설치 가능.
    5. **npm 설치**: Node.js 패키지 매니저로, Yarn과 함께 의존성 관리를 할 수 있음.
- **설치 순서**:
    
    1. Chocolatey 설치 후, Yarn 설치.
    2. Yarn을 통해 React와 TypeScript 설치.
    3. Yarn 또는 npm으로 Next.js 프로젝트 생성.
- **Next.js 프로젝트 설치**:
    
    1. 터미널에서 `yarn create next-app` 명령어를 실행하여 프로젝트 생성.
    2. 생성된 프로젝트에서 `yarn run dev`로 개발 서버를 실행하고, `localhost:3000`에서 웹 애플리케이션을 확인.
- **참고 링크**: [참고 사이트](https://www.evernote.com/shard/s294/client/snv?isnewsnv=true&noteGuid=e157e52e-5312-d9a7-b458-8f431d7818d8&noteKey=OdXtWaLc4veG4xpetekehxY18-S7xUnP3DRFE1rbGtGcbq_wtWbg920BMw&sn=https%3A%2F%2Fwww.evernote.com%2Fshard%2Fs294%2Fsh%2Fe157e52e-5312-d9a7-b458-8f431d7818d8%2FOdXtWaLc4veG4xpetekehxY18-S7xUnP3DRFE1rbGtGcbq_wtWbg920BMw&title=%25EC%25A0%259C%25EB%25AA%25A9%2B%25EC%2597%2586%25EC%259D%258C)
- 
#### 13. Ncloud에서 Spring Boot 실행 방법

- Gradle로 빌드 후 JAR 파일을 실행.
    1. `./gradlew build`로 빌드.
    2. `build/libs/`에서 JAR 파일 확인.
    3. `java -jar application-0.0.1-SNAPSHOT.jar`로 실행.

#### 14. TypeScript로 프론트엔드 실행 방법

- **Node.js 설치 후 npm 또는 yarn 사용**:
    1. `npm install` 또는 `yarn install`로 필요한 패키지 설치.
    2. `yarn run dev` 명령어로 개발 서버 실행 (VSCode 터미널에서 실행 가능).
    3. `localhost:3000`으로 접속해 웹 애플리케이션 확인 (VSCode 터미널에서 `Ctrl + Click`으로 바로 접속 가능).

#### 15. Swagger 설정 및 실행 방법

- Spring Boot에서 Swagger UI 설정.
    1. `springdoc-openapi-ui` 의존성 추가.
    2. Ncloud 서버에서 JAR 파일 실행.
    3. `http://<NCloud-IP>:8080/swagger-ui.html`에서 Swagger UI 확인.

#### 16. Gradle과 Git 토큰 연동 방법

- GitHub Personal Access Token 사용.
    1. GitHub에서 토큰 발급.
    2. `git remote set-url origin https://<토큰>@github.com/username/repository.git`으로 설정.
    3. Gradle로 GitHub와 연동 및 푸시.

#### 17. NCloud 서버에 리눅스로 Git 설치 및 사용법
##### 1. **NCloud 서버에서 Git 설치**

- **Git 설치 명령어**:
    - `sudo apt-get install -y git`
    - 이 명령어를 통해 NCloud 서버의 리눅스 환경에 Git을 설치한다.

##### 2. **Git 리포지토리 클론하는 방법**
- **리포지토리 클론 명령어**:
    - `git clone <repository-url>`
    - 예시:  
        `git clone -b main https://github.com/atoonatoo/hotel-solo-project.git`
    - **경로 주의**: Git 리포지토리를 `/home` 디렉토리에서 클론해야 한다. 터미널에서 `/home`으로 이동 후 클론 작업을 진행한다.
    - 이동 명령어:  
        `cd /home`

##### 3. **Vim 설치 방법**

- **Vim 설치 명령어**:
    - `sudo apt-get install vim`
    - 이 명령어를 사용해 Vim 텍스트 편집기를 설치한다.

##### 4. **Vim 사용하는 법 및 주요 명령어**

- **Vim 기본 사용법**:
    - Vim은 세 가지 모드로 동작한다: **일반 모드**, **편집 모드**, **명령 모드**.
    - **일반 모드**: 텍스트 탐색 및 명령어 입력.
    - **편집 모드**: 텍스트 입력. 일반 모드에서 `i`를 눌러 편집 모드로 진입.
    - **명령 모드**: 파일 저장 및 종료. 일반 모드에서 `:`를 입력해 명령 모드로 진입.
- **Vim 주요 명령어**:
    1. **편집 모드 진입**:
        - `i`: 현재 커서 위치에서 텍스트 편집.
    2. **일반 모드로 전환**:
        - `Esc`: 편집 모드에서 일반 모드로 전환.
    3. **파일 저장 및 종료**:
        - `:wq`: 파일 저장 후 종료.
        - `:q!`: 변경 사항 저장 없이 강제 종료.
    4. **파일 열기**:
        - `vim filename`: 특정 파일을 열기.

##### 5. **Git 리포지토리 삭제 명령어**

- **리포지토리 삭제 명령어**:
    - `rm -r 리포지토리명`
    - 예시:  
        `rm -r greenmarket`
    - 이 명령어로 특정 리포지토리를 서버에서 삭제할 수 있다.

#### 18. Ubuntu 비밀번호 변경

- 터미널에서 다음 명령어를 입력하여 비밀번호를 변경한다.
    
    `passwd`
    
- 프롬프트가 나타나면 현재 비밀번호와 새 비밀번호를 입력한다.
    

##### 2. **Ubuntu 업데이트**

- 터미널에서 시스템을 업데이트하려면 다음 명령어를 사용한다.
    
    `sudo apt update && sudo apt upgrade`
    
- `sudo apt update`는 패키지 목록을 업데이트하고, `sudo apt upgrade`는 모든 패키지를 최신 버전으로 업그레이드한다.

#### 19. Ubuntu 서버에 Docker 설치 및 SSH 연결

##### 1. **SSH로 서버에 접속**

- 서버에 SSH로 접속하기 위해 다음 명령어를 사용한다.
    
    `ssh root@101.79.9.132 -p 22`
    
- 프롬프트가 나타나면 비밀번호를 입력한다.
    
    `D4$qA=miubc`
    

##### 2. **시스템 업데이트 및 필수 패키지 설치**

- 패키지 목록을 업데이트하고 필수 패키지를 설치한다.
    
    1. 패키지 목록 업데이트:
        
        `sudo apt-get update`
        
    2. 필수 패키지 설치:
        
        `sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common`
        

##### **3. Docker 설치**

- 다음 과정을 통해 Docker를 설치한다.

###### 1. 우분투 시스템 패키지 업데이트

```bash
sudo apt-get update
	```

###### 2. 필요한 패키지 설치

```bash
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
```

###### 3. docker 공식 gpg키 추가

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

###### 4. docker의 공식 apt 저장소 추가

```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

###### 5. 시스템 패키지 업데이트

```bash
sudo apt-get update
```

###### 6. docker 설치

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io
```


##### **4. Dcoker Repository 생성**

- build한 Docker이미지를 올릴 저장소가 필요합니다.
- DockerHub([https://hub.docker.com/](https://hub.docker.com/))에 가입 후 새로운 Repository를 생성해줍니다.
- 앞으로 만들 Docker이미지는 해당 Repository에 지속적으로 배포될 예정이며, `namespace/repository-name`이 이미지 이름이 됩니다.



##### **5. Docker File 작성**

- 어플리케이션을 Docker 이미지로 만들기 위해서는 Docker File이 필요하므로 프로젝트 스펙에 맞게 작성해줍니다.
- SpringBoot어플리케이션을 배포하기때문에 스프링공식문서([https://spring.io/guides/topicals/spring-boot-docker/](https://spring.io/guides/topicals/spring-boot-docker/))를 참고하여 작성하였습니다.

```bash
FROM adoptopenjdk/openjdk11
EXPOSE 8080
ARG JAR_FILE=build/libs/*-SNAPSHOT.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

- `FROM adoptopenjdk/openjdk11` : 도커 레지스트리에서 필요한 이미지를 다운받아 이를 기반으로 새로운 이미지를 생성합니다.
    - 해당 프로젝트는 Java11 SDK를 사용하므로 openjdk11 다운받습니다.
- `EXPOSE 8080` : 해당 컨테이너의 8080포트를 개방합니다.
    - 이 명령어만으로 서비스와 매핑되는 건 아닙니다. 개방만 해줄 뿐입니다.
- `ARG JAR_FILE=build/libs/*-SNAPSHOT.jar` : 빌드된 jar파일 경로를 변수로 설정합니다.
- `COPY ${JAR_FILE} app.jar` : 빌드된 jar파일을 Docker 이미지안에 /app.jar로 복사합니다.
- `ENTRYPOINT ["java", "-jar", "/app.jar"]` : 컨테이너가 시작될 때 실행하는 명령어를 지정합니다.
    - java 어플리케이션을 실행하는 명령어를 적어줍니다.

- 해당 도커파일은 배포하고자하는 프로젝트의 root경로에 작성해주세요.

##### **6. Docker 이미지 생성**

- 로컬에서 이미지가 잘 생성이 되는지 테스트 해봅니다. 참고로 마지막 `.` 은 도커파일이 현재 디렉토리에 있다는 뜻입니다.

```bash
docker build -f Dockerfile -t namespace/repository-name .
```
- 

##### **7. Dorker 이미지 올리기**

- 로컬에서 생성한 이미지를 Repository에 올려봅시다.
- 도커허브계정으로 접속 후 만들어준 이미지를 push해주면 hub에 업로드된것을 확인할 수 있습니다.

```bash
docker login -u 계정이름 -p 비밀번호
docker push namespace/repository-name
```

```bsah
docker login -u donguk963@gmail.com -p ehddnr963!
docker push atoonatoo/solo-project-repository
```
##### **8. Git 설치 및 관리**

###### 1. 필요한 의존성 설치

```bash

sudo apt-get update
sudo apt-get install build-essential libssl-dev libcurl4-gnutls-dev libexpat1-dev gettext unzip


```

###### **2. Git 소스 코드 다운로드**

``` bash

cd ~
wget https://github.com/git/git/archive/refs/tags/v2.42.0.zip -O git.zip
unzip git.zip
cd git-2.42.0

```
- **참고:** 버전 번호 `v2.42.0`은 최신 버전으로 변경하세요. [Git 릴리스 페이지](https://github.com/git/git/releases)에서 최신 버전을 확인할 수 있습니다.

##### **3. Git 컴파일 및 홈 디렉토리에 설치**

``` bash

make configure ./configure --prefix=$HOME/git make all make install

```

##### **4. PATH 환경 변수 설정**

``` bash

echo 'export PATH=$HOME/git/bin:$PATH' >> ~/.bashrc
source ~/.bashrc


```

##### **5. 설치 확인**

``` bash

git --version

```

#### 20. 참고 사이트

- [NCP 서버 생성 및 Docker로 애플리케이션 배포하기](https://velog.io/@gjwjdghk123/CI-CD1)








##### 📚**명령어

##### 📚 1. **DATABASE

##### **DB 테이블 전부 삭제 및 재생성**
```SQL 
	DROP DATABASE your_database_name;
	CREATE DATABASE your_database_name;
    USE your_database_name;
    
 -- 이 명령어는 기존 데이터베이스를 삭제한 후 다시 생성하고, 
 -- 해당 데이터베이스를 사용하기 위한 명령어입니다.
```
---
##### 📚 2. **Git**

##### **Git 리포지토리 연동 해제**
```git
    git remote remove origin
       
    로컬 Git 저장소에서 원격 저장소 연결을 해제하는 명령어입니다. 
    주로 원격 저장소를 변경하거나 삭제할 때 사용됩니다.
```



---
##### 📚 3. **Linux**

##### **비밀번호 변경
```Linux
- passwd

현재 사용중인 비밀번호를 변경하는 명령어입니다.
```
---
#### 📚 4. **Vim**
#### 📚 5. **React**
#### 📚 6. **Docker**
##### **📚Interview

#### 📚자기소개서

[목표를 위한 끝없는 노력]
1. 본인이 끝까지 파고들어 본 가장 의미있었던 개발 경험 또는 개발 활동에 대해 얘기해 주세요. 그 개발 경험 또는 개발 활동을 통해 배운 점이 무엇인지, 본인의 '어떤 부분이 성장'했는지에 대해 작성해 주세요. (반드시 지원한 포지션과 관련된 경험이 아니어도 좋습니다.)  
	
	저는 처음 개발 프로젝트에 참여하면서 제 자신의 부족함을 깊이 깨달았습니다. 팀원들은 이미 다양한 기술 스택과 깊은 CS 지식을 바탕으로 프로젝트를 이끌어 나갔지만, 저는 그들과 비교했을 때 많이 부족하다는 느낌을 받았습니다. 이 경험은 저에게 큰 충격이었지만, 동시에 저를 더 나은 개발자로 성장하게 만든 원동력이 되었습니다.
	
	프로젝트 초반에는 코드 리뷰 과정에서 실수나 이해 부족으로 인해 많은 피드백을 받았고, 이러한 피드백은 제게 개발자로서의 실력을 높일 수 있는 좋은 기회였습니다. 하지만 단순히 피드백을 받는 것만으로는 부족하다는 것을 알게 되었고, 이에 따라 CS(Computer Science) 기초 지식을 탄탄히 다지기 위해 체계적인 공부를 시작했습니다.
	
	운영체제, 네트워크, 자료구조, 알고리즘 등 CS 기초를 집중적으로 공부하며, 프로젝트에 필요한 각종 기술 스택도 병행하여 학습했습니다. 학습한 내용을 실전에 적용하기 위해 개인 프로젝트도 진행하며, 실제 개발 환경에서 발생할 수 있는 문제들을 스스로 해결해보는 경험을 쌓았습니다. 이러한 과정은 저의 실력을 한 단계 더 성장시키는 계기가 되었고, 이제는 팀 내에서도 기술적 리더십을 발휘할 수 있게 되었습니다.
	
	저는 지금도 끊임없이 배우고 성장하는 것을 멈추지 않습니다. 새로운 기술을 익히고, 최신 개발 동향을 따라가며, 더 나은 코드를 작성하기 위해 노력하고 있습니다. 저의 성장 과정은 저에게 많은 것을 가르쳐 주었으며, 앞으로도 개발자로서 계속해서 발전할 것입니다.
	
	이제는 다른 팀원들과 함께 협력하며, 함께 성장할 수 있는 개발자가 되기를 희망합니다. 제가 가진 경험과 배움을 바탕으로, 더욱 견고한 기술적 토대를 쌓고, 보다 나은 프로젝트 결과를 만들어내는 데 기여할 수 있도록 최선을 다하겠습니다.

##### **📚GitHub 관리 및 면접 대비 어드바이스**

1. **퍼포먼스와 보안에 중점**:
    
    - **프로그래밍 반응 속도**: 코드의 효율성 및 응답 속도에 중점을 두어 성능 개선.
    - **보안 요소 강조**: 프론트엔드 디자인(CSS)보다는 보안 관련 코드와 기능(인증, 데이터 보호)에 더 많은 비중을 둠.
    - **게시판 기능에 초점**: 로그인 기능보다 게시판의 효율적이고 안전한 구현에 집중.
      
2. **React `fetch()` API 호출**:
    
    - React에서 `fetch()`를 사용한 API 통신을 구현하는 방법을 숙지하고 프로젝트에 적용. ([참고 자료](https://velog.io/@fltxld3/React-API-%ED%98%B8%EC%B6%9C%ED%95%98%EA%B8%B0))
      
3. **GitHub 포트폴리오**:
	
    - 퍼포먼스 개선 사례와 보안 관련 코드 커밋을 명확히 기록.
    - 면접 시 프로젝트의 보안, 성능 최적화 작업을 설명할 수 있도록 준비.
##### 📚**채용 정보
- Nest.js 라는 것을 요구한다. Node.js와 같은 분류인 것인가?
- OOP의 능숙하고 높은 이해도를 요구한다.
- 리눅스 높은 이해도를 필수적으로 요구한다.
- 프로그램 기술 설계 및 개발 경험을 요구한다.
- Docker, Git  등등 
- 타입스크립트?를 많이들 요구한다.
- GitHub Actions? TeamCity?
#### 📚기업이 요구하는 스펙
##### 기술 스텍과 역량
- 추천 알고리즘 개발 경험
- AWS 인프라 구성 및 운영 경험
- Node.js 기반 개발 경험
- 서버 성능 테스트 경험
- 대용량 데이터, 트래픽을 고려한 개발 경험
- ChatGPT API 등 다양한 AI API 사용 경험
- 스타트업 경험이 있으신 분  
- 개발 팀 리딩 경험이 있으신 분
##### 우대사항
- 직접 서비스를 개발하고 제공해본 경험자
- 모니터링 로그 알람 시스템 설계 경험자
- 본인만의 테스트 코드 작성에 대한 철학이 있는 사람
- 대용량 트래픽 경험?
- 웹서비스를 이해하고, 개발해본 경험
- golang을 이용하여 백엔드 개발 경험
- 네트워크 전공 및 자격 보유자(CCNP)
-  TCP/IP , Switching, Routing 등 네트워크 전문지식 보유
##### 마인드
- 새로운 분야에 대한 배움 및 자기성장에 두려움이 없는 마인드
- 기존 시스템의 구조를 파악하고 재설계하는 것에 거부감이 없고, 즐기는 마인드를 보유
- 코드 퀄리티보다는 프로덕트를 우선시 마인드
- 동료간의 커뮤니케이션 능력


##### Interview

- Interview 관련
	- Readme를 링크로 남기며 예상 질문에 대한 준비를 하자.
		- 제목 서술
		- 문제 해결 능력 서술
		- Quester들은 기술면접도 보지만 문제해결능력을 더욱 궁금해한다.
			- 해결되었는가?, 회피가 되었는가?
			- 경험한 소스는 구구절절 적지말고 링크를 남겨라
			- 1차 Quester는 시간이 많이 없다. 그렇기에 내가 준비되었다는 걸 어필
			- 어필 포인트
				- 프로젝트 자체
				- 문제 해결 능력
					- 테마를 정한다.
						- 사람 문제
						- 기술 문제
		- 개인 프로젝트 vs 팀 프로젝트?
			- 팀프로젝트를 많이 할 수록 다양한 문제와 해결 사례 및 느낀점과 배운점 등
			  다양한 소스가 생긴다. 그러므로 팀 프로젝트가 무조건 이득이다.
		- 조직에서는 지시하고 지휘하는 리더보다 보좌하고 도와주는 팔로워를 더 선호할 수 있다.
		- Interview Study는 매우 유용하다.
		- Interview 문과 유튜버 추천
		- 현재 안좋은 사례을 어떻게 소스를 팔까? 
			- 중요 포인트 :: 나를 팔아라
				- 5명 중 3명이 프리라이더
				- 직설적으로 실력미달이라고 하는 것은 무조건 금지
				- 좀 순화하여 나포함 2명과 나머지 3명과 의견이 달랐다라고 순화하자.
				- 하지만 간접적으로 그 3명이 프리라이더 였다는걸 알려줘야 한다.
				- 왜 그들이 심각한 수준인가의 디테일을 알려줘야 한다.
				- 이러한 상황에서 내가 얻은 것과 배운 점 어필할 점을 찾아서 알려주자
					- 나는 잘한다, 나는 솔직하다, 나는 긍정적이다. 나는 의리가 있다 등.
				- 내가 어필하고 싶은 포인트를 끝까지 유지해야 한다.
			- 하기 싫은 일을 해야 하고싶은 일을 할 수 있다.
			- 현제 프로젝트 사례을 띠로 작성하고 정리하자 이것은 나에게 Interview에서 좋은 사례가 될 것이다.

- 다양한 기술을 배워보고싶다 새로운 프로젝트에서 다른 기술을 배우는 것에 대해 질문
	- NO. 기본기를 탄탄하게 하라.
		- 그렇다면 기본기란 무엇인가? 
			- 대상의 근간을 궁금해하라
				- 왜 사용되는건가? , 어떻게 동작하는가? , 보안은 어떻게 유지하는가? 등
				- 그 근간으로 들어가면 결국 자료구조, 네트워크 , 운영체제, 알고리즘..
				- "결국 CS이다."
	- cs 공부, 기술 면접, 기업 분석, 기본기가 가장 중요하다.
	- 내가 엄청난 대단한 무언가가 있는가? 아니면 기본기가 탄탄해야 하는가?
##### **📚 Project Role

##### **📚 GitHub 관련 규칙
##### 2. 브랜치 전략
##### 3. 커밋 메시지 규칙
- **커밋 메시지 형식**: 커밋 메시지는 짧고 명확하게 작성하며, 일반적으로 아래 형식을 따릅니다.
  - `Add`: 새로운 기능 추가
  - `Fix`: 버그 수정
  - `Update`: 기능 또는 문서 업데이트
  - `Refactor`: 코드 리팩토링
  - 예: `Fix: 로그인 에러 해결`
- **커밋 메시지는 영어 혹은 한글로 통일**: 팀 내에서 사용하는 언어를 정하고 일관성 있게 사용합니다.

##### 4. 풀 리퀘스트 (PR) 규칙
- **PR은 한 가지 작업에 대해 하나씩**: 여러 작업이 섞이지 않도록 한 PR에서는 한 가지 기능이나 수정만 다룹니다.
- **PR 리뷰 필수**: 코드 리뷰를 거치지 않은 PR은 병합하지 않습니다. 팀원이 PR을 제출하면 최소 한 명 이상이 리뷰한 후 승인합니다.
- **PR 템플릿 사용**: PR 설명에 작업의 목적, 주요 변경 사항, 관련 이슈 번호 등을 명확하게 작성합니다.

##### 5. 코드 컨벤션
- **코드 스타일 통일**: 팀 내에서 사용하는 프로그래밍 언어의 스타일 가이드를 따릅니다. 예를 들어 Python의 경우 PEP8, JavaScript는 Airbnb 스타일 가이드 등을 사용합니다.
- **자동 포매터 설정**: 코드 스타일을 강제하기 위해 Prettier, ESLint, Black 등의 자동 포매터와 린터를 설정합니다.

---

#### 📚 **팀 프로젝트 규칙

##### 1. 역할 분담
- **역할 및 책임 명확화**
	- 팀원들의 역할을 명확하게 나누고, 책임 범위를 정합니다. 예를 들어, 백엔드 개발자, 프론트엔드 개발자, QA 담당자 등으로 나누어 진행합니다.
- **PM 또는 Scrum Master 지정**
	- 프로젝트의 전반적인 진행 상황을 관리할 사람을 지정하여 스프린트 계획, 작업 할당, 회의 일정 조율 등의 책임을 부여합니다.
##### 2. 회의 규칙
- **정기 회의 일정**
	- 주기적인 미팅 일정을 정해 프로젝트 진행 상황을 공유하고, 문제 발생 시 해결 방안을 논의합니다.
- **회의록 작성 및 공유**
	- 회의 중 나온 주요 논의 사항, 결론, 액션 아이템을 정리한 후 팀원들과 공유합니다.
- **일정 엄수**
	- 미팅 시간과 약속된 마감일을 엄수하며, 지연이 예상되면 사전에 팀원들과 공유합니다.
##### 3. 커뮤니케이션 규칙
- **일관된 툴 사용**
	- 모든 팀원이 사용하는 커뮤니케이션 툴을 통일합니다. 예를 들어, Slack, Notion, Jira 등의 툴을 활용해 정보를 공유하고 업데이트합니다.
- **이슈 관리**
	- GitHub 이슈나 Jira 같은 툴을 사용하여 모든 작업을 이슈로 관리하고, 
	- 각 작업에 대한 상태를 명확하게 표시합니다 (예: `To Do`, `In Progress`, `Done`).
- **오프라인/온라인 소통 균형**
	- 팀원이 오프라인과 온라인에서 자유롭게 소통할 수 있는 환경을 제공합니다.
##### 4. 일정 및 작업 관리
- **작업 단위 명확화**
	- 모든 작업을 작은 단위로 나누어 팀원들이 이해하고 관리하기 쉽게 만듭니다.
- **데드라인 설정**
	- 각 작업에 대해 명확한 마감 기한을 설정하고 이를 준수합니다.
- **우선순위 관리**
	- 모든 작업의 우선순위를 명확히 정해 중요한 작업부터 처리합니다.
##### 5. 문서화
- **프로젝트 문서 작성**
	- 프로젝트 초기 기획서, API 명세서, 기술 스택, 설치 방법, 사용 방법 등을 문서화하여 저장소에 포함합니다.
- **지속적인 업데이트**
	- 문서는 프로젝트 진행 상황에 맞게 지속적으로 업데이트되며, 최신 정보를 유지합니다.

---

##### 📚**Trouble Shooting
### 📚 Server
#### N클라우드 관련
##### 로컬에서는 실행이되는데 NCloud 서버에서는 실행이 안되는 경우

- 추측
	- entityManager extception이 발생한 것으로 DB 관련 오류로 추측
	
- 원인 및 해결
	- **1. N클라우드 서버 DB를 생성하지 않았다.**
		로컬 내에서만 존재했던 스키마를 클라우드 서버에도 스키마를 생성해야한다는 사실을 간과하였다.
		또한, DB는 파일 형식이기 때문에, Linux 커멘드로는 접근에 한계가 있다.
		따라서 Vim을 통해서 파일을 텍스트 형식으로 직접 접속하여 스키마 유무에 대한 확인을 해야한다.
		
		1. N클라우드 서버 내의 Docker를 접속
		2. Remote host의 Docker MYSQL 접속
		3. ls 입력 후 Docker 내의 DB 확인
		4. docker exec -it (`DB ID`) -u bash
		5. MYSQL(DB) -u username -p
		6. SHOW DATABASES;
		7. 스키마가 없는 것으로 확인
		8. 클라우드 서버 내의 DB 생성 `CREATE DATABASE`
		9. 다시 jar 실행 시도
		10. 클라우드 서버 내의 스프링부트 Run 성공
		
	- 2. **로컬 내의 변경사항을 git에 commit push 한 이후 Ncloud 서버 내에서 git pull하지 않았다.**
		어찌보면 이것도 당연하다.. 로컬내의 변경사항은 원격저장소에 업데이트가 되었지만 
		원격 저장소의 최신 업데이트 내용을 클라우드 서버에서 받아오기 위해선 당연히 클라우드 서버에서도
		pull을 받아야한다는 것이다. 로컬 내에 내가 했던 활동을 클라우드 서버에도 당연히 적용해야하는 부분을 항상
		주의 깊게 체크하자.
		
		1. 로컬 단의 프로젝트를 commit / push 
		2. 클라우드 서버 단의 프로제트를 pull을 받는다.
		   
	- 3. **./git gradlew를 하지 않았다.**
		gradle은 알집형식의 파일이기 떄문에 이렇게 업데이트할 필요가 있다.
		  
	- 4. **application yaml의 DB 주소를 잘못 설정하였다.**
		클라우드 서버는 로컬 서버가 아니기 때문에 호스트 주소를 localhost로 하면 안되고 
		클라우드 서버의 공인 IP 주소로 설정해야 한다.
		이 또한 앞 부분의 실수들 처럼 로컬 내의 당연시 했던 활동들을 간과한 실수이다.
		
		- ncloud 서버는 로컬서버가 아니기때문에 localhost로 하면안된다.
		1. 클라우드 서버 내의 최상단 경로 이동 
		2. ip add 명령어 입력
		3. 출력되는 정보에서 docker 0에 앞에 있는 아이피 주소를 사용
		   
	- **결론
		- 평소 로컬 단에서 작업하던 당연시 했던 지식들을 클라우드 서버 단에서도 주의를 기울여야한다.
		- Linux와 Vim을 통해서 터미널 내에 apllication ymal , gradle.build, dokcer compose ymal, DB, 등도 체크하는 습관을 가져한다.
		- 클라우드 서버단에서 git pull을 받는 것을 잊음
		- ncloud 서버 내의 DB 생성을 놓침
		- 클라우드 서버의 DB 주소 연동을 올바르게 하지 못함.

##### ssh: connect to host 211.188.48.211 port 22: Connection timed out 에러

- 문제
	- ssh: connect to host 211.188.48.211 port 22: Connection timed out
	- ssh 서버 접속 시도시 몇초 경과 후 위와 같은 에러 발생 후 서버 접속 시도에 실패
- 원인 및 해결
	- **ACG 와이파이 아이피 주소 재설정**
		ACG 오류로 와이파이가 재설정되어 MY아이피가 바뀌어서 기존 설정한 포트번호와 일치하지않아서 
		생긴 오류 포트 허용 아이피를 재설정하면 된다.
		
	1. 엔 클라우드 서버 ACG 설정
	2. 접근 소스 - myip
	3. 허용 포트 설정 - 22, 3000-9000
	4. 메모 - 현재 위치하는 아이피의 소재지 (구분의 용도)
	5. 적용 버튼 꼭 누르기
	





##### 📚**Coding Test

### 📚함수 및 문법
##### charAt
```java
	 // 문자열 : charAt() 메서드를 호출하는 문자열 객체.
	 // 인덱스 : 반환하려는 문자가 위치한 0부터 시작하는 정수 값.
	 // 반환값 : char 형식의 문자입니다.
	 
	String str = "hello";
	char ch = str.charAt(1);  // 'e'를 반환
	System.out.println(ch);   // 출력: e
```


##### 📚 SQL 문제

-- 001. 전체 축구팀 목록을 팀이름 오름차순으로 출력하시오 

-- 002. 플레이어의 포지션 종류를 나열하시오. 단 중복은 제거하고, 포지션이 없으면 빈공간으로 두시오 

-- 003. 플레이어의 포지션 종류를 나열하시오. 단 중복은 제거하고, 포지션이 없으면 '신입' 으로 기재하시오 

-- 004. 수원팀에서 골키퍼(GK)의 이름을 모두 출력하시오. 단 수원팀 ID는 K02 입니다. -- 005. 수원팀에서 성이 고씨이고 키가 170 이상인 선수를 출력하시오. 단 수원팀 ID는 K02 입니다. -- 005-1. 수원팀의 ID 는 ? 

-- 005-2. 수원팀에서 성이 고씨이고 키가 170 이상인 선수를 출력하시오. (서브쿼리)

-- 문제 6 -- 다음 조건을 만족하는 선수명단을 출력하시오 -- 소속팀이 삼성블루윙즈이거나 -- 드래곤즈에 소속된 선수들이어야 하고, -- 포지션이 미드필더(MF:Midfielder)이어야 한다. -- 키는 170 센티미터 이상이고 180 이하여야 한다. -- 첫번째 단계, id를 알았을 경우 진행해 봄 -- 서브쿼리 -- 인라인뷰 

-- 문제 7 -- 수원을 연고지로 하는 골키퍼는 누구인가? 

-- 문제 8 -- 서울팀 선수들 이름, 키, 몸무게 목록으로 출력하시오 -- 키와 몸무게가 없으면 "0" 으로 표시하시오 -- 키와 몸무게는 내림차순으로 정렬하시오 

-- 문제 9 -- 서울팀 선수들 이름과 포지션과 -- 키(cm표시)와 몸무게(kg표시)와 각 선수의 BMI지수를 출력하시오 -- 단, 키와 몸무게가 없으면 "0" 표시하시오 -- BMI는 "NONE" 으로 표시하시오(as bmi) -- 최종 결과는 이름내림차순으로 정렬하시오 

-- 문제 10 -- STADIUM 에 등록된 운동장 중에서 -- 홈팀이 없는 경기장까지 전부 나오도록 -- 카운트 값은 19 -- 힌트 : LEFT JOIN 사용해야함 

-- 문제 11 -- 팀과 연고지를 연결해서 출력하시오 -- [팀 명] [홈구장] -- 수원[ ]삼성블루윙즈 수원월드컵경기장 

-- 문제 12 -- 수원팀 과 대전팀 선수들 중 -- 키가 180 이상 183 이하인 선수들 -- 키, 팀명, 사람명 오름차순 -- 해결방식 1 (조인 방식) -- 해결방식 1-1 (뷰 생성 ) -- 해결방식 2 (인라인뷰 방식) -- 서브쿼리 내용 확인 

-- 문제 13 -- 모든 선수들 중 포지션을 배정 받지 못한 선수들의 -- 팀명과 선수이름 출력 둘다 오름차순 

-- 문제 14 -- 팀과 스타디움, 스케줄을 조인하여 -- 2012년 3월 17일에 열린 각 경기의 -- 팀이름, 스타디움, 어웨이팀 이름 출력 -- 다중테이블 join 을 찾아서 해결하시오. 

-- 문제 15 -- 2012년 3월 17일 경기에 -- 포항 스틸러스 소속 골키퍼(GK) -- 선수, 포지션,팀명 (연고지포함), -- 스타디움, 경기날짜를 구하시오 -- 연고지와 팀이름은 간격을 띄우시오(수원[]삼성블루윙즈) 

-- 문제 16 -- 홈팀이 3점이상 차이로 승리한 경기의 -- 경기장 이름, 경기 일정 -- 홈팀 이름과 원정팀 이름을 -- 구하시오
##### 📚**Study List
##### React Next.js 14와 Spring Boot를 활용한 라우팅 및 데이터베이스 연동
- **라우팅 (Routing)**: 페이지 간 이동을 처리하는 메커니즘.
- **`layout.tsx`**: 스프링의 메인 메소드와 컨테이너에 대응하는 역할을 함.
- **리액트 Next.js 14 라우팅**: Next.js 14를 사용하여 페이지 간의 이동을 구현. ([참고 자료](https://cjy00n.tistory.com/m/199))
- **TSX와 TS 역할**:
    - **TSX**: 화면을 구성하고, 리턴값을 통해 화면에 표시.
    - **TS**: 통신과 관련된 로직만 담당.
- **DB 등록**: 화면에서 입력된 데이터를 통해 API를 호출하여 Ncloud의 DB에 데이터를 등록.

##### 오늘 게시판

- 키워드
	- 단일 테이블 vs 다중 테이블
	- 교차 엔티티
	- 데이터 마이닝
	- 데이터 크롤링
	- 스크래핑
	- Jsoup
		- 정적
	- Selenium
		- 동적
	- 자바 데이터 크롤링 벅스뮤직 코드 예제
	- 스프링 그래들 크롤링
	- SPA
	- NPA
	- SEO (검색엔진 최적화)
	- AOP
- 템플릿 공유 사이트
	- 유료 사이트
		- https://themeforest.net/search/nextjs
	- 무료 사이트
		- https://vercel.com/templates/next.js
- 24살 비전공자 신입 개발자 최종 합격 포트폴리오
	- https://www.youtube.com/watch?v=bw4uC-P84CQ
- 조코딩 - 7분만에 웹사이트 만들기
	- https://www.youtube.com/watch?v=4mRae9N2pU4
- 조코딩 - next js 기초 강의
	- https://www.youtube.com/watch?v=Tt_tKhhhJqY
- 도커 강의
	- https://www.youtube.com/watch?v=eRfHp16qJq8
- 알고리즘 공부법
	1. 프로그래밍 기본 문법 공부(파이썬)
	2. 알고리즘 기본100제(코드업:기초100제)
	3. 백준 문제풀기(그리디, 탐색, 기초 동적프로그래밍 50문제씩)
	4. 기출문제 풀기(프로그래머스:카카오)
		코드포스 블루레벨 정도면 코딩테스트 합격 가능(또는 삼성 역량 테스트 B형)
		추천 언어 : C++,파이썬
- Python 100제 강의
	- https://codeup.kr/problemsetsol.php?psid=33
- 단일 테이블을 다중 테이블로 확장
- 교차 엔티티
- 데이터 마이닝
- 데이터 크롤링
	- 자바 데이터 크롤링 벅스뮤직 코드 예제
		- https://blog.naver.com/nakwon3345/222446315355
- 교차 엔티티
	- https://parksrazor.tistory.com/79
- 스프링 그래들 크롤링
- 스크래핑
	- 이 HTTP GET 요청에 웹 서버가 응답하면 스크래핑 알고리즘은 HTML 문서를 분석하여 특정 패턴을 지닌 데이터를 추출하는 순서로 진행되며, 추출된 데이터를 원하는 형태로 사용할 수 있도록 데이터베이스에 저장합니다. 
	- 웹 스크래핑은 자동으로 수집된 특정 정보가 필요한 분야에서 다양하게 활용되고 있습니다.
	- 크롤링은 단어의 의미처럼 계속 여기저기 기어다니듯이 탐색을 지속하지만, 스크래핑은 특정 페이지만을 대상으로 한다는 데 차이가 있습니다.
	- 스크래핑 라이브러리
		- Jsoup
		- 
- AOP
- Pagingnation
	- https://www.evernote.com/shard/s294/client/snv?isnewsnv=true&noteGuid=71c4f0c8-bf43-e527-5665-f55f450d966e&noteKey=shwBZ6za4KmM0_oxCeqlP4TP4WxxTn48JxPFTjfH5PJyhKOHBpwd9oWxeQ&sn=https%3A%2F%2Fwww.evernote.com%2Fshard%2Fs294%2Fsh%2F71c4f0c8-bf43-e527-5665-f55f450d966e%2FshwBZ6za4KmM0_oxCeqlP4TP4WxxTn48JxPFTjfH5PJyhKOHBpwd9oWxeQ&title=spring.io%252Fboot%252Fv%252Fhamburg%252Fwego%2B%253A%2BPagination.java
	- https://flowbite.com/docs/components/pagination/
- 크롤링
	- 기초 강의 
		- https://velog.io/@hyn_053/%EC%96%B4%EB%96%A4-%ED%81%AC%EB%A1%A4%EB%A7%81-%EB%8F%84%EA%B5%AC%EB%A5%BC-%EC%84%A0%ED%83%9D%ED%95%B4%EC%95%BC-%ED%95%A0%EA%B9%8C
	- 벅스 크롤링
		- https://blog.naver.com/nakwon3345/222446315355
- 교차 엔티티
	- https://parksrazor.tistory.com/79
- OAuth
	- https://itadventure.tistory.com/653
	  
- info
	- 테스트 주의사항
		- 데이터베이스
			- 1, 10명 X
			- 10000~20000명 O
		- 게시글
			- ㅋㅋㅋㅋㅋ X
			- 김정책 게시물 테스트입니다. 작성일... O
		- 대충 쓰지마라, 제대로 해라
	- 
- 트러블 슈터
	- 로컬 내에서도 doker를 안키면 실행이 안된다.
- 
- 오늘 한것
	- Jsoup, Selenium 세팅하기
	- 리액트 버튼 누르면 컨트롤러에서 sysout "eventCroller"를 출력하게 하기
	- 크롤링한 정보 DB에 저장하기
	- 백엔드, 프론트엔드 Pagingnation 구현
	- OAuth 구현
	- 클라우드 서버내에 Mysql-files에 CSV 파일 넣기
	- 클라우드 서버 내에 넣은 CSV 파일을 Docker Mysql 이미지에 Load하기

- 카카오 알리에게 개인정보 넘겼을 때 보안관련에서 어떠한 문제점이 있었다.
- Quest
	- 리액트 CROS 에러 해결
	- 크롤링한 정보 DB에 저장하기
	- 레이징네이션 구현하기
	- OAuth
	- Next js 14 강의 수강 완료
	- 교차 엔티티
	- 클라우드 서버에 csv 파일 mysql server files에 넣는 방법
	- 쿼리DSL
	- 자바 람다식 사용
	- 

- JS 무료 강의
	- https://nomadcoders.co/courses?utm_source=youtube&utm_medium=cpc&utm_campaign=fp&utm_id=20220320#free

- 1인 프로젝트 최소 할당량
	최소 테이블 5개 이상
	관리자 모드
	msa 형태이기에 프로젝트는 2개로 분류

- 데이터베이스 정규화를 거쳐서 ERD 설계
- 
###### Pagingnation
``` java
rowNum 
pageNum 
blockNum 
row count size start end 
page count size start end 
block count size prev next 
boolean existsPrev, existsNext 
PAGE_SIZE = 10; BLOCK_SIZE = 5; 

public Pagination(int pageNum, int count) { 
	this.pageNum = pageNum; 
	this.totalCount = count; 
	this.pageCount = 
	this.blockCount = 
	this.startRow = 
	this.endRow = 
	this.blockNum = 
	this.startPage = 
	this.endPage = 
	this.existPrev = 
	this.existNext = 
	this.nextBlock = startPage + BLOCK_SIZE; 
	this.prevBlock = startPage - BLOCK_SIZE;
	
```




https://www.inflearn.com/course/%EC%9A%94%EC%A6%98%EC%97%94-supabase-%EB%8C%80%EC%84%B8%EC%A7%80-nextjs-%ED%81%B4%EB%A1%A0%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8#reviews


https://www.inflearn.com/course/supabase-next-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0#reviews




H5?R467eFDiHb


cd /var /lib 
ls

cp team.csv /var/lib/mysql-files



load data infile './stadium.csv' into table stadium fields terminated by ',' enclosed by "" lines terminated by '\n' ignore 1 rows (stadium_id, stadium_name, hometeam_id, seat_count, address, ddd, tel);

sudo nano /etc/mysql/my.cnf



ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'um_id, zip_code1, zip_code2, address, ddd, tel, IGNORE 1 ROWS
     (team_id, reg' at line 6



 LOAD DATA INFILE '/var/lib/mysql-files/team.csv'
     INTO TABLE team
     FIELDS TERMINATED BY ','
     ENCLOSED BY '"'
     LINES TERMINATED BY '\n'
     IGNORE 1 ROWS
     (team_id, region_name, team_name, e_team_name, orig_yyyy, stadium_id, zip_code1, zip_code2, address, ddd, tel, fax, homepage, OWNER);



LOAD DATA INFILE '/var/lib/mysql-files/schedule.csv'
   INTO TABLE team
     FIELDS TERMINATED BY ','
     ENCLOSED BY '"'
     LINES TERMINATED BY '\n'
     IGNORE 1 ROWS
          (stadium_id, sche_date, gubun, hometeam_id, awayteam_id, home_score, away_score);



echo "#Lodging-Commander" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/atoonatoo/Lodging-Commander.git
git push -u origin main



git remote add origin https://github.com/atoonatoo/Lodging-Commander.git
git branch -M main
git push -u origin main


git clone https://github.com/atoonatoo/hotel-solo-project.git


git config --global user.name "atoonatoo"
git config --global user.email "donguk963@gamil.com"


spring:  
  datasource:  
    driver-class-name: com.mysql.cj.jdbc.Driver  
    url: jdbc:mysql://localhost:3306/lodgingCommander  
    username: root  
    password: 1234  
  
  security:  
    user:  
      name: a  
      password: a  
  
  jpa:  
    hibernate:  
      ddl-auto: update  
    show-sql: true

npm install react-router-dom 
npm install axios 
npm install redux 
npm install react-redux
npm install react-bootstrap bootstrap

- Spring CRUD + JPA + Gradle 프로젝트
	- https://github.com/jjang-youngju/spring-crud-jpa

 gradle에 사용하는 buid 형식 

---