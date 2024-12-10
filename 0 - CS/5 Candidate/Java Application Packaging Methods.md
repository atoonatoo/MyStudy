---
created: 2024-01-04
updated: 2024-09-17
---
----
##### 연결 문서
- 
- 
- 
---

# **README**

- [[ATNT/1 - Project/CS (Computer Science)/E list/JAVA|JAVA]] 로 개발된 어플리케이션을 배포하고 실행할 수 있도록 하나의 파일이나 배포 가능한 형태로 묶는 과정을 의미
- 이를 통해 개발자는 어플리케이션을 다른 시스템이나 환경에 쉽게 전달하고, 사용자나 클라이언트는 복잡한 설정 없이도 어플리케이션을 사용할 수 있다. 


##### 주요 패키징 방법

- **[[Jar (Java ARchive)]] 파일 (Java Archive)**
	- Java 클래스 파일과 관련 리소스를 하나의 압축된 파일로 묶은 것
	- jar 명령어를 사용하여 생성하며, 라이브러리나, 어플리케이션 모듈로 활용된다.
	  
- **WAR 파일 (Web Application Archive)**
	- 웹 어플리케이션을 위한 패키지 형식으로, Servlet, JSP, HTML, CSS, Javascript 등 웹 관련 파일들을 포함한다.
	- Tomcat이나 Jetty같은 웹 서버에 배포하여 사용한다.
	
- **EAR 파일 (Enterprise Application Archive)**
	- [[Enterprise Application]] 규모의 어플리케이션을 위한 패키지로, 여러 개의 JAR와 WAR 파일을 하나로 묶는다.
	- JAVA EE 어플리케이션 서버에 배포하여 사용한다.
	
- 실행 가능한 JAR 파일
	- 메인 클래스를 지정하여 더블 클릭이나 명령어로 직접 실행할 수 있는 JAR 파일이다.
	- [[MAINFEST.MF]] 파일에 메인 클래스 정보를 추가하여 생성한다.
	
- [[jpackage]]
	- Java 14부터 도입된 jpackage 도구를 사용하여 플랫폼 별 설치 파일(EXE, DMG 등)을 생성한다.
	- 어플리케이션을 독립 실행형으로 배포할 수 있어 사용자 편의성이 높다.
	
- **빌드 도구 활용 (Maven, Gradle)**
	- [[Maven]]이나 [[Gradle]] 같은 [[Build Tool]]를 사용하여 [[Dependency management]]와 함께 패키징을 자동화한다. 
	- 복잡한 프로젝트에서도 일관된 빌드를 패키지잉 가능하다. 
	
- **[[Docker Container]]**
	- 어플리케이션과 필요한 환경을 컨테이너로 묶어 배포한다.
	- 환경 설정의 차이를 최소화하고, 이식성을 높여준다.
	
- [[GraalVM]] 네이티브 이미지**
	- GraalVM을 이용하여 Java 어플리케이션을 네이티브 실행 파일로 컴파일한다. 
	- 빠른 실행 속도와 적은 메모리 사용량이 특징이다.


