---
created:
---
---
- [[0 Home]]
---
- **A. Study & Research**
    1. **Study**
    2. **Learning**
    3. **Ideas**
	  
- **B. Projects**
    1. **Work**
    2. **Issues - In Progress**
    3. **Issues - Resolved**
    4. **Setup Guide**
      
- **C. Tests & Practice**
    - **Coding Test**
    - **Exams**

---
- [[Mentoring]]
- [[Morning Study]]
- [[Book Study]]
- [[BackUp Code]]
- [[Jmeter 세팅 가이드]]
- [[정보처리기사]]
- [[Conding Test]]
- [[Nginx 로드밸런싱 문제 해결 보고서]]
- [[JMeter 경량 부하 테스트 응답 지연 이슈 분석 및 대응 보고서]]
- [[로그 수집 시스템 구축 (Filebeat + Elasticsearch + Kibana)]]
- [[자주 햇갈리는 개념]]
- [[Project Idea]]
- [[대량의 외부 API를 호출하면 무슨 일이 벌어지는가]]
- [[대용량 데이터 + 스파이크성 트래픽 개선 (2)]]
- [[프로젝트 개선 사항 시나리오]]
- [[GPT 질문 공략]]
- [[Findings]]
- [[SQL Practice]]
- [[Recmmended Book]]
- [[Topic]]
- [[Famous Saying]]
- [[KnowHow 1]]
- [[Why]]
- [[Thingking]]

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
#### learning-loadmap

- [[5 - 분류/7 - CS/4 wait/Data Structure]]
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
	- **[[5 - 분류/7 - CS/4 wait/Data Structure]]**
		- [[5 - 분류/7 - CS/4 wait/Stack]]
		- [[5 - 분류/7 - CS/4 wait/Queue]]
		- [[5 - 분류/7 - CS/4 wait/Linked List]]
		- [[Array]]
		- [[5 - 분류/7 - CS/4 wait/Tree]]
		- [[5 - 분류/7 - CS/4 wait/Heap]]
		- [[Graph]]
		- [[5 - 분류/7 - CS/4 wait/Hash Table]]
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
		- [[5 - 분류/7 - CS/4 wait/Bubble Sort]] 
		- [[5 - 분류/7 - CS/4 wait/Selection Sort]] 
		- [[5 - 분류/7 - CS/4 wait/Insertion Sort]] 
		- [[5 - 분류/7 - CS/4 wait/Heap Sort]] 
		- [[5 - 분류/7 - CS/4 wait/Merge Sort]] 
		- [[5 - 분류/7 - CS/4 wait/Quick Sort]] 
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
		- [[5 - 분류/7 - CS/4 wait/Stack]]
		- [[5 - 분류/7 - CS/4 wait/Queue]]
		- [[5 - 분류/7 - CS/4 wait/Hash Table]]
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


##### GPT
- mycompany의 내용들을 토대로 솔루션을 제공해줘
- cs, 코딩 테스트, 채용회사 서칭, 포트폴리오 프로젝트 코딩, 노트 정리를 하루에 9시간안에 다 해야 한다면? 적절하게 시간을 배분해줘
- 성장가능성이 높은 기업이란 구체적으로 내가 남들에게 자신있게 설명할 수 있도록 알려줘
- 아주 못하는 초짜도 코딩 테스트를 준비하는 방법
- cs 공부 순서
- SI VS 비IT VS IT VS 서비스 기업이란?

	  
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
- 키워드
	- Kubernetes 관리 플랫폼
		- 클러스터 구성, 워크로드 배포 등 쿠버네티스 구성 및 자동화 관리
	- MLOps 플랫폼 (Kubeflow) 구성, 관리 자동화 개발
	- Flask
	- Django
	- gRFC
	- RDBMS
	- NoSQL

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
  
- 문제 해결 -> 수치화 -> 성능 측정

- hikari
	- Java 기반 application에서 데이터베이스와 연결을 효율적으로 관리하기 위한 커넥션 풀 라이브러리이다.
