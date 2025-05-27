---
created:
---

---
- [[0 Home]]
---
- [](#)
- [](#)
- [](#)
---

#### spec

- **언제든 설명할 수 있는 지식**

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

#### coding-test  




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