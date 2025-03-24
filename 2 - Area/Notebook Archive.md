---
created: 2024-01-03
updated: 
tags:
  - bookmark
---
---
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
		        1. 예를 들어, 데이터를 왕창 집어넣어서 의도적으로 쿼리를 느리게 만들어야한다
		        2. 동시성 문제가 없었는데 내가 그걸 어거지로 시나리오를 만들어서 했다던지
		            1. 없는 시나리오를 직접 제안해서 그 상황을 맞딱뜨린다
		    2. 문제를 만들어서 개선을 한다면 어떤 내용이 중점이 되어야하는가?
		        1. 나의 기본기를 드러낼 수 있어야한다

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
    1. Git 설치 및 Repository Clone:
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
    1. **JAVA_HOME 설정 추가**:
        
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








## 📚**명령어

#### 📚 1. **DATABASE

##### **DB 테이블 전부 삭제 및 재생성**
```SQL 
	DROP DATABASE your_database_name;
	CREATE DATABASE your_database_name;
    USE your_database_name;
    
 -- 이 명령어는 기존 데이터베이스를 삭제한 후 다시 생성하고, 
 -- 해당 데이터베이스를 사용하기 위한 명령어입니다.
```
---
#### 📚 2. **Git**

##### **Git 리포지토리 연동 해제**
```git
    git remote remove origin
       
    로컬 Git 저장소에서 원격 저장소 연결을 해제하는 명령어입니다. 
    주로 원격 저장소를 변경하거나 삭제할 때 사용됩니다.
```



---
#### 📚 3. **Linux**

##### **비밀번호 변경
```Linux
- passwd

현재 사용중인 비밀번호를 변경하는 명령어입니다.
```
---
#### 📚 4. **Vim**
#### 📚 5. **React**
#### 📚 6. **Docker**
## **📚Interview

#### 📚자기소개서

[목표를 위한 끝없는 노력]
1. 본인이 끝까지 파고들어 본 가장 의미있었던 개발 경험 또는 개발 활동에 대해 얘기해 주세요. 그 개발 경험 또는 개발 활동을 통해 배운 점이 무엇인지, 본인의 '어떤 부분이 성장'했는지에 대해 작성해 주세요. (반드시 지원한 포지션과 관련된 경험이 아니어도 좋습니다.)  
	
	저는 처음 개발 프로젝트에 참여하면서 제 자신의 부족함을 깊이 깨달았습니다. 팀원들은 이미 다양한 기술 스택과 깊은 CS 지식을 바탕으로 프로젝트를 이끌어 나갔지만, 저는 그들과 비교했을 때 많이 부족하다는 느낌을 받았습니다. 이 경험은 저에게 큰 충격이었지만, 동시에 저를 더 나은 개발자로 성장하게 만든 원동력이 되었습니다.
	
	프로젝트 초반에는 코드 리뷰 과정에서 실수나 이해 부족으로 인해 많은 피드백을 받았고, 이러한 피드백은 제게 개발자로서의 실력을 높일 수 있는 좋은 기회였습니다. 하지만 단순히 피드백을 받는 것만으로는 부족하다는 것을 알게 되었고, 이에 따라 CS(Computer Science) 기초 지식을 탄탄히 다지기 위해 체계적인 공부를 시작했습니다.
	
	운영체제, 네트워크, 자료구조, 알고리즘 등 CS 기초를 집중적으로 공부하며, 프로젝트에 필요한 각종 기술 스택도 병행하여 학습했습니다. 학습한 내용을 실전에 적용하기 위해 개인 프로젝트도 진행하며, 실제 개발 환경에서 발생할 수 있는 문제들을 스스로 해결해보는 경험을 쌓았습니다. 이러한 과정은 저의 실력을 한 단계 더 성장시키는 계기가 되었고, 이제는 팀 내에서도 기술적 리더십을 발휘할 수 있게 되었습니다.
	
	저는 지금도 끊임없이 배우고 성장하는 것을 멈추지 않습니다. 새로운 기술을 익히고, 최신 개발 동향을 따라가며, 더 나은 코드를 작성하기 위해 노력하고 있습니다. 저의 성장 과정은 저에게 많은 것을 가르쳐 주었으며, 앞으로도 개발자로서 계속해서 발전할 것입니다.
	
	이제는 다른 팀원들과 함께 협력하며, 함께 성장할 수 있는 개발자가 되기를 희망합니다. 제가 가진 경험과 배움을 바탕으로, 더욱 견고한 기술적 토대를 쌓고, 보다 나은 프로젝트 결과를 만들어내는 데 기여할 수 있도록 최선을 다하겠습니다.

#### **📚GitHub 관리 및 면접 대비 어드바이스**

1. **퍼포먼스와 보안에 중점**:
    
    - **프로그래밍 반응 속도**: 코드의 효율성 및 응답 속도에 중점을 두어 성능 개선.
    - **보안 요소 강조**: 프론트엔드 디자인(CSS)보다는 보안 관련 코드와 기능(인증, 데이터 보호)에 더 많은 비중을 둠.
    - **게시판 기능에 초점**: 로그인 기능보다 게시판의 효율적이고 안전한 구현에 집중.
      
2. **React `fetch()` API 호출**:
    
    - React에서 `fetch()`를 사용한 API 통신을 구현하는 방법을 숙지하고 프로젝트에 적용. ([참고 자료](https://velog.io/@fltxld3/React-API-%ED%98%B8%EC%B6%9C%ED%95%98%EA%B8%B0))
      
3. **GitHub 포트폴리오**:
	
    - 퍼포먼스 개선 사례와 보안 관련 코드 커밋을 명확히 기록.
    - 면접 시 프로젝트의 보안, 성능 최적화 작업을 설명할 수 있도록 준비.
#### 📚**채용 정보
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


### Interview

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
## **📚 Project Role

#### **📚 GitHub 관련 규칙
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

## 📚**Trouble Shooting
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
	





## 📚**Coding Test

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


### 📚 SQL 문제

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
## 📚**Study List
##### React Next.js 14와 Spring Boot를 활용한 라우팅 및 데이터베이스 연동
- **라우팅 (Routing)**: 페이지 간 이동을 처리하는 메커니즘.
- **`layout.tsx`**: 스프링의 메인 메소드와 컨테이너에 대응하는 역할을 함.
- **리액트 Next.js 14 라우팅**: Next.js 14를 사용하여 페이지 간의 이동을 구현. ([참고 자료](https://cjy00n.tistory.com/m/199))
- **TSX와 TS 역할**:
    - **TSX**: 화면을 구성하고, 리턴값을 통해 화면에 표시.
    - **TS**: 통신과 관련된 로직만 담당.
- **DB 등록**: 화면에서 입력된 데이터를 통해 API를 호출하여 Ncloud의 DB에 데이터를 등록.

### 오늘 게시판

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


- 