- connection pool
	- DB와 연결을 새로 맺는 것은 매우 비용이 큰 작업이다. 그래서 미리 일정 수의 DB 연결을 만들어 폴에 보관하고 어플리케이션은 필요할 때 폴에서 연결을 꺼내서 사용하고, 사용 후 다시 반납하는 방식으로 동작한다.
	- 설정값
		- `maxinmum-pool-size` : 폴에 생성할 수 있는 최대 커넥션수
		- `minimum-idle` : 항상 유지할 최소 유휴(idle) 커넥션 수
		- `idle-timeout` : 커넥션이 사용되지 않고 idle 상태로 있으면 해제될 때까지 대기 시간 (ms)
		- `max-lifetime` : 커넥션이 살아 있을 수 있는 최대 시간 (ms). DB가 커넥션을 강제로 끊는 문제 예방
			- aws rds, mysql은 일정시간이 지나 자동으로 커넥션을 닫는다.
			- 그 이유는 자원 보호 및 누수의 문제를 해결 하기 위함이다.
- hibernate
	- java 진영의 ORM 프레임워크이다.
	- 객체지향 코드(java 코드)와 관계형 데이터베이스 (DB 테이블)간 매핑을 자동화
	- 즉, 직접 SQL문을 작성하지 않아도 객체 상태를 기반으로 DB 작업을 자동 수행
	- 기능
		- Entity <-> 테이블 자동 매핑
		- CURD 자동 처리
		- 지연 로딩 / 캐싱
		- 트랜잭션 / Lazy Loading
- Spring Boot Actuator
	- 스프링부트의 운영 및 모니터링 기능을 제공하는 라이브러리
	- 이를 통해 서버 상태, 매트릭, 헬스 체크, 애플리케이션 정보 등을 실시간으로 확인 가능
	- 설정값
		-  `management.endpoints.web.exposure.include: "*"` : 모든 actuator 엔드포인트를 HTTP로 노출
			- 기본 값은 `"health", "info`만 노출 -> 이를 `"**"`로 변경해 전체 활성화 한 것
		- `management.endpoint.health.show-details: always` : `/actuator/health`에 접근했을 때 상세 상태 정보를 항상 표시
			- 기본 값은 `never` 또는`when-authorized`인데 이 경우 인증 없이는 `status:UP`같은 간단한 정보만 표시
		- `management.endpoint.prometheus.enabled: true` : Prometheus 엔드포인트(`/actuator/prometheus`)를 활성화
			- 이 설정이 있어야 Prometheus가 Spring Boot 앱의 메트릭을 수집할 수 있다.
			- 이 엔드포인트는 Prometheus 포맷의 텍스트 데이터를 반환한다.
- SLA (Service Level Agreement)
	- 사용자와 약속한 성능 보장 기준
	- 예 - 평균 응답시간 1초 이하, TPS 1000 이상, 에러율 1% 이하

- 키워드
	- 단일 테이블 vs 다중 테이블
	- 교차 엔티티
	- 데이터 마이닝
	- 데이터 크롤링
	- 스크래핑
	- Jsoup
	- Selenium
	- 자바 데이터 크롤링 벅스뮤직 코드 예제
	- 스프링 그래들 크롤링
	- SPA
	- NPA
	- SEO (검색엔진 최적화)
	- AOP
	- 단일 테이블을 다중 테이블로 확장
	- 교차 엔티티
	- 데이터 마이닝
	- 데이터 크롤링
	- 자바 데이터 크롤링 벅스뮤직 코드 예제
	- 스프링 그래들 크롤링
	  


---


- 알고리즘 공부법
	1. 프로그래밍 기본 문법 공부(파이썬)
	2. 알고리즘 기본100제(코드업:기초100제)
	3. 백준 문제풀기(그리디, 탐색, 기초 동적프로그래밍 50문제씩)
	4. 기출문제 풀기(프로그래머스:카카오)
		코드포스 블루레벨 정도면 코딩테스트 합격 가능(또는 삼성 역량 테스트 B형)
		추천 언어 : C++,파이썬
- Python 100제 강의
	- https://codeup.kr/problemsetsol.php?psid=33

- **Interview**
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
		10. **Linux 부팅 과정과 관련된 부트로더(예: GRUB) 및 init 시스템(systemd, init.d 등)의 역할에 대해 설명해 주세요.
---